<section class="section-padding relative">
	<!-- Section overlay -->
	<div class="absolute inset-0 section-overlay"></div>
	
	<div class="section-container relative z-10">
		<div class="max-w-3xl mx-auto text-center space-y-12">
			<div class="space-y-6">
				<div class="inline-flex items-center space-x-2 px-4 py-2 bg-red-500/10 backdrop-blur-sm border border-red-500/20 rounded-full text-sm text-red-400">
					<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20">
						<path fill-rule="evenodd" d="M8.257 3.099c.765-1.36 2.722-1.36 3.486 0l5.58 9.92c.75 1.334-.213 2.98-1.742 2.98H4.42c-1.53 0-2.493-1.646-1.743-2.98l5.58-9.92zM11 13a1 1 0 11-2 0 1 1 0 012 0zm-1-8a1 1 0 00-1 1v3a1 1 0 002 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
					</svg>
					<span>The Hidden Cost of Slow Responses</span>
				</div>
				<h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold">
					Losing Customers <span class="gradient-text">While You Sleep?</span>
				</h2>
				<p class="text-lg sm:text-xl text-gray-400">
					Every missed message is a missed opportunity
				</p>
			</div>

			<div class="grid gap-6 sm:gap-8">
				{#each problems as problem, i}
					<div class="card flex items-start space-x-4 text-left group" style="animation-delay: {i * 100}ms">
						<div class="flex-shrink-0 w-12 h-12 rounded-lg bg-red-500/10 border border-red-500/20 flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
							<svg class="w-6 h-6 text-red-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
							</svg>
						</div>
						<div class="flex-1 space-y-2">
							<h3 class="text-lg sm:text-xl font-semibold text-white group-hover:text-red-400 transition-colors">{problem.title}</h3>
							<p class="text-gray-400">{problem.description}</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</div>
</section>

<script>
	const problems = [
		{
			title: 'Delayed Responses',
			description: 'Customers expect instant replies. Every hour of delay reduces conversion by 10%.'
		},
		{
			title: 'Overwhelmed Team',
			description: 'Your team can\'t handle the volume. Messages pile up, leads go cold.'
		},
		{
			title: 'Lost Revenue',
			description: 'Competitors with faster response times are stealing your customers.'
		},
		{
			title: 'No After-Hours Support',
			description: 'Your business sleeps, but your customers don\'t. Missing 60% of inquiries.'
		}
	];
</script>
