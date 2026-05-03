<section class="section-padding relative">
	<div class="absolute inset-0 section-overlay"></div>
	
	<div class="section-container relative z-10">
		<div class="max-w-4xl mx-auto">
			<div class="card text-center space-y-8">
				<div class="inline-flex items-center justify-center w-20 h-20 rounded-2xl bg-gradient-to-br from-primary-500 to-cyan-500 mx-auto shadow-lg shadow-primary-500/50">
					<svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
					</svg>
				</div>

				<h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold">
					Meet Your <span class="gradient-text">AI Assistant</span>
				</h2>

				<p class="text-lg sm:text-xl text-gray-300 leading-relaxed max-w-2xl mx-auto">
					Dolpai handles customer conversations automatically—responding instantly, qualifying leads, and booking appointments while learning from every interaction.
				</p>

				<div class="grid sm:grid-cols-3 gap-8 pt-8">
					{#each features as feature}
						<div class="space-y-3">
							<div class="text-4xl sm:text-5xl font-bold gradient-text">{feature.stat}</div>
							<div class="text-sm text-gray-400 uppercase tracking-wider">{feature.label}</div>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</div>
</section>

<script>
	const features = [
		{ stat: '<1s', label: 'Response Time' },
		{ stat: '24/7', label: 'Always Available' },
		{ stat: '95%', label: 'Customer Satisfaction' }
	];
</script>
