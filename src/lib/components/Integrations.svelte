<script>
	const integrations = [
		{
			name: 'WhatsApp',
			desc: 'Respond to WhatsApp messages instantly',
			color: 'from-green-500 to-green-600',
			glow: 'rgba(34,197,94,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 text-white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z"/></svg>`
		},
		{
			name: 'Instagram',
			desc: 'Auto-reply to DMs and story mentions',
			color: 'from-pink-500 to-purple-600',
			glow: 'rgba(236,72,153,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 text-white"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>`
		},
		{
			name: 'Facebook',
			desc: 'Handle Messenger conversations at scale',
			color: 'from-blue-500 to-blue-700',
			glow: 'rgba(59,130,246,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 text-white"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>`
		},
		{
			name: 'Telegram',
			desc: 'Automate Telegram bot conversations',
			color: 'from-sky-400 to-sky-600',
			glow: 'rgba(56,189,248,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6 text-white"><path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/></svg>`
		},
		{
			name: 'Website Chat',
			desc: 'Embed AI chat on any website in minutes',
			color: 'from-cyan-500 to-blue-600',
			glow: 'rgba(6,182,212,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" class="w-6 h-6 text-white"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/></svg>`
		},
		{
			name: 'CRM Systems',
			desc: 'Sync leads and data to your CRM automatically',
			color: 'from-violet-500 to-purple-700',
			glow: 'rgba(139,92,246,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" class="w-6 h-6 text-white"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4"/></svg>`
		},
		{
			name: 'Google Calendar',
			desc: 'Book appointments directly into your calendar',
			color: 'from-red-500 to-orange-500',
			glow: 'rgba(239,68,68,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" class="w-6 h-6 text-white"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>`
		},
		{
			name: 'Email / SMTP',
			desc: 'Send automated follow-ups and confirmations',
			color: 'from-amber-500 to-yellow-600',
			glow: 'rgba(245,158,11,0.15)',
			icon: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" class="w-6 h-6 text-white"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>`
		}
	];
</script>

<section id="integrations" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[700px] h-[700px] rounded-full bg-blue-600/4 blur-[150px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Integrations</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Connect Every <span class="gradient-text">Channel</span>
			</h2>
			<p class="text-lg text-gray-500">
				One AI brain. Every platform your customers use. All conversations in one unified dashboard.
			</p>
		</div>

		<!-- Central hub visual -->
		<div class="relative max-w-4xl mx-auto mb-16">
			<!-- Hub center -->
			<div class="flex justify-center mb-10">
				<div class="relative">
					<!-- Outer ring -->
					<div class="absolute inset-0 rounded-2xl border border-cyan-500/20 animate-border-glow scale-110"></div>
					<!-- Glow -->
					<div class="absolute inset-0 rounded-2xl bg-cyan-500/10 blur-xl scale-125 pointer-events-none"></div>
					<div class="relative w-20 h-20 rounded-2xl bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center shadow-2xl shadow-cyan-500/30">
						<svg class="w-9 h-9 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17H3a2 2 0 01-2-2V5a2 2 0 012-2h14a2 2 0 012 2v3"/>
						</svg>
					</div>
					<div class="absolute -bottom-6 left-1/2 -translate-x-1/2 whitespace-nowrap text-xs font-bold text-cyan-400 tracking-wider">DOLPAI AI</div>
				</div>
			</div>

			<!-- Integration cards grid -->
			<div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
				{#each integrations as integration, i}
					<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-4 hover:border-white/[0.14] transition-all duration-300 overflow-hidden cursor-default text-center"
						style="animation-delay: {i * 60}ms">
						<!-- Hover glow -->
						<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-400 pointer-events-none rounded-2xl"
							style="background: radial-gradient(circle at 50% 50%, {integration.glow} 0%, transparent 70%);">
						</div>

						<div class="relative space-y-3">
							<div class="w-11 h-11 rounded-xl bg-gradient-to-br {integration.color} flex items-center justify-center mx-auto shadow-lg group-hover:scale-110 transition-transform duration-300">
								{@html integration.icon}
							</div>
							<div>
								<div class="text-sm font-semibold text-white">{integration.name}</div>
								<div class="text-[11px] text-gray-600 mt-0.5 leading-tight">{integration.desc}</div>
							</div>
							<!-- Connected badge -->
							<div class="inline-flex items-center gap-1 px-2 py-0.5 rounded-full bg-green-500/10 border border-green-500/20">
								<span class="w-1 h-1 rounded-full bg-green-500"></span>
								<span class="text-[9px] text-green-400 font-semibold">Connected</span>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Bottom stat bar -->
		<div class="max-w-3xl mx-auto grid grid-cols-3 gap-4">
			{#each [
				{ value: '8+',    label: 'Platforms Supported' },
				{ value: '1-click', label: 'Setup Process' },
				{ value: '100%',  label: 'Sync Reliability' }
			] as stat}
				<div class="text-center rounded-2xl border border-white/[0.06] bg-white/[0.02] py-5 px-4">
					<div class="text-2xl font-black gradient-text">{stat.value}</div>
					<div class="text-xs text-gray-500 mt-1">{stat.label}</div>
				</div>
			{/each}
		</div>
	</div>
</section>
