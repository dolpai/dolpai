<section id="pricing" class="section-padding">
	<div class="section-container">
		<div class="text-center space-y-4 mb-12 sm:mb-16">
			<h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold">
				Simple, Transparent Pricing
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				Choose the plan that fits your business needs
			</p>
		</div>

		<div class="grid md:grid-cols-3 gap-6 lg:gap-8 max-w-6xl mx-auto">
			{#each plans as plan, i}
				<div class="card relative group {plan.popular ? 'border-primary-500/50 shadow-xl shadow-primary-500/20' : ''}" style="animation-delay: {i * 100}ms">
					{#if plan.popular}
						<div class="absolute -top-4 left-1/2 -translate-x-1/2 px-4 py-1 bg-gradient-to-r from-primary-600 to-cyan-500 text-white text-sm font-semibold rounded-full">
							Most Popular
						</div>
					{/if}

					<div class="space-y-6">
						<!-- Plan Name -->
						<div>
							<h3 class="text-2xl font-bold text-white">{plan.name}</h3>
							<p class="text-gray-400 mt-2">{plan.description}</p>
						</div>

						<!-- Price -->
						<div class="flex items-baseline space-x-2">
							<span class="text-4xl sm:text-5xl font-bold gradient-text">${plan.price}</span>
							<span class="text-gray-400">/month</span>
						</div>

						<!-- Features -->
						<ul class="space-y-3">
							{#each plan.features as feature}
								<li class="flex items-start space-x-3">
									<svg class="w-5 h-5 text-primary-500 flex-shrink-0 mt-0.5" fill="currentColor" viewBox="0 0 20 20">
										<path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
									</svg>
									<span class="text-gray-300">{feature}</span>
								</li>
							{/each}
						</ul>

						<!-- CTA Button -->
						<a 
							href="https://wa.me/9779765244850?text=I'm interested in the {plan.name} plan" 
							target="_blank" 
							rel="noopener noreferrer"
							class="{plan.popular ? 'btn-primary' : 'btn-secondary'} w-full text-center block"
						>
							Get Started
						</a>
					</div>
				</div>
			{/each}
		</div>

		<!-- Enterprise -->
		<div class="mt-12 text-center">
			<div class="card max-w-2xl mx-auto">
				<div class="flex flex-col sm:flex-row items-center justify-between space-y-4 sm:space-y-0 sm:space-x-6">
					<div class="text-left flex-1">
						<h3 class="text-2xl font-bold text-white mb-2">Enterprise</h3>
						<p class="text-gray-400">Custom solutions for large organizations with advanced needs</p>
					</div>
					<a href="https://wa.me/9779765244850?text=I'm interested in Enterprise plan" target="_blank" rel="noopener noreferrer" class="btn-primary whitespace-nowrap">
						Contact Sales
					</a>
				</div>
			</div>
		</div>
	</div>
</section>

<script>
	const plans = [
		{
			name: 'Starter',
			description: 'Perfect for small businesses',
			price: '49',
			popular: false,
			features: [
				'Up to 1,000 conversations/month',
				'2 messaging channels',
				'Basic AI training',
				'Email support',
				'Analytics dashboard',
				'Mobile app access'
			]
		},
		{
			name: 'Professional',
			description: 'For growing businesses',
			price: '149',
			popular: true,
			features: [
				'Up to 10,000 conversations/month',
				'Unlimited messaging channels',
				'Advanced AI training',
				'Priority support 24/7',
				'Advanced analytics',
				'Custom integrations',
				'Team collaboration',
				'API access'
			]
		},
		{
			name: 'Business',
			description: 'For established companies',
			price: '299',
			popular: false,
			features: [
				'Unlimited conversations',
				'Unlimited channels',
				'Premium AI features',
				'Dedicated account manager',
				'White-label options',
				'Advanced security',
				'Custom workflows',
				'Priority onboarding'
			]
		}
	];
</script>
