<script>
	const steps = [
		{
			number: '01',
			title: 'Connect Your Channels',
			description: 'Link WhatsApp, Facebook, Instagram, and your website in one click. No technical setup required.',
			icon: 'M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1'
		},
		{
			number: '02',
			title: 'Train Your AI',
			description: 'Upload your product catalog, FAQs, and brand guidelines. The AI learns your business in minutes.',
			icon: 'M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z'
		},
		{
			number: '03',
			title: 'Go Live & Automate',
			description: 'Activate Dolpai and watch it handle conversations 24/7. Monitor results from your dashboard.',
			icon: 'M5 3l14 9-14 9V3z'
		}
	];
</script>

<section id="how-it-works" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] rounded-full bg-cyan-500/4 blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Process</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Up and Running in <span class="gradient-text">Minutes</span>
			</h2>
			<p class="text-lg text-gray-500">
				Three simple steps to automate your customer interactions forever.
			</p>
		</div>

		<!-- Steps -->
		<div class="max-w-5xl mx-auto">
			<!-- Desktop: horizontal with connector -->
			<div class="hidden lg:grid lg:grid-cols-3 gap-8 relative">
				<!-- Connector line -->
				<div class="absolute top-12 left-[calc(16.67%+2rem)] right-[calc(16.67%+2rem)] h-px">
					<div class="h-full bg-gradient-to-r from-cyan-500/40 via-blue-500/40 to-cyan-500/40"></div>
					<!-- Animated dot -->
					<div class="absolute top-1/2 -translate-y-1/2 w-2 h-2 rounded-full bg-cyan-400 shadow-lg shadow-cyan-400/50 animate-shimmer" style="left: 0; animation: moveRight 3s linear infinite;"></div>
				</div>

				{#each steps as step, i}
					<div class="group text-center space-y-6">
						<!-- Number circle -->
						<div class="relative inline-flex">
							<div class="w-24 h-24 rounded-2xl bg-white/[0.03] border border-white/[0.08] flex items-center justify-center group-hover:border-cyan-500/30 group-hover:bg-cyan-500/5 transition-all duration-300">
								<span class="text-3xl font-black gradient-text">{step.number}</span>
							</div>
							<!-- Icon badge -->
							<div class="absolute -bottom-2 -right-2 w-8 h-8 rounded-lg bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center shadow-lg shadow-cyan-500/30">
								<svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={step.icon} />
								</svg>
							</div>
						</div>

						<div class="space-y-2">
							<h3 class="text-lg font-bold text-white group-hover:text-cyan-300 transition-colors duration-200">{step.title}</h3>
							<p class="text-sm text-gray-500 leading-relaxed">{step.description}</p>
						</div>
					</div>
				{/each}
			</div>

			<!-- Mobile: vertical -->
			<div class="lg:hidden space-y-0">
				{#each steps as step, i}
					<div class="group flex gap-6">
						<!-- Left: number + line -->
						<div class="flex flex-col items-center">
							<div class="w-14 h-14 rounded-xl bg-white/[0.03] border border-white/[0.08] flex items-center justify-center flex-shrink-0 group-hover:border-cyan-500/30 transition-all duration-300">
								<span class="text-xl font-black gradient-text">{step.number}</span>
							</div>
							{#if i < steps.length - 1}
								<div class="w-px flex-1 my-3 bg-gradient-to-b from-cyan-500/30 to-transparent min-h-[40px]"></div>
							{/if}
						</div>

						<!-- Right: content -->
						<div class="pb-10 pt-2 space-y-2 flex-1">
							<h3 class="text-lg font-bold text-white">{step.title}</h3>
							<p class="text-sm text-gray-500 leading-relaxed">{step.description}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Bottom CTA -->
		<div class="text-center mt-16">
			<a href="#contact" class="btn-primary">
				Start Automating Today
				<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
				</svg>
			</a>
		</div>
	</div>
</section>
