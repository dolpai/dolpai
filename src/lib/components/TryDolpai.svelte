<script>
	import { onMount, tick } from 'svelte';

	// ── Business types ─────────────────────────────────────────────
	const businesses = [
		{
			id: 'clinic',
			label: 'Clinic',
			icon: '🏥',
			color: 'from-red-500 to-pink-600',
			glow: 'rgba(239,68,68,0.12)',
			inquiries: [
				'I need to book a dental checkup',
				'What are your consultation fees?',
				'Do you accept walk-ins?',
				'I need to reschedule my appointment'
			],
			responses: {
				'I need to book a dental checkup': { text: 'Of course! We have slots available this week. Tuesday 10 AM or Thursday 2 PM — which works for you?', action: '📅 Appointment slot offered', score: 82 },
				'What are your consultation fees?': { text: 'General consultation is $60. Dental checkup with cleaning is $120. Would you like to book an appointment?', action: '💰 Pricing shared · Lead captured', score: 68 },
				'Do you accept walk-ins?': { text: 'Yes, we accept walk-ins Mon–Sat 9 AM–5 PM. For shorter wait times, booking in advance is recommended. Want to book now?', action: '📋 FAQ answered · Booking offered', score: 71 },
				'I need to reschedule my appointment': { text: 'No problem! Please share your name and current appointment time, and I\'ll find the next available slot for you.', action: '🔄 Reschedule flow initiated', score: 75 }
			}
		},
		{
			id: 'restaurant',
			label: 'Restaurant',
			icon: '🍽️',
			color: 'from-orange-500 to-red-600',
			glow: 'rgba(249,115,22,0.12)',
			inquiries: [
				'Table for 4 this Saturday at 7pm?',
				'Do you have vegetarian options?',
				'What are your opening hours?',
				'Can I order for delivery?'
			],
			responses: {
				'Table for 4 this Saturday at 7pm?': { text: 'Saturday 7 PM for 4 guests is available! Shall I confirm the reservation? I\'ll need a name for the booking.', action: '📅 Reservation slot confirmed', score: 88 },
				'Do you have vegetarian options?': { text: 'Yes! We have an extensive vegetarian menu including pasta, salads, and our famous veggie burger. Want to see the full menu or make a reservation?', action: '📋 Menu info shared · Upsell offered', score: 65 },
				'What are your opening hours?': { text: 'We\'re open Mon–Thu 11 AM–10 PM, Fri–Sat 11 AM–11 PM, and Sunday 12 PM–9 PM. Would you like to make a reservation?', action: '📋 Hours shared · Booking CTA triggered', score: 60 },
				'Can I order for delivery?': { text: 'Yes! We deliver within 5km. Minimum order $25, delivery in 30–45 minutes. Want to place an order now?', action: '🚚 Delivery info shared · Order flow started', score: 72 }
			}
		},
		{
			id: 'education',
			label: 'Education',
			icon: '🎓',
			color: 'from-blue-500 to-violet-600',
			glow: 'rgba(59,130,246,0.12)',
			inquiries: [
				'What courses do you offer?',
				'How much does enrollment cost?',
				'Can I get a free trial class?',
				'Do you offer online classes?'
			],
			responses: {
				'What courses do you offer?': { text: 'We offer Digital Marketing, Web Development, Data Analytics, and Business Management — all available online and in-person. Which interests you most?', action: '📚 Course catalog shared · Lead qualified', score: 74 },
				'How much does enrollment cost?': { text: 'Courses range from $199–$499 depending on duration. We also offer payment plans. Would you like to book a free consultation with our advisor?', action: '💰 Pricing shared · Consultation offered', score: 79 },
				'Can I get a free trial class?': { text: 'Absolutely! We offer a free 1-hour trial class for any course. I can book you in for this week — what\'s your preferred day?', action: '🎯 Trial class booking initiated', score: 85 },
				'Do you offer online classes?': { text: 'Yes! All our courses are available 100% online with live sessions and recorded content. You can study at your own pace. Want to enroll?', action: '💻 Online info shared · Enrollment CTA', score: 70 }
			}
		},
		{
			id: 'agency',
			label: 'Agency',
			icon: '💼',
			color: 'from-violet-500 to-purple-700',
			glow: 'rgba(139,92,246,0.12)',
			inquiries: [
				'We need help with social media',
				'What\'s your pricing for SEO?',
				'Can you build us a website?',
				'I want to discuss a project'
			],
			responses: {
				'We need help with social media': { text: 'We specialize in social media growth! Our packages start at $500/month and include content creation, scheduling, and analytics. What\'s your monthly budget?', action: '📊 Service info shared · Budget qualified', score: 76 },
				'What\'s your pricing for SEO?': { text: 'SEO packages start at $800/month for local SEO and $1,500/month for national campaigns. We offer a free audit first. Want to schedule one?', action: '🔍 SEO pricing shared · Audit offered', score: 80 },
				'Can you build us a website?': { text: 'Yes! We build custom websites from $2,000 for landing pages to $8,000+ for full e-commerce. Can I book a 30-min discovery call to understand your needs?', action: '🌐 Web dev info shared · Discovery call offered', score: 83 },
				'I want to discuss a project': { text: 'Great! I\'d love to connect you with our team. Can you share a brief about your project and your timeline? I\'ll schedule a call within 24 hours.', action: '📞 Discovery call initiated · Lead captured', score: 87 }
			}
		}
	];

	// ── State ──────────────────────────────────────────────────────
	let selectedBusiness = $state(businesses[0]);
	let selectedInquiry = $state('');
	let chatMessages = $state(/** @type {Array<{type:string,text:string}>} */ ([]));
	let isTyping = $state(false);
	let actionFired = $state('');
	let leadScore = $state(0);
	let isRunning = $state(false);
	/** @type {HTMLDivElement|null} */
	let chatEl = $state(null);
	/** @type {ReturnType<typeof setTimeout>[]} */
	let timeouts = [];

	function clearTimeouts() { timeouts.forEach(clearTimeout); timeouts = []; }

	/** @param {typeof businesses[0]} biz */
	function selectBusiness(biz) {
		clearTimeouts();
		selectedBusiness = biz;
		selectedInquiry = '';
		chatMessages = [];
		actionFired = '';
		leadScore = 0;
		isRunning = false;
		isTyping = false;
	}

	/** @param {string} inquiry */
	async function sendInquiry(inquiry) {
		if (isRunning) return;
		clearTimeouts();
		selectedInquiry = inquiry;
		chatMessages = [{ type: 'user', text: inquiry }];
		actionFired = '';
		leadScore = 0;
		isRunning = true;
		isTyping = true;
		await scrollChat();

		const resp = selectedBusiness.responses[inquiry];
		if (!resp) return;

		const t1 = setTimeout(async () => {
			isTyping = false;
			chatMessages = [...chatMessages, { type: 'bot', text: resp.text }];
			leadScore = resp.score;
			await scrollChat();

			const t2 = setTimeout(() => {
				actionFired = resp.action;
				isRunning = false;
			}, 600);
			timeouts.push(t2);
		}, 1200);
		timeouts.push(t1);
	}

	async function scrollChat() {
		await tick();
		if (chatEl) chatEl.scrollTop = chatEl.scrollHeight;
	}

	onMount(() => () => clearTimeouts());
</script>

<section id="try-dolpai" class="section-padding relative overflow-hidden bg-[#030712]">
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] rounded-full bg-violet-500/4 blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-4 mb-12">
			<div class="section-label">Sandbox</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Try Dolpai for <span class="gradient-text">Your Business</span>
			</h2>
			<p class="text-lg text-gray-500">
				Select your industry, pick a customer inquiry, and watch Dolpai handle it instantly.
			</p>
		</div>

		<div class="max-w-4xl mx-auto">
			<!-- Business type selector -->
			<div class="flex flex-wrap justify-center gap-3 mb-8">
				{#each businesses as biz}
					<button
						onclick={() => selectBusiness(biz)}
						class="flex items-center gap-2.5 px-5 py-2.5 rounded-xl border text-sm font-semibold transition-all duration-200
							{selectedBusiness.id === biz.id
								? 'border-white/[0.18] bg-white/[0.07] text-white scale-[1.02]'
								: 'border-white/[0.06] bg-white/[0.02] text-gray-400 hover:border-white/[0.12] hover:text-white'}"
					>
						<span class="text-base">{biz.icon}</span>
						{biz.label}
					</button>
				{/each}
			</div>

			<div class="grid lg:grid-cols-2 gap-6">

				<!-- Left: Inquiry picker + chat -->
				<div class="space-y-4">
					<!-- Inquiry buttons -->
					<div class="space-y-2">
						<p class="text-xs text-gray-600 uppercase tracking-wider font-semibold px-1">Customer says:</p>
						{#each selectedBusiness.inquiries as inquiry}
							<button
								onclick={() => sendInquiry(inquiry)}
								disabled={isRunning}
								class="w-full text-left px-4 py-3 rounded-xl border text-sm transition-all duration-200
									{selectedInquiry === inquiry
										? 'border-cyan-500/30 bg-cyan-500/5 text-white'
										: isRunning
											? 'border-white/[0.04] bg-white/[0.01] text-gray-700 cursor-not-allowed'
											: 'border-white/[0.06] bg-white/[0.02] text-gray-400 hover:border-white/[0.12] hover:text-white hover:bg-white/[0.04] active:scale-[0.99]'}"
							>
								<span class="text-gray-600 mr-2">"</span>{inquiry}<span class="text-gray-600">"</span>
							</button>
						{/each}
					</div>
				</div>

				<!-- Right: Chat + result -->
				<div class="space-y-4">
					<!-- Chat window -->
					<div class="relative rounded-2xl border border-white/[0.07] bg-white/[0.02] overflow-hidden"
						style="background: radial-gradient(circle at 50% 0%, {selectedBusiness.glow} 0%, transparent 60%), rgba(255,255,255,0.02);">

						<!-- Header -->
						<div class="flex items-center gap-3 px-4 py-3 border-b border-white/[0.06] bg-white/[0.02]">
							<div class="w-8 h-8 rounded-xl bg-gradient-to-br {selectedBusiness.color} flex items-center justify-center text-sm flex-shrink-0">
								{selectedBusiness.icon}
							</div>
							<div class="flex-1 min-w-0">
								<div class="text-xs font-semibold text-white">Dolpai AI · {selectedBusiness.label}</div>
								<div class="flex items-center gap-1 text-[10px] text-gray-500">
									<span class="w-1 h-1 rounded-full {isRunning ? 'bg-green-500 animate-pulse' : 'bg-gray-600'}"></span>
									{isRunning ? 'Responding...' : 'Ready'}
								</div>
							</div>
						</div>

						<!-- Messages -->
						<div bind:this={chatEl} class="px-4 py-4 space-y-3 min-h-[180px] max-h-[220px] overflow-y-auto scroll-smooth">
							{#if chatMessages.length === 0}
								<div class="flex items-center justify-center h-28 text-center">
									<p class="text-xs text-gray-700">Select an inquiry on the left to see Dolpai respond</p>
								</div>
							{/if}
							{#each chatMessages as msg}
								<div class="flex {msg.type === 'user' ? 'justify-end' : 'justify-start gap-2'} animate-in fade-in slide-in-from-bottom-2 duration-300">
									{#if msg.type === 'bot'}
										<div class="w-6 h-6 rounded-full bg-gradient-to-br {selectedBusiness.color} flex-shrink-0 flex items-center justify-center text-[10px] mt-auto">{selectedBusiness.icon}</div>
									{/if}
									<div class="max-w-[82%] px-3.5 py-2.5 rounded-2xl text-sm leading-relaxed
										{msg.type === 'user'
											? 'bg-gradient-to-r from-cyan-600 to-blue-600 text-white rounded-tr-sm'
											: 'bg-white/[0.06] text-gray-100 border border-white/[0.07] rounded-tl-sm'}">
										{msg.text}
									</div>
								</div>
							{/each}
							{#if isTyping}
								<div class="flex justify-start gap-2 animate-in fade-in duration-200">
									<div class="w-6 h-6 rounded-full bg-gradient-to-br {selectedBusiness.color} flex-shrink-0 flex items-center justify-center text-[10px] mt-auto">{selectedBusiness.icon}</div>
									<div class="px-3.5 py-2.5 rounded-2xl rounded-tl-sm bg-white/[0.06] border border-white/[0.07]">
										<div class="flex gap-1.5">
											<div class="w-1.5 h-1.5 bg-cyan-400 rounded-full animate-bounce" style="animation-delay:0ms"></div>
											<div class="w-1.5 h-1.5 bg-cyan-400 rounded-full animate-bounce" style="animation-delay:150ms"></div>
											<div class="w-1.5 h-1.5 bg-cyan-400 rounded-full animate-bounce" style="animation-delay:300ms"></div>
										</div>
									</div>
								</div>
							{/if}
						</div>
					</div>

					<!-- Automation result card -->
					<div class="rounded-2xl border transition-all duration-500 overflow-hidden
						{actionFired ? 'border-green-500/20 bg-green-500/[0.04]' : 'border-white/[0.06] bg-white/[0.02]'}">
						<div class="px-4 py-3.5 space-y-2.5">
							<div class="flex items-center justify-between">
								<span class="text-[10px] font-semibold text-gray-500 uppercase tracking-wider">Automation Triggered</span>
								{#if actionFired}
									<span class="text-[10px] text-green-400 font-semibold animate-in fade-in duration-300">✓ Complete</span>
								{/if}
							</div>
							{#if actionFired}
								<div class="flex items-start gap-2 animate-in fade-in slide-in-from-bottom-2 duration-400">
									<div class="w-1.5 h-1.5 rounded-full bg-green-500 mt-1.5 flex-shrink-0"></div>
									<span class="text-sm text-gray-300 font-mono">{actionFired}</span>
								</div>
								<!-- Lead score -->
								<div class="space-y-1 pt-1">
									<div class="flex justify-between text-[10px]">
										<span class="text-gray-600">Lead Score</span>
										<span class="text-cyan-400 font-bold">{leadScore}</span>
									</div>
									<div class="h-1 rounded-full bg-white/[0.05] overflow-hidden">
										<div class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500 transition-all duration-700"
											style="width:{leadScore}%"></div>
									</div>
								</div>
							{:else}
								<div class="text-[11px] text-gray-700 italic">Waiting for conversation...</div>
							{/if}
						</div>
					</div>

					<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer"
						class="btn-primary w-full justify-center text-sm group">
						Deploy for My {selectedBusiness.label}
						<svg class="w-4 h-4 group-hover:translate-x-0.5 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
						</svg>
					</a>
				</div>
			</div>
		</div>
	</div>
</section>
