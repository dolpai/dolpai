<script>
	const plans = [
		{
			name: 'Starter',
			description: 'For small businesses ready to stop missing leads.',
			price: '49',
			popular: false,
			cta: 'Start Free Trial',
			features: [
				'1,000 conversations/month',
				'2 messaging channels',
				'AI trained on your business',
				'Appointment booking',
				'Analytics dashboard',
				'Email support'
			]
		},
		{
			name: 'Professional',
			description: 'For growing teams that need full automation power.',
			price: '149',
			popular: true,
			cta: 'Start Free Trial',
			features: [
				'10,000 conversations/month',
				'Unlimited channels',
				'Advanced AI training',
				'Lead scoring & qualification',
				'CRM sync & integrations',
				'Team collaboration tools',
				'API access',
				'Priority support 24/7'
			]
		},
		{
			name: 'Business',
			description: 'For established companies with high-volume needs.',
			price: '299',
			popular: false,
			cta: 'Start Free Trial',
			features: [
				'Unlimited conversations',
				'Unlimited channels',
				'Custom AI workflows',
				'Dedicated account manager',
				'White-label options',
				'Advanced security & compliance',
				'Custom reporting',
				'Priority onboarding call'
			]
		}
	];
</script>

<section id="pricing" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] rounded-full bg-blue-600/4 blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Pricing</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Simple, <span class="gradient-text">Transparent</span> Pricing
			</h2>
			<p class="text-lg text-gray-500">
				No hidden fees. No surprises. Cancel anytime.
			</p>
		</div>

		<!-- Plans grid -->
		<div class="grid md:grid-cols-3 gap-5 max-w-5xl mx-auto">
			{#each plans as plan, i}
				<div class="relative group rounded-2xl border transition-all duration-300 overflow-hidden flex flex-col
					{plan.popular
						? 'border-cyan-500/40 bg-gradient-to-b from-cyan-500/[0.08] to-blue-600/[0.05] shadow-xl shadow-cyan-500/10'
						: 'border-white/[0.06] bg-white/[0.02] hover:border-white/[0.12] hover:bg-white/[0.04]'}">

					{#if plan.popular}
						<!-- Popular badge -->
						<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-cyan-500/60 to-transparent"></div>
						<div class="absolute -top-px left-1/2 -translate-x-1/2">
							<div class="px-4 py-1 bg-gradient-to-r from-cyan-500 to-blue-600 text-white text-xs font-bold tracking-wider uppercase rounded-b-lg shadow-lg shadow-cyan-500/30">
								Most Popular
							</div>
						</div>
					{/if}

					<div class="p-7 flex flex-col flex-1 {plan.popular ? 'pt-10' : ''}">
						<!-- Plan info -->
						<div class="space-y-2 mb-6">
							<h3 class="text-xl font-bold text-white">{plan.name}</h3>
							<p class="text-sm text-gray-500 leading-relaxed">{plan.description}</p>
						</div>

						<!-- Price -->
						<div class="flex items-baseline gap-1.5 mb-8">
							<span class="text-5xl font-black gradient-text">${plan.price}</span>
							<span class="text-gray-500 text-sm">/month</span>
						</div>

						<!-- Features -->
						<ul class="space-y-3 flex-1 mb-8">
							{#each plan.features as feature}
								<li class="flex items-start gap-3">
									<div class="flex-shrink-0 w-4 h-4 rounded-full bg-cyan-500/20 border border-cyan-500/30 flex items-center justify-center mt-0.5">
										<svg class="w-2.5 h-2.5 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
											<path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
										</svg>
									</div>
									<span class="text-sm text-gray-400">{feature}</span>
								</li>
							{/each}
						</ul>

						<!-- CTA -->
						<a
							href="https://wa.me/9779765244850?text=I'm interested in the {plan.name} plan"
							target="_blank"
							rel="noopener noreferrer"
							class="{plan.popular ? 'btn-primary' : 'btn-secondary'} w-full justify-center"
						>
							{plan.cta}
						</a>
					</div>
				</div>
			{/each}
		</div>

		<!-- Enterprise -->
		<div class="mt-8 max-w-5xl mx-auto">
			<div class="rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 sm:p-8">
				<div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-5">
					<div class="space-y-1">
						<div class="flex items-center gap-3">
							<h3 class="text-xl font-bold text-white">Enterprise</h3>
							<span class="px-2.5 py-0.5 rounded-full text-xs font-semibold bg-white/5 border border-white/10 text-gray-400">Custom</span>
						</div>
						<p class="text-sm text-gray-500">Custom solutions for large organizations with advanced security, compliance, and scale requirements.</p>
					</div>
					<a
						href="https://wa.me/9779765244850?text=I'm interested in Enterprise plan"
						target="_blank"
						rel="noopener noreferrer"
						class="btn-secondary whitespace-nowrap flex-shrink-0"
					>
						Contact Sales
					</a>
				</div>
			</div>
		</div>

		<!-- Guarantee -->
		<div class="mt-10 text-center space-y-3">
			<p class="text-sm text-gray-600">
				🔒 14-day free trial on all plans · No credit card required · Cancel anytime
			</p>
			<p class="text-xs text-gray-700">
				All plans include onboarding support, AI training assistance, and access to our help center.
			</p>
		</div>
	</div>
</section>
