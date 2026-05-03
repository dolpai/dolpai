<section id="benefits" class="section-padding bg-dark-900/50">
	<div class="section-container">
		<div class="text-center space-y-4 mb-12 sm:mb-16">
			<h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold">
				Why Choose Dolpai
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				Built for modern businesses that value speed and efficiency
			</p>
		</div>

		<div class="grid sm:grid-cols-2 gap-6 lg:gap-8 max-w-5xl mx-auto">
			{#each benefits as benefit, i}
				<div class="card flex items-start space-x-4 group" style="animation-delay: {i * 100}ms">
					<div class="flex-shrink-0 w-12 h-12 rounded-lg bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center group-hover:scale-110 group-hover:rotate-6 transition-all duration-300 shadow-lg shadow-primary-500/20">
						{@html benefit.icon}
					</div>
					<div class="flex-1 space-y-2">
						<h3 class="text-xl font-semibold group-hover:text-primary-400 transition-colors">{benefit.title}</h3>
						<p class="text-gray-400">{benefit.description}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<script>
	const benefits = [
		{
			title: '10x Faster Response',
			description: 'Reply to customers in under 1 second, not hours. Never lose a lead to slow response times.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" /></svg>'
		},
		{
			title: 'Save 20+ Hours/Week',
			description: 'Automate repetitive conversations and let your team focus on high-value tasks.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>'
		},
		{
			title: '3x More Conversions',
			description: 'Instant responses and smart follow-ups turn more leads into paying customers.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6" /></svg>'
		},
		{
			title: 'Zero Training Required',
			description: 'Set up in minutes with our intuitive interface. No technical skills needed.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>'
		},
		{
			title: 'Works While You Sleep',
			description: '24/7 availability means you never miss an opportunity, even at 3 AM.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" /></svg>'
		},
		{
			title: 'Scales Infinitely',
			description: 'Handle 10 or 10,000 conversations simultaneously without hiring more staff.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 12l3-3 3 3 4-4M8 21l4-4 4 4M3 4h18M4 4h16v12a1 1 0 01-1 1H5a1 1 0 01-1-1V4z" /></svg>'
		}
	];
</script>
