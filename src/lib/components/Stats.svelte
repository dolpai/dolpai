<section class="section-padding relative bg-gradient-to-br from-primary-950/20 via-transparent to-transparent">
	<!-- Background decoration -->
	<div class="absolute inset-0 opacity-30">
		<div class="absolute top-1/2 left-1/4 w-96 h-96 bg-primary-500 rounded-full blur-[150px]"></div>
		<div class="absolute bottom-1/4 right-1/4 w-96 h-96 bg-cyan-500 rounded-full blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<div class="grid grid-cols-2 lg:grid-cols-4 gap-12 lg:gap-16">
			{#each stats as stat, i}
				<div class="text-center space-y-3 group" style="animation-delay: {i * 100}ms">
					<div class="text-5xl sm:text-6xl lg:text-7xl font-bold gradient-text group-hover:scale-110 transition-transform duration-300">
						{stat.value}
					</div>
					<div class="text-sm sm:text-base text-gray-400 font-medium uppercase tracking-wider">
						{stat.label}
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<script>
	const stats = [
		{ value: '500+', label: 'Active Businesses' },
		{ value: '1M+', label: 'Messages Handled' },
		{ value: '<1s', label: 'Response Time' },
		{ value: '95%', label: 'Satisfaction Rate' }
	];
</script>
