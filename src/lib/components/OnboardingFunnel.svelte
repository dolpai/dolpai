<script>
	import { onMount } from 'svelte';

	let activeStep = $state(0);

	const steps = [
		{
			number: '01',
			title: 'Book Your Demo',
			subtitle: '15-minute call · No commitment',
			description: 'Talk to our team. We\'ll understand your business, show you a live walkthrough, and answer every question you have.',
			detail: 'We\'ll map your exact use case and show you what Dolpai looks like running inside your business — not a generic demo.',
			cta: 'Book Free Demo',
			ctaHref: 'https://wa.me/9779765244850',
			icon: 'M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z',
			color: 'from-cyan-500 to-blue-600',
			glow: 'rgba(6,182,212,0.15)',
			badge: 'Start here',
			badgeColor: 'bg-cyan-500/10 border-cyan-500/20 text-cyan-400'
		},
		{
			number: '02',
			title: 'Connect Your Channels',
			subtitle: 'One-click setup · 5 minutes',
			description: 'Link WhatsApp, Instagram, Facebook, or your website chat. Our guided setup walks you through every step.',
			detail: 'No API keys, no developer needed. If you can click a button, you can connect your channels.',
			cta: null,
			ctaHref: null,
			icon: 'M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1',
			color: 'from-blue-500 to-violet-600',
			glow: 'rgba(59,130,246,0.15)',
			badge: 'Day 1',
			badgeColor: 'bg-blue-500/10 border-blue-500/20 text-blue-400'
		},
		{
			number: '03',
			title: 'Train Your AI',
			subtitle: 'Upload once · Learns forever',
			description: 'Share your product catalog, FAQs, pricing, and brand guidelines. Dolpai learns your business in minutes and improves with every conversation.',
			detail: 'Most clients complete training in under 30 minutes. The AI handles edge cases by escalating to your team — with full context.',
			cta: null,
			ctaHref: null,
			icon: 'M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z',
			color: 'from-violet-500 to-purple-700',
			glow: 'rgba(139,92,246,0.15)',
			badge: 'Day 1',
			badgeColor: 'bg-violet-500/10 border-violet-500/20 text-violet-400'
		},
		{
			number: '04',
			title: 'Go Live',
			subtitle: 'Fully automated · From day one',
			description: 'Activate Dolpai and your AI agent starts handling conversations immediately. Monitor everything from your real-time dashboard.',
			detail: 'Average time from signup to first automated conversation: 47 minutes. Your team gets notified only when human judgment is needed.',
			cta: 'Start Today',
			ctaHref: '#contact',
			icon: 'M5 3l14 9-14 9V3z',
			color: 'from-green-500 to-cyan-600',
			glow: 'rgba(34,197,94,0.15)',
			badge: 'Go live',
			badgeColor: 'bg-green-500/10 border-green-500/20 text-green-400'
		}
	];

	onMount(() => {
		const interval = setInterval(() => {
			activeStep = (activeStep + 1) % steps.length;
		}, 3000);
		return () => clearInterval(interval);
	});
</script>

<section id="onboarding" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 right-0 w-96 h-96 rounded-full bg-cyan-500/4 blur-[130px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Getting Started</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				From Demo to <span class="gradient-text">Live in a Day</span>
			</h2>
			<p class="text-lg text-gray-500">
				No lengthy onboarding. No technical complexity. Most businesses are fully automated within 24 hours of their first call.
			</p>
		</div>

		<div class="grid lg:grid-cols-2 gap-10 lg:gap-14 items-start max-w-5xl mx-auto">

			<!-- Left: Step list -->
			<div class="space-y-3">
				{#each steps as step, i}
					<button
						onclick={() => activeStep = i}
						class="w-full text-left group relative rounded-2xl border transition-all duration-300 overflow-hidden
							{activeStep === i
								? 'border-white/[0.15] bg-white/[0.05]'
								: 'border-white/[0.05] bg-white/[0.01] hover:border-white/[0.10] hover:bg-white/[0.03]'}"
					>
						{#if activeStep === i}
							<div class="absolute inset-0 pointer-events-none"
								style="background: radial-gradient(circle at 0% 50%, {step.glow} 0%, transparent 60%);">
							</div>
						{/if}

						<div class="relative flex items-start gap-4 px-5 py-4">
							<!-- Step icon -->
							<div class="flex-shrink-0 w-10 h-10 rounded-xl bg-gradient-to-br {step.color} flex items-center justify-center shadow-lg transition-all duration-300 {activeStep === i ? 'scale-110' : 'opacity-50'}">
								<svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={step.icon}/>
								</svg>
							</div>

							<div class="flex-1 min-w-0">
								<div class="flex items-center gap-2 mb-0.5">
									<span class="text-sm font-bold {activeStep === i ? 'text-white' : 'text-gray-400'} transition-colors duration-200">{step.title}</span>
									<span class="text-[9px] px-2 py-0.5 rounded-full border font-semibold {step.badgeColor}">{step.badge}</span>
								</div>
								<div class="text-xs text-gray-600">{step.subtitle}</div>
								{#if activeStep === i}
									<p class="text-sm text-gray-400 leading-relaxed mt-2 animate-in fade-in duration-300">{step.description}</p>
								{/if}
							</div>

							<div class="flex-shrink-0 text-lg font-black {activeStep === i ? 'gradient-text' : 'text-gray-700'} transition-colors duration-200">
								{step.number}
							</div>
						</div>
					</button>
				{/each}
			</div>

			<!-- Right: Active step detail -->
			<div class="lg:sticky lg:top-24">
				{#each steps as step, i}
					{#if activeStep === i}
						<div class="animate-in fade-in duration-300">
							<div class="relative rounded-2xl border border-white/[0.08] bg-white/[0.03] overflow-hidden">
								<!-- Top accent -->
								<div class="h-1 bg-gradient-to-r {step.color}"></div>

								<div class="p-7 space-y-6">
									<!-- Step header -->
									<div class="flex items-center gap-4">
										<div class="w-14 h-14 rounded-2xl bg-gradient-to-br {step.color} flex items-center justify-center shadow-xl flex-shrink-0">
											<svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={step.icon}/>
											</svg>
										</div>
										<div>
											<div class="text-xs text-gray-500 mb-0.5">{step.number} of 04</div>
											<h3 class="text-xl font-bold text-white">{step.title}</h3>
											<div class="text-xs text-gray-500 mt-0.5">{step.subtitle}</div>
										</div>
									</div>

									<!-- Detail text -->
									<div class="rounded-xl border border-white/[0.06] bg-white/[0.03] p-4">
										<p class="text-sm text-gray-300 leading-relaxed">{step.detail}</p>
									</div>

									<!-- Progress indicator -->
									<div class="space-y-2">
										<div class="flex justify-between text-xs text-gray-600">
											<span>Progress</span>
											<span>Step {i + 1} of {steps.length}</span>
										</div>
										<div class="h-1.5 rounded-full bg-white/[0.06] overflow-hidden">
											<div class="h-full rounded-full bg-gradient-to-r {step.color} transition-all duration-500"
												style="width: {((i + 1) / steps.length) * 100}%">
											</div>
										</div>
									</div>

									{#if step.cta}
										<a
											href={step.ctaHref}
											target={step.ctaHref?.startsWith('http') ? '_blank' : undefined}
											rel={step.ctaHref?.startsWith('http') ? 'noopener noreferrer' : undefined}
											class="btn-primary w-full justify-center"
										>
											{step.cta}
											<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
											</svg>
										</a>
									{/if}
								</div>
							</div>

							<!-- Time estimate -->
							<div class="mt-4 text-center text-xs text-gray-600">
								⏱ Average time to complete this step: {i === 0 ? '15 minutes' : i === 1 ? '5 minutes' : i === 2 ? '30 minutes' : '2 minutes'}
							</div>
						</div>
					{/if}
				{/each}
			</div>
		</div>
	</div>
</section>
