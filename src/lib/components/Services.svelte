<section id="services" class="section-padding relative">
	<div class="absolute inset-0 section-overlay"></div>
	
	<div class="section-container relative z-10">
		<div class="text-center space-y-4 mb-16">
			<h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold">
				Everything You <span class="gradient-text">Need</span>
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				Powerful features to automate customer interactions
			</p>
		</div>

		<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
			{#each services as service, i}
				<div class="card group cursor-pointer" style="animation-delay: {i * 100}ms">
					<div class="w-14 h-14 rounded-xl bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center mb-6 group-hover:scale-110 group-hover:rotate-3 transition-all duration-300 shadow-lg shadow-primary-500/30">
						{@html service.icon}
					</div>
					<h3 class="text-xl font-semibold mb-3 group-hover:text-primary-400 transition-colors">{service.title}</h3>
					<p class="text-gray-400 leading-relaxed">{service.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<script>
	const services = [
		{
			title: 'Instant Responses',
			description: 'Reply to customer inquiries in under 1 second, any time of day or night.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" /></svg>'
		},
		{
			title: 'Lead Qualification',
			description: 'Automatically qualify leads and route them to the right team member.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" /></svg>'
		},
		{
			title: 'Appointment Booking',
			description: 'Let customers book meetings directly through chat, synced with your calendar.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" /></svg>'
		},
		{
			title: 'Multi-Channel Support',
			description: 'Connect WhatsApp, Facebook, Instagram, and your website in one place.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" /></svg>'
		},
		{
			title: 'Smart Analytics',
			description: 'Track conversations, response times, and conversion rates in real-time.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" /></svg>'
		},
		{
			title: 'Custom Training',
			description: 'Train the AI on your business, products, and brand voice for perfect responses.',
			icon: '<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" /></svg>'
		}
	];
</script>
