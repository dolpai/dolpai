<script>
	import { onMount, tick } from 'svelte';

	// ── State ──────────────────────────────────────────────────────
	/** @type {Array<{type:string,text:string,tag?:string,score?:number,action?:string}>} */
	let messages = $state([]);
	let isTyping = $state(false);
	let automationLog = $state(/** @type {string[]} */ ([]));
	let leadScore = $state(0);
	let isRunning = $state(false);
	let isDone = $state(false);
	let activeAction = $state('');
	/** @type {ReturnType<typeof setTimeout>[]} */
	let timeouts = [];
	/** @type {HTMLDivElement|null} */
	let chatScroll = $state(null);

	// ── Preset quick-send messages ─────────────────────────────────
	const presets = [
		{ label: 'Book appointment',  icon: '📅', text: 'I want to book an appointment for next week' },
		{ label: 'Check pricing',     icon: '💰', text: 'What are your pricing plans?' },
		{ label: 'Product inquiry',   icon: '📦', text: 'Do you have the iPhone 15 in stock?' },
		{ label: 'Get a quote',       icon: '📋', text: 'Can I get a quote for your services?' }
	];

	// ── Conversation scripts keyed by preset ──────────────────────
	const scripts = {
		'I want to book an appointment for next week': [
			{ type: 'bot', text: 'Of course! We have slots available Monday–Friday. Do you prefer morning or afternoon?', delay: 1100, tag: 'Booking Intent', score: 78 },
			{ type: 'user', text: 'Morning, preferably Tuesday', delay: 1400 },
			{ type: 'bot', text: 'Tuesday 10 AM works perfectly. Can I get your name and email to confirm?', delay: 1200, tag: 'Qualifying', score: 85 },
			{ type: 'user', text: 'Sarah Johnson, sarah@example.com', delay: 1600 },
			{ type: 'bot', text: '✅ Appointment confirmed — Tuesday 10 AM. Confirmation sent to sarah@example.com. See you then!', delay: 1400, tag: 'Booked', score: 96, action: 'booked' }
		],
		'What are your pricing plans?': [
			{ type: 'bot', text: 'We have three plans: Starter ($49/mo), Professional ($149/mo), and Business ($299/mo). All include a 14-day free trial. Which fits your team size?', delay: 1100, tag: 'Pricing Inquiry', score: 65 },
			{ type: 'user', text: 'We\'re a team of 5, growing fast', delay: 1500 },
			{ type: 'bot', text: 'Professional is perfect for growing teams — unlimited channels, advanced AI, and priority support. Want me to set up a free trial?', delay: 1300, tag: 'Qualified', score: 82 },
			{ type: 'user', text: 'Yes, let\'s do it', delay: 1200 },
			{ type: 'bot', text: '🚀 Trial activated! Check your email for setup instructions. Your AI agent will be live in under 10 minutes.', delay: 1400, tag: 'Converted', score: 94, action: 'trial' }
		],
		'Do you have the iPhone 15 in stock?': [
			{ type: 'bot', text: 'Yes! iPhone 15 is available in all colors — Black, Blue, Pink, Yellow, and Green. Which color interests you?', delay: 1000, tag: 'Product Inquiry', score: 72 },
			{ type: 'user', text: 'Blue, 256GB', delay: 1400 },
			{ type: 'bot', text: 'iPhone 15 Blue 256GB is $899. We have 3 units left. Would you like to reserve one or visit our store?', delay: 1200, tag: 'Purchase Intent', score: 88 },
			{ type: 'user', text: 'Reserve it please', delay: 1300 },
			{ type: 'bot', text: '✅ Reserved! iPhone 15 Blue 256GB held for 24 hours. Visit us at your convenience to complete the purchase.', delay: 1400, tag: 'Reserved', score: 95, action: 'reserved' }
		],
		'Can I get a quote for your services?': [
			{ type: 'bot', text: 'Happy to help! To give you an accurate quote, what type of business do you run and how many customer messages do you receive per day?', delay: 1100, tag: 'Lead Capture', score: 60 },
			{ type: 'user', text: 'We run a dental clinic, about 50 messages/day', delay: 1600 },
			{ type: 'bot', text: 'For a dental clinic at that volume, our Professional plan ($149/mo) covers everything — appointment booking, reminders, and patient FAQs. Want a custom demo?', delay: 1300, tag: 'Qualified', score: 84 },
			{ type: 'user', text: 'Yes, book me a demo', delay: 1200 },
			{ type: 'bot', text: '📅 Demo booked! Our team will reach out within 2 hours to schedule your personalized walkthrough.', delay: 1400, tag: 'Demo Booked', score: 93, action: 'booked' }
		]
	};

	// ── Automation events per action ──────────────────────────────
	const actionEvents = {
		booked:   ['🔍 Lead qualified', '📅 Calendar slot reserved', '📧 Confirmation email sent', '🗂️ CRM contact created', '🔔 Team notified via Slack'],
		trial:    ['🔍 Lead qualified', '🚀 Trial account provisioned', '📧 Setup email dispatched', '🗂️ CRM deal created', '📊 Onboarding sequence started'],
		reserved: ['🔍 Lead qualified', '📦 Inventory hold placed', '📧 Reservation confirmation sent', '🗂️ CRM record created', '🔔 Sales team alerted'],
		default:  ['🔍 Lead qualified', '📈 Intent scored', '🗂️ CRM record created', '🔔 Team notified']
	};

	// ── Run a conversation from a preset ─────────────────────────
	/** @param {string} userText */
	async function runConversation(userText) {
		if (isRunning) return;
		clearAll();
		isRunning = true;
		isDone = false;
		leadScore = 0;

		// Push user message immediately
		messages = [{ type: 'user', text: userText }];
		await scrollChat();

		const script = scripts[userText] || scripts['Do you have the iPhone 15 in stock?'];
		let elapsed = 0;

		for (let i = 0; i < script.length; i++) {
			const msg = script[i];
			elapsed += msg.delay;

			const t = setTimeout(async () => {
				if (msg.type === 'bot') {
					isTyping = true;
					await scrollChat();
					const t2 = setTimeout(async () => {
						isTyping = false;
						messages = [...messages, msg];
						if (msg.score) leadScore = msg.score;
						if (msg.action) activeAction = msg.action;
						await scrollChat();

						// Fire automation events after last bot message
						if (i === script.length - 1) {
							const events = actionEvents[msg.action || 'default'] || actionEvents.default;
							events.forEach((ev, ei) => {
								const et = setTimeout(() => {
									automationLog = [...automationLog, ev];
								}, 600 + ei * 700);
								timeouts.push(et);
							});
							const doneT = setTimeout(() => {
								isRunning = false;
								isDone = true;
							}, 600 + events.length * 700 + 400);
							timeouts.push(doneT);
						}
					}, 900);
					timeouts.push(t2);
				} else {
					messages = [...messages, msg];
					await scrollChat();
				}
			}, elapsed);
			timeouts.push(t);
		}
	}

	async function scrollChat() {
		await tick();
		if (chatScroll) chatScroll.scrollTop = chatScroll.scrollHeight;
	}

	function clearAll() {
		timeouts.forEach(clearTimeout);
		timeouts = [];
		messages = [];
		automationLog = [];
		isTyping = false;
		leadScore = 0;
		activeAction = '';
		isDone = false;
	}

	function reset() {
		clearAll();
		isRunning = false;
	}

	onMount(() => () => timeouts.forEach(clearTimeout));

	// Score color
	/** @param {number} s */
	function scoreColor(s) {
		if (s >= 90) return 'text-green-400';
		if (s >= 75) return 'text-cyan-400';
		if (s >= 60) return 'text-blue-400';
		return 'text-gray-400';
	}
	/** @param {number} s */
	function scoreBarColor(s) {
		if (s >= 90) return 'from-green-500 to-cyan-500';
		if (s >= 75) return 'from-cyan-500 to-blue-500';
		return 'from-blue-500 to-violet-500';
	}
</script>

<section id="demo" class="section-padding relative overflow-hidden bg-[#030712]">
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[700px] h-[700px] rounded-full bg-cyan-500/4 blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-4 mb-12">
			<div class="section-label">Interactive Demo</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Try It <span class="gradient-text">Yourself</span>
			</h2>
			<p class="text-lg text-gray-500">
				Click a message below and watch Dolpai respond, qualify the lead, and trigger the full automation pipeline in real time.
			</p>
		</div>

		<!-- Preset buttons -->
		<div class="flex flex-wrap justify-center gap-2.5 mb-10 max-w-3xl mx-auto">
			{#each presets as preset}
				<button
					onclick={() => runConversation(preset.text)}
					disabled={isRunning}
					class="flex items-center gap-2 px-4 py-2.5 rounded-xl border text-sm font-medium transition-all duration-200
						{isRunning
							? 'border-white/[0.04] bg-white/[0.01] text-gray-700 cursor-not-allowed'
							: 'border-white/[0.08] bg-white/[0.03] text-gray-300 hover:border-cyan-500/30 hover:bg-cyan-500/5 hover:text-white active:scale-[0.97]'}"
				>
					<span>{preset.icon}</span>
					<span>{preset.label}</span>
				</button>
			{/each}
			{#if messages.length > 0}
				<button
					onclick={reset}
					class="flex items-center gap-2 px-4 py-2.5 rounded-xl border border-white/[0.06] bg-white/[0.02] text-gray-500 hover:text-white hover:border-white/[0.12] text-sm font-medium transition-all duration-200 active:scale-[0.97]"
				>
					<svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/>
					</svg>
					Reset
				</button>
			{/if}
		</div>

		<div class="grid lg:grid-cols-5 gap-5 max-w-5xl mx-auto">

			<!-- ── Chat window (3 cols) ── -->
			<div class="lg:col-span-3 relative">
				<div class="absolute inset-0 rounded-2xl bg-cyan-500/4 blur-2xl scale-105 pointer-events-none"></div>
				<div class="relative glass-card overflow-hidden shadow-2xl shadow-cyan-500/8 {isRunning ? 'animate-border-glow' : ''}">

					<!-- Chat header -->
					<div class="flex items-center gap-3 px-5 py-3.5 border-b border-white/[0.07] bg-white/[0.02]">
						<div class="w-9 h-9 rounded-xl bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center shadow-lg shadow-cyan-500/30 flex-shrink-0">
							<svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17H3a2 2 0 01-2-2V5a2 2 0 012-2h14a2 2 0 012 2v3"/>
							</svg>
						</div>
						<div class="flex-1 min-w-0">
							<div class="font-semibold text-white text-sm">Dolpai AI Agent</div>
							<div class="flex items-center gap-1.5 text-[10px] text-gray-500">
								<span class="w-1.5 h-1.5 rounded-full {isRunning ? 'bg-green-500 animate-pulse' : 'bg-gray-600'}"></span>
								<span>{isRunning ? 'Processing conversation...' : isDone ? 'Automation complete' : 'Ready — click a message above'}</span>
							</div>
						</div>
						<div class="flex gap-1.5">
							<div class="w-2.5 h-2.5 rounded-full bg-red-500/50"></div>
							<div class="w-2.5 h-2.5 rounded-full bg-yellow-500/50"></div>
							<div class="w-2.5 h-2.5 rounded-full bg-green-500/50"></div>
						</div>
					</div>

					<!-- Messages area -->
					<div bind:this={chatScroll} class="px-5 py-5 space-y-3 min-h-[320px] max-h-[380px] overflow-y-auto scroll-smooth">
						{#if messages.length === 0}
							<div class="flex flex-col items-center justify-center h-48 space-y-3 text-center">
								<div class="w-12 h-12 rounded-2xl bg-white/[0.04] border border-white/[0.07] flex items-center justify-center">
									<svg class="w-6 h-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/>
									</svg>
								</div>
								<p class="text-sm text-gray-600">Select a message above to start the demo</p>
							</div>
						{/if}

						{#each messages as message}
							<div class="flex {message.type === 'user' ? 'justify-end' : 'justify-start gap-2'} animate-in fade-in slide-in-from-bottom-2 duration-300">
								{#if message.type === 'bot'}
									<div class="w-7 h-7 rounded-full bg-gradient-to-br from-cyan-500 to-blue-600 flex-shrink-0 flex items-center justify-center text-[10px] font-bold text-white mt-auto">D</div>
								{/if}
								<div class="max-w-[78%] space-y-1">
									<div class="px-4 py-2.5 rounded-2xl text-sm leading-relaxed
										{message.type === 'user'
											? 'bg-gradient-to-r from-cyan-600 to-blue-600 text-white rounded-tr-sm shadow-lg'
											: 'bg-white/[0.06] text-gray-100 border border-white/[0.07] rounded-tl-sm'}">
										{message.text}
									</div>
									{#if message.type === 'bot' && message.tag}
										<div class="flex items-center gap-2 pl-1">
											<span class="text-[9px] px-2 py-0.5 rounded-full bg-cyan-500/10 border border-cyan-500/20 text-cyan-400 font-semibold">{message.tag}</span>
											{#if message.score}
												<span class="text-[9px] text-gray-600">Score: <span class="{scoreColor(message.score)} font-bold">{message.score}</span></span>
											{/if}
										</div>
									{/if}
								</div>
							</div>
						{/each}

						{#if isTyping}
							<div class="flex justify-start gap-2 animate-in fade-in duration-200">
								<div class="w-7 h-7 rounded-full bg-gradient-to-br from-cyan-500 to-blue-600 flex-shrink-0 flex items-center justify-center text-[10px] font-bold text-white">D</div>
								<div class="px-4 py-3 rounded-2xl rounded-tl-sm bg-white/[0.06] border border-white/[0.07]">
									<div class="flex gap-1.5 items-center">
										<div class="w-1.5 h-1.5 bg-cyan-400 rounded-full animate-bounce" style="animation-delay:0ms"></div>
										<div class="w-1.5 h-1.5 bg-cyan-400 rounded-full animate-bounce" style="animation-delay:150ms"></div>
										<div class="w-1.5 h-1.5 bg-cyan-400 rounded-full animate-bounce" style="animation-delay:300ms"></div>
										<span class="text-[10px] text-gray-600 ml-1">AI thinking...</span>
									</div>
								</div>
							</div>
						{/if}

						{#if isDone}
							<div class="flex justify-center animate-in fade-in duration-400">
								<div class="flex items-center gap-2 px-4 py-2 rounded-full bg-green-500/10 border border-green-500/20">
									<svg class="w-3.5 h-3.5 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M5 13l4 4L19 7"/>
									</svg>
									<span class="text-[11px] text-green-400 font-semibold">Automation complete — all 5 actions triggered</span>
								</div>
							</div>
						{/if}
					</div>

					<!-- Input bar -->
					<div class="px-5 py-3.5 border-t border-white/[0.07] bg-white/[0.02]">
						<div class="flex items-center gap-3 px-4 py-2.5 rounded-xl bg-white/[0.04] border border-white/[0.07] {isRunning ? 'opacity-30' : 'opacity-50'}">
							<input type="text" placeholder={isRunning ? 'AI is responding...' : 'Click a preset above to send a message'} disabled class="flex-1 bg-transparent text-gray-500 text-sm outline-none"/>
							<svg class="w-4 h-4 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"/>
							</svg>
						</div>
					</div>
				</div>
			</div>

			<!-- ── Intelligence panel (2 cols) ── -->
			<div class="lg:col-span-2 space-y-4">

				<!-- Lead score card -->
				<div class="glass-card p-4 space-y-3">
					<div class="flex items-center justify-between">
						<span class="text-xs font-semibold text-gray-500 uppercase tracking-wider">Lead Intelligence</span>
						<span class="text-[10px] {isRunning ? 'text-cyan-400' : 'text-gray-600'} font-semibold transition-colors duration-300">
							{isRunning ? '● Live' : isDone ? '✓ Complete' : 'Idle'}
						</span>
					</div>
					<div class="space-y-2.5">
						<!-- Lead score bar -->
						<div class="space-y-1">
							<div class="flex justify-between text-[10px]">
								<span class="text-gray-500">Lead Score</span>
								<span class="{leadScore > 0 ? scoreColor(leadScore) : 'text-gray-600'} font-bold transition-colors duration-300">
									{leadScore > 0 ? leadScore : '—'}
								</span>
							</div>
							<div class="h-1.5 rounded-full bg-white/[0.06] overflow-hidden">
								<div class="h-full rounded-full bg-gradient-to-r {scoreBarColor(leadScore)} transition-all duration-700"
									style="width: {leadScore}%"></div>
							</div>
						</div>
						<!-- Fixed metrics -->
						{#each [
							{ label: 'AI Confidence', value: '94%', width: '94%', color: 'from-blue-500 to-violet-500' },
							{ label: 'Intent Match',  value: '98%', width: '98%', color: 'from-green-500 to-cyan-500' }
						] as m}
							<div class="space-y-1">
								<div class="flex justify-between text-[10px]">
									<span class="text-gray-500">{m.label}</span>
									<span class="text-white font-bold">{m.value}</span>
								</div>
								<div class="h-1.5 rounded-full bg-white/[0.06] overflow-hidden">
									<div class="h-full rounded-full bg-gradient-to-r {m.color}" style="width:{m.width}"></div>
								</div>
							</div>
						{/each}
					</div>
				</div>

				<!-- Automation log -->
				<div class="glass-card p-4 space-y-3">
					<div class="flex items-center justify-between">
						<span class="text-xs font-semibold text-gray-500 uppercase tracking-wider">Automation Log</span>
						<div class="flex items-center gap-1 text-[10px] {isRunning || isDone ? 'text-green-400' : 'text-gray-600'} transition-colors duration-300">
							<span class="w-1.5 h-1.5 rounded-full {isRunning ? 'bg-green-500 animate-pulse' : isDone ? 'bg-green-500' : 'bg-gray-700'}"></span>
							{isRunning ? 'Running' : isDone ? 'Done' : 'Waiting'}
						</div>
					</div>
					<div class="space-y-2 min-h-[140px]">
						{#if automationLog.length === 0}
							<div class="text-[11px] text-gray-700 italic pt-1">
								{isRunning ? 'Waiting for conversation to complete...' : 'Automation events will appear here'}
							</div>
						{/if}
						{#each automationLog as event, i}
							<div class="flex items-start gap-2 animate-in fade-in slide-in-from-left-2 duration-300">
								<div class="w-1.5 h-1.5 rounded-full bg-cyan-500 mt-1.5 flex-shrink-0 animate-pulse" style="animation-delay:{i*100}ms"></div>
								<span class="text-[11px] text-gray-300 font-mono leading-relaxed">{event}</span>
							</div>
						{/each}
					</div>
				</div>

				<!-- CTA -->
				<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer"
					class="btn-primary w-full justify-center text-sm group">
					Deploy This for My Business
					<svg class="w-4 h-4 group-hover:translate-x-0.5 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
					</svg>
				</a>
			</div>
		</div>
	</div>
</section>
