<script>
	let activeCase = $state(0);

	const cases = [
		{
			industry: 'Healthcare & Clinics',
			icon: 'M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z',
			color: 'from-red-500 to-pink-600',
			glow: 'rgba(239,68,68,0.12)',
			problem: 'Patients call after hours, miss appointments, and staff spend hours on scheduling calls.',
			automation: 'AI handles appointment booking, sends reminders, answers FAQs about services and insurance.',
			outcome: '60% fewer no-shows · 3 hours saved daily · 24/7 patient support',
			conversation: [
				{ type: 'user', text: 'I need to book a dental checkup for next week' },
				{ type: 'bot',  text: 'Of course! We have slots on Tuesday at 10 AM or Thursday at 2 PM. Which works for you?' },
				{ type: 'user', text: 'Tuesday please' },
				{ type: 'bot',  text: '✅ Booked! Tuesday 10 AM with Dr. Smith. Reminder sent to your phone.' }
			]
		},
		{
			industry: 'Education & Coaching',
			icon: 'M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253',
			color: 'from-blue-500 to-violet-600',
			glow: 'rgba(59,130,246,0.12)',
			problem: 'Prospective students ask the same questions repeatedly. Enrollment team is overwhelmed.',
			automation: 'AI qualifies leads, answers course questions, shares brochures, and books discovery calls.',
			outcome: '4x more enrollments · 80% fewer repetitive queries · Instant lead follow-up',
			conversation: [
				{ type: 'user', text: 'What courses do you offer for digital marketing?' },
				{ type: 'bot',  text: 'We offer 3 programs: Beginner (4 weeks), Advanced (8 weeks), and Pro Certification (12 weeks). Which level suits you?' },
				{ type: 'user', text: 'Advanced sounds good. What\'s the fee?' },
				{ type: 'bot',  text: 'Advanced is $299. Want me to book a free discovery call with our advisor?' }
			]
		},
		{
			industry: 'Restaurants & Food',
			icon: 'M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z',
			color: 'from-orange-500 to-red-600',
			glow: 'rgba(249,115,22,0.12)',
			problem: 'Missed reservation calls, manual order taking, and no way to handle peak-hour inquiries.',
			automation: 'AI takes reservations, answers menu questions, handles delivery inquiries, and upsells specials.',
			outcome: '2x more reservations · Zero missed calls · Automated upselling',
			conversation: [
				{ type: 'user', text: 'Do you have a table for 4 this Saturday at 7pm?' },
				{ type: 'bot',  text: 'Yes! Saturday 7 PM for 4 guests is available. Shall I confirm the reservation?' },
				{ type: 'user', text: 'Yes please, name is Johnson' },
				{ type: 'bot',  text: '✅ Reserved! Table for 4 — Saturday 7 PM under Johnson. See you then! 🍽️' }
			]
		},
		{
			industry: 'Service Businesses',
			icon: 'M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z M15 12a3 3 0 11-6 0 3 3 0 016 0z',
			color: 'from-cyan-500 to-blue-600',
			glow: 'rgba(6,182,212,0.12)',
			problem: 'Plumbers, salons, and agencies lose leads when they\'re busy on-site or after hours.',
			automation: 'AI captures leads, qualifies job requirements, provides quotes, and books service visits.',
			outcome: '5x more leads captured · Instant quote delivery · No missed opportunities',
			conversation: [
				{ type: 'user', text: 'I need a plumber for a leaking pipe, how much?' },
				{ type: 'bot',  text: 'We can help! Standard pipe repair starts at $80. Can you share your location and a photo?' },
				{ type: 'user', text: 'Sure, I\'m in downtown. Sending photo now' },
				{ type: 'bot',  text: 'Got it! A plumber can be there today at 3 PM. Shall I confirm the booking?' }
			]
		},
		{
			industry: 'Agencies & Consultants',
			icon: 'M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z',
			color: 'from-violet-500 to-purple-700',
			glow: 'rgba(139,92,246,0.12)',
			problem: 'High-value leads go cold while waiting for a proposal. Discovery calls are hard to schedule.',
			automation: 'AI qualifies prospects, shares case studies, books discovery calls, and sends follow-ups.',
			outcome: '3x faster sales cycle · 90% lead response rate · Automated nurturing',
			conversation: [
				{ type: 'user', text: 'We need help with our social media marketing' },
				{ type: 'bot',  text: 'Great! We specialize in social media growth. What\'s your monthly budget range?' },
				{ type: 'user', text: 'Around $2,000/month' },
				{ type: 'bot',  text: 'Perfect fit! Let me book a 30-min strategy call with our team. When works for you?' }
			]
		}
	];
</script>

<section id="use-cases" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/4 right-0 w-80 h-80 rounded-full bg-violet-500/4 blur-[120px]"></div>
		<div class="absolute bottom-1/4 left-0 w-80 h-80 rounded-full bg-cyan-500/4 blur-[120px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-14 sm:mb-18">
			<div class="section-label">Use Cases</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Built for Your <span class="gradient-text">Industry</span>
			</h2>
			<p class="text-lg text-gray-500">
				Dolpai adapts to your business. See how it works across different industries.
			</p>
		</div>

		<!-- Industry tabs -->
		<div class="flex flex-wrap justify-center gap-2 mb-10">
			{#each cases as c, i}
				<button
					onclick={() => activeCase = i}
					class="px-4 py-2 rounded-xl text-sm font-medium transition-all duration-200
						{activeCase === i
							? 'bg-white/[0.08] border border-white/[0.15] text-white'
							: 'border border-white/[0.05] bg-white/[0.02] text-gray-500 hover:text-gray-300 hover:border-white/[0.10]'}"
				>
					{c.industry}
				</button>
			{/each}
		</div>

		<!-- Active case content -->
		{#each cases as c, i}
			{#if activeCase === i}
				<div class="grid lg:grid-cols-2 gap-8 max-w-5xl mx-auto animate-in fade-in duration-300">

					<!-- Left: Case details -->
					<div class="space-y-5">
						<!-- Industry header -->
						<div class="flex items-center gap-4">
							<div class="w-12 h-12 rounded-2xl bg-gradient-to-br {c.color} flex items-center justify-center shadow-lg flex-shrink-0">
								<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={c.icon}/>
								</svg>
							</div>
							<h3 class="text-xl font-bold text-white">{c.industry}</h3>
						</div>

						<!-- Problem -->
						<div class="rounded-2xl border border-red-500/10 bg-red-500/[0.04] p-5">
							<div class="flex items-center gap-2 mb-2">
								<svg class="w-4 h-4 text-red-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/>
								</svg>
								<span class="text-xs font-semibold text-red-400 uppercase tracking-wider">The Problem</span>
							</div>
							<p class="text-sm text-gray-400 leading-relaxed">{c.problem}</p>
						</div>

						<!-- Automation -->
						<div class="rounded-2xl border border-cyan-500/10 bg-cyan-500/[0.04] p-5">
							<div class="flex items-center gap-2 mb-2">
								<svg class="w-4 h-4 text-cyan-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
								</svg>
								<span class="text-xs font-semibold text-cyan-400 uppercase tracking-wider">Dolpai Automation</span>
							</div>
							<p class="text-sm text-gray-400 leading-relaxed">{c.automation}</p>
						</div>

						<!-- Outcome -->
						<div class="rounded-2xl border border-green-500/10 bg-green-500/[0.04] p-5">
							<div class="flex items-center gap-2 mb-2">
								<svg class="w-4 h-4 text-green-400 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
								</svg>
								<span class="text-xs font-semibold text-green-400 uppercase tracking-wider">Outcome</span>
							</div>
							<p class="text-sm text-green-300 font-medium leading-relaxed">{c.outcome}</p>
						</div>
					</div>

					<!-- Right: Sample conversation -->
					<div class="relative">
						<div class="absolute inset-0 rounded-2xl pointer-events-none"
							style="background: radial-gradient(circle at 50% 50%, {c.glow} 0%, transparent 70%);">
						</div>
						<div class="relative glass-card overflow-hidden">
							<!-- Chat header -->
							<div class="flex items-center gap-3 px-5 py-3.5 border-b border-white/[0.07] bg-white/[0.02]">
								<div class="w-8 h-8 rounded-xl bg-gradient-to-br {c.color} flex items-center justify-center flex-shrink-0">
									<svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={c.icon}/>
									</svg>
								</div>
								<div class="flex-1">
									<div class="text-xs font-semibold text-white">Dolpai AI · {c.industry}</div>
									<div class="flex items-center gap-1 text-[10px] text-gray-500">
										<span class="w-1.5 h-1.5 bg-green-500 rounded-full animate-pulse"></span>
										Active
									</div>
								</div>
							</div>

							<!-- Messages -->
							<div class="px-5 py-5 space-y-3">
								{#each c.conversation as msg}
									<div class="flex {msg.type === 'user' ? 'justify-end' : 'justify-start gap-2'}">
										{#if msg.type === 'bot'}
											<div class="w-6 h-6 rounded-full bg-gradient-to-br {c.color} flex-shrink-0 flex items-center justify-center text-[9px] font-bold text-white mt-auto">D</div>
										{/if}
										<div class="max-w-[80%] px-3.5 py-2.5 rounded-2xl text-sm leading-relaxed
											{msg.type === 'user'
												? 'bg-gradient-to-r from-cyan-600 to-blue-600 text-white rounded-tr-sm'
												: 'bg-white/[0.06] text-gray-100 border border-white/[0.07] rounded-tl-sm'}">
											{msg.text}
										</div>
									</div>
								{/each}
							</div>

							<!-- Footer tag -->
							<div class="px-5 py-3 border-t border-white/[0.07] bg-white/[0.02] flex items-center justify-between">
								<span class="text-[10px] text-gray-600">Powered by Dolpai AI</span>
								<span class="text-[10px] text-green-400 font-semibold">✓ Automated</span>
							</div>
						</div>
					</div>
				</div>
			{/if}
		{/each}
	</div>
</section>
