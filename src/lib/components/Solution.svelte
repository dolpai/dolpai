<script>
	const metrics = [
		{ stat: '<1s',  label: 'Response Time',        icon: 'M13 10V3L4 14h7v7l9-11h-7z' },
		{ stat: '24/7', label: 'Always Available',     icon: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z' },
		{ stat: '95%',  label: 'Satisfaction Rate',    icon: 'M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z' },
		{ stat: '3x',   label: 'More Conversions',     icon: 'M13 7h8m0 0v8m0-8l-8 8-4-4-6 6' }
	];
</script>

<section class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider line -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background glow -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 right-1/4 w-96 h-96 rounded-full bg-cyan-500/6 blur-[120px]"></div>
	</div>

	<div class="section-container relative z-10">
		<div class="max-w-5xl mx-auto">
			<div class="grid lg:grid-cols-2 gap-12 lg:gap-16 items-center">

				<!-- Left: Text -->
				<div class="space-y-8">
					<div class="space-y-5">
						<div class="section-label">The Solution</div>
						<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white leading-tight">
							Meet Your
							<span class="gradient-text block">AI Assistant</span>
						</h2>
						<p class="text-lg text-gray-400 leading-relaxed">
							Dolpai deploys intelligent AI agents that handle customer conversations automatically — responding instantly, qualifying leads, and booking appointments while learning from every interaction.
						</p>
					</div>

					<ul class="space-y-4">
						{#each [
							'Responds to every message in under 1 second',
							'Works across WhatsApp, Instagram, Facebook & web',
							'Learns your brand voice and product catalog',
							'Escalates complex issues to your team seamlessly'
						] as item}
							<li class="flex items-start gap-3">
								<div class="flex-shrink-0 w-5 h-5 rounded-full bg-cyan-500/20 border border-cyan-500/30 flex items-center justify-center mt-0.5">
									<svg class="w-3 h-3 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
									</svg>
								</div>
								<span class="text-gray-300 text-sm leading-relaxed">{item}</span>
							</li>
						{/each}
					</ul>

					<a href="#contact" class="btn-primary inline-flex">
						See How It Works
						<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
						</svg>
					</a>
				</div>

				<!-- Right: Metrics grid -->
				<div class="grid grid-cols-2 gap-4">
					{#each metrics as metric, i}
						<div class="group relative rounded-2xl border border-white/[0.07] bg-white/[0.03] p-6 hover:border-cyan-500/20 hover:bg-white/[0.05] transition-all duration-300 overflow-hidden">
							<!-- Hover glow -->
							<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
								style="background: radial-gradient(circle at 50% 100%, rgba(6,182,212,0.08) 0%, transparent 70%);">
							</div>

							<div class="relative space-y-3">
								<div class="w-10 h-10 rounded-xl bg-cyan-500/10 border border-cyan-500/20 flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
									<svg class="w-5 h-5 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={metric.icon} />
									</svg>
								</div>
								<div class="text-3xl font-extrabold gradient-text">{metric.stat}</div>
								<div class="text-xs text-gray-500 font-medium uppercase tracking-wider">{metric.label}</div>
							</div>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</div>
</section>
