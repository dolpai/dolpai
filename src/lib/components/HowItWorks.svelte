<section id="how-it-works" class="section-padding">
	<div class="section-container">
		<div class="text-center space-y-4 mb-12 sm:mb-16">
			<h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold">
				How It Works
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				Get started in minutes, not months
			</p>
		</div>

		<div class="max-w-5xl mx-auto">
			<!-- Desktop: Horizontal Layout -->
			<div class="hidden lg:flex items-center justify-between relative">
				<!-- Connection Line -->
				<div class="absolute top-1/2 left-0 right-0 h-0.5 bg-gradient-to-r from-primary-500 via-cyan-500 to-primary-500 -translate-y-1/2 -z-10"></div>

				{#each steps as step, i}
					<div class="flex-1 text-center">
						<div class="inline-flex flex-col items-center space-y-4">
							<div class="w-16 h-16 rounded-full bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center text-2xl font-bold text-white shadow-lg shadow-primary-500/30">
								{i + 1}
							</div>
							<div class="space-y-2">
								<h3 class="text-xl font-semibold">{step.title}</h3>
								<p class="text-gray-400 text-sm max-w-xs">{step.description}</p>
							</div>
						</div>
					</div>
				{/each}
			</div>

			<!-- Mobile/Tablet: Vertical Layout -->
			<div class="lg:hidden space-y-8">
				{#each steps as step, i}
					<div class="flex items-start space-x-4">
						<div class="flex-shrink-0 w-12 h-12 rounded-full bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center text-xl font-bold text-white shadow-lg shadow-primary-500/30">
							{i + 1}
						</div>
						<div class="flex-1 pt-2 space-y-2">
							<h3 class="text-lg sm:text-xl font-semibold">{step.title}</h3>
							<p class="text-gray-400">{step.description}</p>
						</div>
					</div>
					{#if i < steps.length - 1}
						<div class="ml-6 h-8 w-0.5 bg-gradient-to-b from-primary-500 to-cyan-500"></div>
					{/if}
				{/each}
			</div>
		</div>
	</div>
</section>

<script>
	const steps = [
		{
			title: 'Connect',
			description: 'Link your messaging channels in one click. WhatsApp, Facebook, Instagram, and more.'
		},
		{
			title: 'Train',
			description: 'Teach the AI about your business, products, and brand voice in minutes.'
		},
		{
			title: 'Automate',
			description: 'Let Dolpai handle conversations 24/7 while you focus on growing your business.'
		}
	];
</script>
