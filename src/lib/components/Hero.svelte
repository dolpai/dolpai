<script>
	import { onMount } from 'svelte';

	let mounted = $state(false);
	let logoError = $state(false);
	let tick = $state(0);

	// Live-incrementing counters for the dashboard
	let convCount = $state(247);
	let leadsCount = $state(89);
	let apptsCount = $state(34);

	const liveMetrics = $derived([
		{ label: 'Active Conversations', value: String(convCount),  delta: '+12', color: 'text-cyan-400' },
		{ label: 'Leads Captured Today', value: String(leadsCount), delta: '+5',  color: 'text-green-400' },
		{ label: 'Appts Booked',         value: String(apptsCount), delta: '+2',  color: 'text-blue-400' },
	]);

	onMount(() => {
		setTimeout(() => { mounted = true; }, 80);

		// Cycle highlight
		const tickInterval = setInterval(() => { tick = (tick + 1) % 3; }, 2800);

		// Simulate live counter increments
		const counterInterval = setInterval(() => {
			const r = Math.random();
			if (r < 0.5)      convCount  += Math.floor(Math.random() * 3) + 1;
			else if (r < 0.8) leadsCount += 1;
			else              apptsCount += 1;
		}, 3500);

		return () => {
			clearInterval(tickInterval);
			clearInterval(counterInterval);
		};
	});

	function handleLogoError() { logoError = true; }
</script>

<section class="relative min-h-screen flex items-center justify-center overflow-hidden bg-[#030712]">

	<!-- Grid overlay -->
	<div class="absolute inset-0 grid-overlay pointer-events-none"></div>

	<!-- Radial glow -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[1000px] h-[1000px] rounded-full"
			style="background: radial-gradient(circle, rgba(6,182,212,0.10) 0%, rgba(37,99,235,0.07) 40%, transparent 70%);">
		</div>
	</div>

	<!-- Floating orbs -->
	<div class="absolute top-20 left-[8%] w-80 h-80 rounded-full bg-cyan-500/8 blur-[110px] animate-glow-pulse pointer-events-none"></div>
	<div class="absolute bottom-28 right-[6%] w-96 h-96 rounded-full bg-blue-600/8 blur-[130px] animate-glow-pulse pointer-events-none" style="animation-delay:1.5s"></div>

	<!-- Bottom fade -->
	<div class="absolute bottom-0 left-0 right-0 h-56 bg-gradient-to-t from-[#030712] to-transparent pointer-events-none"></div>

	<div class="section-container relative z-10 pt-28 pb-16 sm:pt-36 sm:pb-24">
		<div class="grid lg:grid-cols-2 gap-14 lg:gap-10 items-center">

			<!-- ── Left: Copy ── -->
			<div class="space-y-8 {mounted ? 'animate-fade-up' : 'opacity-0'}">

				<!-- Badge -->
				<div class="inline-flex items-center gap-2.5 px-4 py-2 rounded-full border border-cyan-500/20 bg-cyan-500/5 backdrop-blur-sm">
					<span class="relative flex h-2 w-2">
						<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-cyan-400 opacity-75"></span>
						<span class="relative inline-flex rounded-full h-2 w-2 bg-cyan-500"></span>
					</span>
					<span class="text-xs font-semibold tracking-widest uppercase text-cyan-400">AI Automation Platform</span>
				</div>

				<!-- Headline -->
				<div class="space-y-2">
					<h1 class="text-5xl sm:text-6xl lg:text-[64px] xl:text-7xl font-extrabold leading-[1.05] tracking-tight text-white">
						Never Miss a
					</h1>
					<h1 class="text-5xl sm:text-6xl lg:text-[64px] xl:text-7xl font-extrabold leading-[1.05] tracking-tight gradient-text">
						Customer Again
					</h1>
				</div>

				<p class="text-lg sm:text-xl text-gray-400 leading-relaxed max-w-lg font-light">
					Dolpai deploys intelligent AI agents that respond instantly, qualify leads, and book appointments — 24/7, across every channel.
				</p>

				<!-- CTAs -->
				<div class="flex flex-col sm:flex-row gap-3 pt-1">
					<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer"
						class="btn-primary text-base px-8 py-4 shadow-xl shadow-cyan-500/20">
						Get Free Demo
						<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
						</svg>
					</a>
					<a href="#demo" class="btn-secondary text-base px-8 py-4">
						Watch Demo
						<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z"/>
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
						</svg>
					</a>
				</div>

				<!-- Social proof -->
				<div class="flex items-center gap-5 pt-1">
					<div class="flex -space-x-2">
						{#each ['S','M','E','D','L'] as initial, i}
							<div class="w-8 h-8 rounded-full border-2 border-[#030712] bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center text-xs font-bold text-white" style="z-index:{5-i}">
								{initial}
							</div>
						{/each}
					</div>
					<div class="text-sm text-gray-400">
						<span class="text-white font-semibold">500+</span> businesses trust Dolpai
					</div>
				</div>
			</div>

			<!-- ── Right: AI Operations Dashboard ── -->
			<div class="relative {mounted ? 'animate-slide-right' : 'opacity-0'}" style="animation-delay:0.2s">

				<!-- Floating stat pill — top left -->
				<div class="absolute -top-5 -left-3 z-20 animate-float" style="animation-delay:0.4s">
					<div class="glass-card px-3.5 py-2.5 flex items-center gap-2.5 shadow-xl shadow-black/50">
						<div class="w-7 h-7 rounded-lg bg-green-500/20 flex items-center justify-center flex-shrink-0">
							<svg class="w-3.5 h-3.5 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"/>
							</svg>
						</div>
						<div>
							<div class="text-[10px] text-gray-500 leading-none mb-0.5">Conversions</div>
							<div class="text-sm font-bold text-white leading-none">+247% <span class="text-green-400 text-xs">↑</span></div>
						</div>
					</div>
				</div>

				<!-- Floating stat pill — bottom right -->
				<div class="absolute -bottom-4 -right-3 z-20 animate-float" style="animation-delay:1.3s">
					<div class="glass-card px-3.5 py-2.5 flex items-center gap-2.5 shadow-xl shadow-black/50">
						<div class="w-7 h-7 rounded-lg bg-cyan-500/20 flex items-center justify-center flex-shrink-0">
							<svg class="w-3.5 h-3.5 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
							</svg>
						</div>
						<div>
							<div class="text-[10px] text-gray-500 leading-none mb-0.5">Avg Response</div>
							<div class="text-sm font-bold text-white leading-none">&lt;0.8s</div>
						</div>
					</div>
				</div>

				<!-- Main dashboard card -->
				<div class="glass-card overflow-hidden shadow-2xl shadow-cyan-500/10 animate-border-glow">

					<!-- Dashboard top bar -->
					<div class="flex items-center justify-between px-4 py-3 border-b border-white/[0.07] bg-white/[0.02]">
						<div class="flex items-center gap-2">
							<div class="w-7 h-7 rounded-lg bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center">
								<svg class="w-3.5 h-3.5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17H3a2 2 0 01-2-2V5a2 2 0 012-2h14a2 2 0 012 2v3"/>
								</svg>
							</div>
							<span class="text-xs font-semibold text-white">Dolpai Operations</span>
						</div>
						<div class="flex items-center gap-3">
							<div class="flex items-center gap-1.5 text-[10px] text-green-400">
								<span class="w-1.5 h-1.5 bg-green-500 rounded-full animate-pulse"></span>
								All systems live
							</div>
							<div class="flex gap-1">
								<div class="w-2 h-2 rounded-full bg-red-500/50"></div>
								<div class="w-2 h-2 rounded-full bg-yellow-500/50"></div>
								<div class="w-2 h-2 rounded-full bg-green-500/50"></div>
							</div>
						</div>
					</div>

					<!-- Metric row -->
					<div class="grid grid-cols-3 divide-x divide-white/[0.05] border-b border-white/[0.07]">
						{#each liveMetrics as m, i}
							<div class="px-3 py-3 text-center transition-all duration-500 {tick === i ? 'bg-cyan-500/5' : ''}">
								<div class="text-base font-black {m.color}">{m.value}</div>
								<div class="text-[9px] text-gray-600 leading-tight mt-0.5">{m.label}</div>
								<div class="text-[9px] text-green-400 mt-0.5">{m.delta} today</div>
							</div>
						{/each}
					</div>

					<!-- Active conversations list -->
					<div class="px-4 pt-3 pb-1">
						<div class="flex items-center justify-between mb-2">
							<span class="text-[10px] font-semibold text-gray-500 uppercase tracking-wider">Active Conversations</span>
							<span class="text-[10px] text-cyan-400 font-medium">247 live</span>
						</div>
						<div class="space-y-2">
							{#each [
								{ name: 'Sarah K.',    channel: 'WhatsApp', msg: 'Interested in the Pro plan...', score: 92, tag: 'Hot Lead',    tagColor: 'bg-orange-500/20 text-orange-400', time: '0:12s' },
								{ name: 'Raj Patel',   channel: 'Instagram', msg: 'Can I book a demo for Friday?', score: 87, tag: 'Booking',    tagColor: 'bg-blue-500/20 text-blue-400',   time: '0:34s' },
								{ name: 'Emma Liu',    channel: 'Facebook', msg: 'What are your pricing plans?', score: 74, tag: 'Qualified',   tagColor: 'bg-cyan-500/20 text-cyan-400',   time: '1:05s' },
							] as conv}
								<div class="flex items-center gap-2.5 p-2 rounded-xl bg-white/[0.03] hover:bg-white/[0.05] transition-colors duration-200 group">
									<div class="w-7 h-7 rounded-full bg-gradient-to-br from-cyan-600 to-blue-700 flex items-center justify-center text-[10px] font-bold text-white flex-shrink-0">
										{conv.name.charAt(0)}
									</div>
									<div class="flex-1 min-w-0">
										<div class="flex items-center gap-1.5 mb-0.5">
											<span class="text-xs font-semibold text-white">{conv.name}</span>
											<span class="text-[9px] text-gray-600">· {conv.channel}</span>
										</div>
										<div class="text-[10px] text-gray-500 truncate">{conv.msg}</div>
									</div>
									<div class="flex flex-col items-end gap-1 flex-shrink-0">
										<span class="text-[9px] px-1.5 py-0.5 rounded-full font-semibold {conv.tagColor}">{conv.tag}</span>
										<span class="text-[9px] text-gray-600">{conv.time}</span>
									</div>
								</div>
							{/each}
						</div>
					</div>

					<!-- AI status bar -->
					<div class="px-4 py-3 mt-1 border-t border-white/[0.07] bg-white/[0.02] flex items-center justify-between">
						<div class="flex items-center gap-2">
							<div class="w-5 h-5 rounded-md bg-cyan-500/20 flex items-center justify-center">
								<svg class="w-3 h-3 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
									<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
								</svg>
							</div>
							<span class="text-[10px] text-gray-500">AI Confidence</span>
						</div>
						<div class="flex items-center gap-2">
							<div class="w-24 h-1.5 rounded-full bg-white/[0.06] overflow-hidden">
								<div class="h-full w-[94%] rounded-full bg-gradient-to-r from-cyan-500 to-blue-500"></div>
							</div>
							<span class="text-[10px] font-bold text-cyan-400">94%</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Scroll indicator -->
	<div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-1.5 animate-bounce opacity-30">
		<span class="text-[10px] text-gray-600 tracking-widest uppercase">Scroll</span>
		<svg class="w-4 h-4 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
			<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
		</svg>
	</div>
</section>
