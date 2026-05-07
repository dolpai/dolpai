<script>
	const kpis = [
		{
			before: '4–8 hours',
			after: '<1 second',
			label: 'Average Response Time',
			improvement: '28,800x faster',
			icon: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z',
			color: 'cyan'
		},
		{
			before: '23%',
			after: '67%',
			label: 'Lead Conversion Rate',
			improvement: '+191% improvement',
			icon: 'M13 7h8m0 0v8m0-8l-8 8-4-4-6 6',
			color: 'blue'
		},
		{
			before: '60%',
			after: '3%',
			label: 'Missed Inquiries',
			improvement: '95% reduction',
			icon: 'M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z',
			color: 'violet'
		},
		{
			before: '22 hrs/week',
			after: '2 hrs/week',
			label: 'Manual Response Work',
			improvement: '91% time saved',
			icon: 'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z',
			color: 'cyan'
		}
	];

	const insights = [
		{ metric: '1.2M+', label: 'Conversations automated', sub: 'across all clients' },
		{ metric: '94%',   label: 'First-contact resolution', sub: 'no human needed' },
		{ metric: '4.8/5', label: 'Customer satisfaction', sub: 'avg across industries' },
		{ metric: '18 days', label: 'Average payback period', sub: 'from first month' }
	];

	const colorMap = {
		cyan:   { before: 'text-red-400',  after: 'text-cyan-400',   bar: 'bg-gradient-to-r from-cyan-500 to-blue-500' },
		blue:   { before: 'text-red-400',  after: 'text-blue-400',   bar: 'bg-gradient-to-r from-blue-500 to-violet-500' },
		violet: { before: 'text-red-400',  after: 'text-violet-400', bar: 'bg-gradient-to-r from-violet-500 to-cyan-500' }
	};
</script>

<section id="results" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/4 left-0 w-96 h-96 rounded-full bg-cyan-500/4 blur-[130px]"></div>
		<div class="absolute bottom-1/4 right-0 w-96 h-96 rounded-full bg-violet-500/4 blur-[130px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Business Results</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Numbers That <span class="gradient-text">Matter</span>
			</h2>
			<p class="text-lg text-gray-500">
				Real outcomes from businesses that switched to Dolpai. Measured, not estimated.
			</p>
		</div>

		<!-- Before / After KPI cards -->
		<div class="grid sm:grid-cols-2 gap-5 max-w-4xl mx-auto mb-14">
			{#each kpis as kpi}
				{@const c = colorMap[kpi.color]}
				<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 hover:border-white/[0.12] hover:bg-white/[0.04] transition-all duration-300 overflow-hidden">
					<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
						style="background: radial-gradient(circle at 100% 0%, rgba(6,182,212,0.05) 0%, transparent 60%);">
					</div>
					<div class="relative space-y-4">
						<!-- Label -->
						<div class="text-xs font-semibold text-gray-500 uppercase tracking-wider">{kpi.label}</div>

						<!-- Before → After -->
						<div class="flex items-center gap-3">
							<div class="flex-1 rounded-xl border border-red-500/15 bg-red-500/5 px-4 py-3 text-center">
								<div class="text-[10px] text-gray-600 mb-1 uppercase tracking-wider">Before</div>
								<div class="text-lg font-bold {c.before} line-through opacity-70">{kpi.before}</div>
							</div>
							<svg class="w-5 h-5 text-gray-600 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
							</svg>
							<div class="flex-1 rounded-xl border border-cyan-500/15 bg-cyan-500/5 px-4 py-3 text-center">
								<div class="text-[10px] text-gray-600 mb-1 uppercase tracking-wider">With Dolpai</div>
								<div class="text-lg font-bold {c.after}">{kpi.after}</div>
							</div>
						</div>

						<!-- Improvement badge -->
						<div class="flex items-center gap-2">
							<div class="h-1.5 flex-1 rounded-full bg-white/[0.05] overflow-hidden">
								<div class="h-full w-4/5 rounded-full {c.bar}"></div>
							</div>
							<span class="text-xs font-semibold text-green-400 whitespace-nowrap">{kpi.improvement}</span>
						</div>
					</div>
				</div>
			{/each}
		</div>

		<!-- AI Performance Insights -->
		<div class="max-w-4xl mx-auto">
			<div class="relative rounded-2xl border border-white/[0.07] bg-white/[0.02] overflow-hidden">
				<!-- Header bar -->
				<div class="flex items-center justify-between px-6 py-4 border-b border-white/[0.06] bg-white/[0.02]">
					<div class="flex items-center gap-2">
						<div class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></div>
						<span class="text-xs font-semibold text-gray-400 uppercase tracking-wider">AI Performance Dashboard</span>
					</div>
					<span class="text-[10px] text-gray-600">Aggregated across 500+ clients · Updated daily</span>
				</div>

				<div class="grid grid-cols-2 sm:grid-cols-4 divide-x divide-y sm:divide-y-0 divide-white/[0.05]">
					{#each insights as insight}
						<div class="px-6 py-6 text-center">
							<div class="text-3xl font-black gradient-text mb-1">{insight.metric}</div>
							<div class="text-sm font-medium text-white mb-0.5">{insight.label}</div>
							<div class="text-xs text-gray-600">{insight.sub}</div>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</div>
</section>
