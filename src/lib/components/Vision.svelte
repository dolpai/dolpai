<section id="vision" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] rounded-full"
			style="background: radial-gradient(circle, rgba(6,182,212,0.05) 0%, rgba(37,99,235,0.04) 50%, transparent 70%);">
		</div>
	</div>
	<div class="absolute inset-0 grid-overlay opacity-30 pointer-events-none"></div>

	<div class="section-container relative z-10">
		<div class="max-w-4xl mx-auto">

			<!-- Company identity bar -->
			<div class="flex items-center justify-center gap-3 mb-16">
				<div class="h-px flex-1 bg-gradient-to-r from-transparent to-white/[0.08]"></div>
				<div class="flex items-center gap-2.5 px-5 py-2 rounded-full border border-white/[0.08] bg-white/[0.03]">
					<div class="w-5 h-5 rounded-md bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center">
						<span class="text-white font-black text-[10px]">D</span>
					</div>
					<span class="text-xs font-semibold text-gray-400 tracking-widest uppercase">Dolpai Labs</span>
				</div>
				<div class="h-px flex-1 bg-gradient-to-l from-transparent to-white/[0.08]"></div>
			</div>

			<!-- Main narrative -->
			<div class="text-center space-y-8 mb-16">
				<h2 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold tracking-tight text-white leading-tight">
					We built Dolpai because<br class="hidden sm:block"/>
					<span class="gradient-text">businesses deserve better.</span>
				</h2>
				<p class="text-lg sm:text-xl text-gray-400 leading-relaxed max-w-3xl mx-auto font-light">
					Every day, thousands of businesses lose customers not because their product is bad — but because no one replied in time. A message goes unanswered. A lead goes cold. A booking never happens.
				</p>
				<p class="text-lg text-gray-500 leading-relaxed max-w-2xl mx-auto">
					Dolpai exists to close that gap. We build intelligent automation systems that keep businesses connected to their customers — at any hour, at any scale.
				</p>
			</div>

			<!-- Three pillars -->
			<div class="grid sm:grid-cols-3 gap-5">
				{#each [
					{
						title: 'Always-On Communication',
						body: 'Your AI agent handles every inquiry the moment it arrives — whether it\'s 9 AM or 3 AM. No delays, no missed opportunities.',
						icon: 'M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z',
						accent: 'cyan'
					},
					{
						title: 'Intelligent Workflows',
						body: 'Every conversation triggers a chain of automated actions — qualification, booking, CRM sync, team alerts. One message. Five outcomes.',
						icon: 'M13 10V3L4 14h7v7l9-11h-7z',
						accent: 'blue'
					},
					{
						title: 'Built to Scale',
						body: 'From a single-location business to a multi-channel enterprise — Dolpai\'s infrastructure grows with you without adding complexity.',
						icon: 'M7 12l3-3 3 3 4-4M8 21l4-4 4 4M3 4h18M4 4h16v12a1 1 0 01-1 1H5a1 1 0 01-1-1V4z',
						accent: 'violet'
					}
				] as pillar}
					<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 hover:border-white/[0.12] hover:bg-white/[0.04] transition-all duration-300 overflow-hidden text-center">
						<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
							style="background: radial-gradient(circle at 50% 0%, rgba(6,182,212,0.06) 0%, transparent 70%);">
						</div>
						<div class="relative space-y-3">
							<div class="w-10 h-10 rounded-xl mx-auto
								{pillar.accent === 'cyan' ? 'bg-cyan-500/10 border border-cyan-500/20' : pillar.accent === 'blue' ? 'bg-blue-500/10 border border-blue-500/20' : 'bg-violet-500/10 border border-violet-500/20'}
								flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
								<svg class="w-5 h-5 {pillar.accent === 'cyan' ? 'text-cyan-400' : pillar.accent === 'blue' ? 'text-blue-400' : 'text-violet-400'}"
									fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={pillar.icon}/>
								</svg>
							</div>
							<h3 class="font-semibold text-white text-sm">{pillar.title}</h3>
							<p class="text-xs text-gray-500 leading-relaxed">{pillar.body}</p>
						</div>
					</div>
				{/each}
			</div>

			<!-- Mission statement -->
			<div class="mt-14 text-center">
				<div class="inline-block relative">
					<div class="absolute inset-0 rounded-2xl bg-cyan-500/5 blur-xl pointer-events-none"></div>
					<div class="relative rounded-2xl border border-white/[0.07] bg-white/[0.02] px-8 py-6 max-w-2xl">
						<p class="text-sm text-gray-400 leading-relaxed italic">
							"Our mission is to make intelligent automation accessible to every business — not just enterprises with engineering teams. If you have customers, you need Dolpai."
						</p>
						<div class="flex items-center justify-center gap-3 mt-4">
							<div class="w-8 h-8 rounded-full bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center text-xs font-bold text-white">D</div>
							<div class="text-left">
								<div class="text-xs font-semibold text-white">Dolpai Labs</div>
								<div class="text-[10px] text-gray-600">AI Automation · Est. 2024</div>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<script>
	// No reactive state needed — static section
</script>
