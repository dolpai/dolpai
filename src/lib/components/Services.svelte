<script>
	const services = [
		{
			title: 'Instant Responses',
			description: 'Reply to every customer inquiry in under 1 second, any time of day or night. Zero wait time.',
			icon: 'M13 10V3L4 14h7v7l9-11h-7z',
			color: 'cyan'
		},
		{
			title: 'Lead Qualification',
			description: 'Automatically score and qualify leads, then route them to the right team member at the right time.',
			icon: 'M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z',
			color: 'blue'
		},
		{
			title: 'Appointment Booking',
			description: 'Let customers book meetings directly through chat, synced with your calendar in real time.',
			icon: 'M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z',
			color: 'violet'
		},
		{
			title: 'Multi-Channel Support',
			description: 'Connect WhatsApp, Facebook, Instagram, and your website. One AI, every channel, unified inbox.',
			icon: 'M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z',
			color: 'cyan'
		},
		{
			title: 'Smart Analytics',
			description: 'Track conversations, response times, and conversion rates. Make data-driven decisions in real time.',
			icon: 'M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z',
			color: 'blue'
		},
		{
			title: 'Custom AI Training',
			description: 'Train the AI on your business, products, and brand voice. It gets smarter with every conversation.',
			icon: 'M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253',
			color: 'violet'
		}
	];

	const colorMap = {
		cyan:   { bg: 'bg-cyan-500/10',   border: 'border-cyan-500/20',   icon: 'text-cyan-400',   glow: 'rgba(6,182,212,0.08)' },
		blue:   { bg: 'bg-blue-500/10',   border: 'border-blue-500/20',   icon: 'text-blue-400',   glow: 'rgba(59,130,246,0.08)' },
		violet: { bg: 'bg-violet-500/10', border: 'border-violet-500/20', icon: 'text-violet-400', glow: 'rgba(139,92,246,0.08)' }
	};
</script>

<section id="services" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute bottom-0 left-1/3 w-96 h-96 rounded-full bg-blue-600/5 blur-[120px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Features</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Everything You <span class="gradient-text">Need</span>
			</h2>
			<p class="text-lg text-gray-500">
				Powerful AI features to automate customer interactions and grow your business.
			</p>
		</div>

		<!-- Cards grid -->
		<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-5">
			{#each services as service, i}
				{@const c = colorMap[service.color]}
				<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 sm:p-7 hover:border-white/[0.12] hover:bg-white/[0.04] transition-all duration-300 overflow-hidden cursor-default">
					<!-- Hover glow -->
					<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
						style="background: radial-gradient(circle at 0% 0%, {c.glow} 0%, transparent 60%);">
					</div>

					<!-- Top accent line -->
					<div class="absolute top-0 left-6 right-6 h-px bg-gradient-to-r from-transparent via-white/10 to-transparent group-hover:via-cyan-500/30 transition-all duration-300"></div>

					<div class="relative space-y-4">
						<div class="w-11 h-11 rounded-xl {c.bg} border {c.border} flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
							<svg class="w-5 h-5 {c.icon}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={service.icon} />
							</svg>
						</div>
						<div>
							<h3 class="font-semibold text-white mb-2 group-hover:text-cyan-300 transition-colors duration-200">{service.title}</h3>
							<p class="text-sm text-gray-500 leading-relaxed">{service.description}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
