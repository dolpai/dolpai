<script>
	const pillars = [
		{
			title: '99.9% Uptime SLA',
			description: 'Dolpai runs on redundant cloud infrastructure. Your AI agent stays online even when everything else doesn\'t.',
			icon: 'M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z',
			color: 'cyan',
			stat: '99.9%',
			statLabel: 'Uptime guarantee'
		},
		{
			title: 'End-to-End Encryption',
			description: 'Every conversation is encrypted in transit and at rest. Your customer data never leaves your control.',
			icon: 'M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z',
			color: 'blue',
			stat: 'AES-256',
			statLabel: 'Encryption standard'
		},
		{
			title: 'Onboarding in 10 Minutes',
			description: 'Connect your channels, upload your business info, and go live. No engineers, no waiting, no friction.',
			icon: 'M13 10V3L4 14h7v7l9-11h-7z',
			color: 'violet',
			stat: '<10 min',
			statLabel: 'Average setup time'
		},
		{
			title: 'Scales With Your Business',
			description: 'From 100 to 100,000 conversations per month — the infrastructure scales automatically. No plan upgrades needed mid-campaign.',
			icon: 'M7 12l3-3 3 3 4-4M8 21l4-4 4 4M3 4h18M4 4h16v12a1 1 0 01-1 1H5a1 1 0 01-1-1V4z',
			color: 'cyan',
			stat: '∞',
			statLabel: 'Conversation capacity'
		},
		{
			title: 'GDPR & Data Compliance',
			description: 'Built with privacy by design. Compliant with GDPR, CCPA, and regional data protection laws out of the box.',
			icon: 'M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2',
			color: 'blue',
			stat: 'GDPR',
			statLabel: 'Compliant by default'
		},
		{
			title: '24/7 Human Support',
			description: 'Our team is available around the clock. If something needs attention, a real person responds — not another bot.',
			icon: 'M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.192l-3.536 3.536M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-5 0a4 4 0 11-8 0 4 4 0 018 0z',
			color: 'violet',
			stat: '24/7',
			statLabel: 'Human support'
		}
	];

	const colorMap = {
		cyan:   { bg: 'bg-cyan-500/10',   border: 'border-cyan-500/20',   icon: 'text-cyan-400',   stat: 'from-cyan-400 to-cyan-300' },
		blue:   { bg: 'bg-blue-500/10',   border: 'border-blue-500/20',   icon: 'text-blue-400',   stat: 'from-blue-400 to-blue-300' },
		violet: { bg: 'bg-violet-500/10', border: 'border-violet-500/20', icon: 'text-violet-400', stat: 'from-violet-400 to-violet-300' }
	};
</script>

<section id="trust" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[700px] h-[700px] rounded-full bg-blue-600/4 blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Infrastructure</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Built to Be <span class="gradient-text">Trusted</span>
			</h2>
			<p class="text-lg text-gray-500">
				Reliability isn't a feature — it's the foundation. Dolpai is engineered for businesses that can't afford downtime.
			</p>
		</div>

		<!-- Uptime banner -->
		<div class="max-w-4xl mx-auto mb-12">
			<div class="relative rounded-2xl border border-cyan-500/15 bg-gradient-to-r from-cyan-500/5 via-blue-600/5 to-cyan-500/5 p-6 overflow-hidden">
				<div class="absolute inset-0 grid-overlay opacity-20 pointer-events-none"></div>
				<div class="relative flex flex-col sm:flex-row items-center justify-between gap-6">
					<div class="flex items-center gap-4">
						<div class="w-3 h-3 rounded-full bg-green-500 animate-pulse shadow-lg shadow-green-500/50"></div>
						<div>
							<div class="text-white font-semibold text-sm">All Systems Operational</div>
							<div class="text-xs text-gray-500 mt-0.5">AI agents · API · Dashboard · Integrations</div>
						</div>
					</div>
					<!-- Uptime bars -->
					<div class="flex items-center gap-1">
						{#each Array(30) as _, i}
							<div class="w-1.5 h-6 rounded-sm {i === 14 ? 'bg-yellow-500/60' : 'bg-green-500/70'} hover:opacity-100 transition-opacity"></div>
						{/each}
					</div>
					<div class="text-right">
						<div class="text-2xl font-black gradient-text">99.97%</div>
						<div class="text-xs text-gray-500">Last 90 days</div>
					</div>
				</div>
			</div>
		</div>

		<!-- Pillars grid -->
		<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-5 max-w-6xl mx-auto">
			{#each pillars as pillar}
				{@const c = colorMap[pillar.color]}
				<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 sm:p-7 hover:border-white/[0.12] hover:bg-white/[0.04] transition-all duration-300 overflow-hidden">
					<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
						style="background: radial-gradient(circle at 0% 0%, rgba(6,182,212,0.05) 0%, transparent 60%);">
					</div>
					<div class="relative space-y-4">
						<div class="flex items-start justify-between">
							<div class="w-11 h-11 rounded-xl {c.bg} border {c.border} flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
								<svg class="w-5 h-5 {c.icon}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={pillar.icon}/>
								</svg>
							</div>
							<div class="text-right">
								<div class="text-lg font-black bg-gradient-to-r {c.stat} bg-clip-text text-transparent">{pillar.stat}</div>
								<div class="text-[10px] text-gray-600">{pillar.statLabel}</div>
							</div>
						</div>
						<div>
							<h3 class="font-semibold text-white mb-2 group-hover:text-cyan-300 transition-colors duration-200">{pillar.title}</h3>
							<p class="text-sm text-gray-500 leading-relaxed">{pillar.description}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
