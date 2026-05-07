<script>
	const problems = [
		{
			title: 'Delayed Responses Kill Deals',
			description: 'Every hour of delay reduces conversion by 10%. Customers move on before you even see the message.',
			stat: '10%',
			statLabel: 'lost per hour'
		},
		{
			title: 'Your Team Is Overwhelmed',
			description: 'Messages pile up, leads go cold, and your best people spend hours on repetitive questions.',
			stat: '73%',
			statLabel: 'of queries are repetitive'
		},
		{
			title: 'No After-Hours Coverage',
			description: 'Your business sleeps, but your customers don\'t. You\'re missing 60% of inquiries outside business hours.',
			stat: '60%',
			statLabel: 'missed after hours'
		},
		{
			title: 'Competitors Are Faster',
			description: 'Businesses with instant response times are capturing your leads. Speed is the new competitive advantage.',
			stat: '5x',
			statLabel: 'faster = more sales'
		}
	];
</script>

<section class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Subtle top border glow -->
	<div class="absolute top-0 left-1/2 -translate-x-1/2 w-px h-24 bg-gradient-to-b from-transparent via-red-500/30 to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/2 left-1/4 w-80 h-80 rounded-full bg-red-500/5 blur-[100px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label" style="border-color: rgba(239,68,68,0.2); background: rgba(239,68,68,0.05); color: rgb(248,113,113);">
				<svg class="w-3 h-3" fill="currentColor" viewBox="0 0 20 20">
					<path fill-rule="evenodd" d="M8.257 3.099c.765-1.36 2.722-1.36 3.486 0l5.58 9.92c.75 1.334-.213 2.98-1.742 2.98H4.42c-1.53 0-2.493-1.646-1.743-2.98l5.58-9.92zM11 13a1 1 0 11-2 0 1 1 0 012 0zm-1-8a1 1 0 00-1 1v3a1 1 0 002 0V6a1 1 0 00-1-1z" clip-rule="evenodd" />
				</svg>
				The Problem
			</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Losing Customers
				<span class="block" style="background: linear-gradient(135deg, #f87171, #ef4444); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;">While You Sleep?</span>
			</h2>
			<p class="text-lg text-gray-500 leading-relaxed">
				Every missed message is a missed opportunity. Here's what slow response times are costing you.
			</p>
		</div>

		<!-- Problem cards -->
		<div class="grid sm:grid-cols-2 gap-5 max-w-4xl mx-auto">
			{#each problems as problem, i}
				<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 hover:border-red-500/20 hover:bg-red-500/[0.03] transition-all duration-300 overflow-hidden">
					<!-- Hover glow -->
					<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
						style="background: radial-gradient(circle at 50% 0%, rgba(239,68,68,0.06) 0%, transparent 70%);">
					</div>

					<div class="relative flex items-start gap-4">
						<!-- X icon -->
						<div class="flex-shrink-0 w-10 h-10 rounded-xl bg-red-500/10 border border-red-500/20 flex items-center justify-center group-hover:scale-110 transition-transform duration-300">
							<svg class="w-5 h-5 text-red-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M6 18L18 6M6 6l12 12" />
							</svg>
						</div>

						<div class="flex-1 min-w-0">
							<div class="flex items-start justify-between gap-3 mb-2">
								<h3 class="font-semibold text-white text-base leading-snug">{problem.title}</h3>
								<div class="flex-shrink-0 text-right">
									<div class="text-lg font-bold text-red-400">{problem.stat}</div>
									<div class="text-xs text-gray-600">{problem.statLabel}</div>
								</div>
							</div>
							<p class="text-sm text-gray-500 leading-relaxed">{problem.description}</p>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>
