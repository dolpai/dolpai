<script>
	import { onMount } from 'svelte';

	let activeStep = $state(0);
	let paused = $state(false);
	/** @type {ReturnType<typeof setInterval>|null} */
	let interval = null;

	const steps = [
		{
			id: 'message',
			label: 'Customer Message',
			sublabel: 'Incoming via WhatsApp',
			icon: 'M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z',
			color: 'from-green-500 to-green-600',
			glow: 'rgba(34,197,94,0.18)',
			detail: '"Hi, I need to book a consultation for next week"',
			detailColor: 'text-green-300',
			badge: 'Received',
			badgeColor: 'bg-green-500/10 text-green-400 border-green-500/20'
		},
		{
			id: 'qualify',
			label: 'AI Qualification',
			sublabel: 'Intent analysis · Lead scoring',
			icon: 'M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z',
			color: 'from-cyan-500 to-blue-600',
			glow: 'rgba(6,182,212,0.18)',
			detail: 'Score: 91 · Intent: Booking · Priority: High · Channel: WhatsApp',
			detailColor: 'text-cyan-300',
			badge: 'Score: 91',
			badgeColor: 'bg-cyan-500/10 text-cyan-400 border-cyan-500/20'
		},
		{
			id: 'book',
			label: 'Appointment Booked',
			sublabel: 'Calendar sync · Invite sent',
			icon: 'M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z',
			color: 'from-blue-500 to-violet-600',
			glow: 'rgba(59,130,246,0.18)',
			detail: 'Slot: Mon 10 AM · Duration: 30 min · Invite sent to customer',
			detailColor: 'text-blue-300',
			badge: 'Confirmed',
			badgeColor: 'bg-blue-500/10 text-blue-400 border-blue-500/20'
		},
		{
			id: 'crm',
			label: 'CRM Updated',
			sublabel: 'Contact created · Pipeline staged',
			icon: 'M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4',
			color: 'from-violet-500 to-purple-700',
			glow: 'rgba(139,92,246,0.18)',
			detail: 'Contact saved · Stage: Consultation · Owner: Auto-assigned',
			detailColor: 'text-violet-300',
			badge: 'Synced',
			badgeColor: 'bg-violet-500/10 text-violet-400 border-violet-500/20'
		},
		{
			id: 'notify',
			label: 'Team Notified',
			sublabel: 'Slack · Email · Dashboard',
			icon: 'M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9',
			color: 'from-amber-500 to-orange-600',
			glow: 'rgba(245,158,11,0.18)',
			detail: '🔔 New consultation booked — Sarah K. · Mon 10 AM · Score: 91',
			detailColor: 'text-amber-300',
			badge: 'Sent',
			badgeColor: 'bg-amber-500/10 text-amber-400 border-amber-500/20'
		}
	];

	function startInterval() {
		interval = setInterval(() => {
			if (!paused) activeStep = (activeStep + 1) % steps.length;
		}, 2000);
	}

	/** @param {number} i */
	function jumpTo(i) {
		activeStep = i;
		paused = true;
		if (interval) clearInterval(interval);
		// Resume auto-play after 4s of inactivity
		setTimeout(() => {
			paused = false;
			startInterval();
		}, 4000);
	}

	onMount(() => {
		startInterval();
		return () => { if (interval) clearInterval(interval); };
	});

	// Execution time display
	const execTimes = ['0.0s', '0.3s', '0.8s', '1.2s', '1.7s'];
</script>

<section id="workflow" class="section-padding relative overflow-hidden bg-[#030712]">
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/3 left-0 w-96 h-96 rounded-full bg-violet-600/4 blur-[130px]"></div>
		<div class="absolute bottom-1/3 right-0 w-96 h-96 rounded-full bg-cyan-500/4 blur-[130px]"></div>
	</div>

	<div class="section-container relative z-10">
		<div class="grid lg:grid-cols-2 gap-14 lg:gap-16 items-center">

			<!-- Left: Copy -->
			<div class="space-y-8">
				<div class="space-y-5">
					<div class="section-label">Automation Engine</div>
					<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white leading-tight">
						One Message.<br>
						<span class="gradient-text">Five Actions. Zero Effort.</span>
					</h2>
					<p class="text-lg text-gray-400 leading-relaxed">
						Every customer message triggers a full automation pipeline — qualification, booking, CRM sync, and team notification — all in under 2 seconds.
					</p>
				</div>

				<div class="space-y-3">
					{#each [
						{ stat: '<2s',  label: 'Full pipeline execution time' },
						{ stat: '100%', label: 'Automated — zero manual steps' },
						{ stat: '24/7', label: 'Runs while your team sleeps' }
					] as item}
						<div class="flex items-center gap-4 p-4 rounded-xl border border-white/[0.06] bg-white/[0.02]">
							<span class="text-xl font-black gradient-text w-14 flex-shrink-0">{item.stat}</span>
							<span class="text-sm text-gray-400">{item.label}</span>
						</div>
					{/each}
				</div>

				<!-- Step selector hint -->
				<p class="text-xs text-gray-600">↗ Click any step in the pipeline to inspect it</p>

				<a href="#contact" class="btn-primary inline-flex group">
					See Full Workflow
					<svg class="w-4 h-4 group-hover:translate-x-0.5 transition-transform duration-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
					</svg>
				</a>
			</div>

			<!-- Right: Interactive pipeline -->
			<div class="relative">
				<div class="absolute inset-0 rounded-2xl pointer-events-none"
					style="background: radial-gradient(circle at 50% 50%, rgba(6,182,212,0.04) 0%, transparent 70%);">
				</div>

				<!-- Execution timer bar -->
				<div class="mb-3 flex items-center justify-between px-1">
					<span class="text-[10px] text-gray-600 uppercase tracking-wider">Pipeline execution</span>
					<div class="flex items-center gap-1.5">
						<div class="w-1.5 h-1.5 rounded-full bg-cyan-500 animate-pulse"></div>
						<span class="text-[10px] text-cyan-400 font-mono font-semibold">{execTimes[activeStep]} / 1.7s</span>
					</div>
				</div>

				<!-- Progress bar -->
				<div class="mb-4 h-1 rounded-full bg-white/[0.05] overflow-hidden">
					<div class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500 transition-all duration-500"
						style="width: {((activeStep + 1) / steps.length) * 100}%">
					</div>
				</div>

				<div class="space-y-2">
					{#each steps as step, i}
						<div class="relative">
							<!-- Clickable step card -->
							<button
								onclick={() => jumpTo(i)}
								class="w-full text-left relative rounded-2xl border transition-all duration-400 overflow-hidden
									{activeStep === i
										? 'border-white/[0.18] bg-white/[0.05] shadow-lg scale-[1.01]'
										: activeStep > i
											? 'border-white/[0.08] bg-white/[0.03]'
											: 'border-white/[0.04] bg-white/[0.01] hover:border-white/[0.08] hover:bg-white/[0.02]'}"
							>
								<!-- Active glow -->
								{#if activeStep === i}
									<div class="absolute inset-0 pointer-events-none"
										style="background: radial-gradient(circle at 0% 50%, {step.glow} 0%, transparent 55%);">
									</div>
								{/if}

								<div class="relative flex items-start gap-4 px-5 py-3.5">
									<!-- Icon + check -->
									<div class="flex-shrink-0 flex flex-col items-center gap-1 pt-0.5">
										<div class="w-9 h-9 rounded-xl bg-gradient-to-br {step.color} flex items-center justify-center shadow-lg transition-all duration-300
											{activeStep === i ? 'scale-110 shadow-cyan-500/20' : 'opacity-50'}">
											<svg class="w-4 h-4 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
												<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d={step.icon}/>
											</svg>
										</div>
										{#if activeStep > i}
											<div class="w-3.5 h-3.5 rounded-full bg-green-500/20 border border-green-500/40 flex items-center justify-center">
												<svg class="w-2 h-2 text-green-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
													<path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"/>
												</svg>
											</div>
										{/if}
									</div>

									<!-- Content -->
									<div class="flex-1 min-w-0">
										<div class="flex items-center justify-between gap-2 mb-0.5">
											<span class="text-sm font-semibold transition-colors duration-300
												{activeStep === i ? 'text-white' : activeStep > i ? 'text-gray-400' : 'text-gray-600'}">
												{step.label}
											</span>
											<div class="flex items-center gap-2 flex-shrink-0">
												{#if activeStep === i}
													<span class="text-[9px] px-2 py-0.5 rounded-full border font-semibold {step.badgeColor} animate-in fade-in duration-300">
														{step.badge}
													</span>
													<span class="flex items-center gap-1 text-[9px] text-cyan-400 font-semibold">
														<span class="w-1 h-1 rounded-full bg-cyan-400 animate-pulse"></span>
														Running
													</span>
												{:else if activeStep > i}
													<span class="text-[9px] text-green-400 font-semibold">✓ {execTimes[i]}</span>
												{/if}
											</div>
										</div>
										<div class="text-[11px] text-gray-600">{step.sublabel}</div>
										{#if activeStep === i}
											<div class="text-[11px] {step.detailColor} font-mono bg-white/[0.04] rounded-lg px-3 py-1.5 mt-2 animate-in fade-in duration-300 leading-relaxed">
												{step.detail}
											</div>
										{/if}
									</div>
								</div>
							</button>

							<!-- Connector -->
							{#if i < steps.length - 1}
								<div class="flex justify-center my-0.5 pointer-events-none">
									<div class="flex flex-col items-center gap-0">
										<div class="w-px h-3 transition-colors duration-500 {activeStep > i ? 'bg-cyan-500/50' : 'bg-white/[0.05]'}"></div>
										<svg class="w-3 h-3 transition-colors duration-500 {activeStep > i ? 'text-cyan-500/70' : 'text-white/[0.06]'}" fill="currentColor" viewBox="0 0 24 24">
											<path d="M12 16l-6-6h12l-6 6z"/>
										</svg>
									</div>
								</div>
							{/if}
						</div>
					{/each}
				</div>
			</div>
		</div>
	</div>
</section>
