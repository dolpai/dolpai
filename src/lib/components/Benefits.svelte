<script>
	const benefits = [
		{
			title: '10x Faster Response',
			description: 'Reply in under 1 second, not hours. Never lose a lead to slow response times again.',
			metric: '10x',
			icon: 'M13 10V3L4 14h7v7l9-11h-7z',
			color: 'cyan'
		},
		{
			title: 'Save 20+ Hours/Week',
			description: 'Automate repetitive conversations and let your team focus on high-value strategic work.',
			metric: '20h',
			icon: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z',
			color: 'blue'
		},
		{
			title: '3x More Conversions',
			description: 'Instant responses and smart follow-ups turn more leads into paying customers.',
			metric: '3x',
			icon: 'M13 7h8m0 0v8m0-8l-8 8-4-4-6 6',
			color: 'violet'
		},
		{
			title: 'Zero Training Required',
			description: 'Set up in minutes with our intuitive interface. No technical skills needed whatsoever.',
			metric: '0',
			icon: 'M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z',
			color: 'cyan'
		},
		{
			title: 'Works While You Sleep',
			description: '24/7 availability means you never miss an opportunity, even at 3 AM on a Sunday.',
			metric: '24/7',
			icon: 'M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z',
			color: 'blue'
		},
		{
			title: 'Scales Infinitely',
			description: 'Handle 10 or 10,000 conversations simultaneously without hiring more staff.',
			metric: '∞',
			icon: 'M7 12l3-3 3 3 4-4M8 21l4-4 4 4M3 4h18M4 4h16v12a1 1 0 01-1 1H5a1 1 0 01-1-1V4z',
			color: 'violet'
		}
	];

	const colorMap = {
		cyan:   { bg: 'bg-cyan-500/10',   border: 'border-cyan-500/20',   icon: 'text-cyan-400',   metric: 'from-cyan-400 to-cyan-300' },
		blue:   { bg: 'bg-blue-500/10',   border: 'border-blue-500/20',   icon: 'text-blue-400',   metric: 'from-blue-400 to-blue-300' },
		violet: { bg: 'bg-violet-500/10', border: 'border-violet-500/20', icon: 'text-violet-400', metric: 'from-violet-400 to-violet-300' }
	};
</script>

<section id="benefits" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/4 right-0 w-80 h-80 rounded-full bg-violet-500/5 blur-[120px]"></div>
		<div class="absolute bottom-1/4 left-0 w-80 h-80 rounded-full bg-cyan-500/5 blur-[120px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Why Dolpai</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Built for <span class="gradient-text">Results</span>
			</h2>
			<p class="text-lg text-gray-500">
				Every feature is designed to drive measurable business outcomes.
			</p>
		</div>

		<!-- Benefits grid -->
		<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-5 max-w-6xl mx-auto">
			{#each benefits as benefit, i}
				{@const c = colorMap[benefit.color]}
				<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 sm:p-7 hover:border-white/[0.12] hover:bg-white/[0.04] transition-all duration-300 overflow-hidden">
					<!-- Hover glow -->
					<div class="absolute top-0 right-0 w-32 h-32 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none rounded-full blur-2xl"
						style="background: radial-gradient(circle, rgba(6,182,212,0.1) 0%, transparent 70%); transform: translate(30%, -30%);">
					</div>

					<div class="relative space-y-4">
						<div class="flex items-start justify-between">
							<div class="w-11 h-11 rounded-xl {c.bg} border {c.border} flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
								<svg class="w-5 h-5 {c.icon}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={benefit.icon} />
								</svg>
							</div>
							<span class="text-2xl font-black bg-gradient-to-r {c.metric} bg-clip-text text-transparent">{benefit.metric}</span>
						</div>
						<div>
							<h3 class="font-semibold text-white mb-2 group-hover:text-cyan-300 transition-colors duration-200">{benefit.title}</h3>
							<p class="text-sm text-gray-500 leading-relaxed">{benefit.description}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
