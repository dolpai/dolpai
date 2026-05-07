<script>
	const testimonials = [
		{
			name: 'Sarah Johnson',
			role: 'CEO',
			company: 'TechStart Inc',
			quote: 'We went from responding in 4 hours to under a second. That alone increased our close rate by 40%. Dolpai paid for itself in the first week.',
			avatar: 'SJ',
			color: 'from-cyan-500 to-blue-600',
			metric: '+40% close rate'
		},
		{
			name: 'Michael Chen',
			role: 'Founder',
			company: 'GrowthLabs',
			quote: 'Dolpai handles 90% of our inbound conversations without any human involvement. My team now focuses on deals, not inbox management.',
			avatar: 'MC',
			color: 'from-blue-500 to-violet-600',
			metric: '90% automated'
		},
		{
			name: 'Emma Rodriguez',
			role: 'Marketing Director',
			company: 'ShopNow',
			quote: 'Setup was genuinely 10 minutes. I was skeptical, but the first automated booking came in before I even finished the onboarding call.',
			avatar: 'ER',
			color: 'from-violet-500 to-cyan-600',
			metric: '10 min setup'
		},
		{
			name: 'David Kim',
			role: 'Owner',
			company: 'Bloom Cafe',
			quote: 'I run a small cafe. I can\'t afford a full-time receptionist. Dolpai handles reservations, menu questions, and catering inquiries around the clock.',
			avatar: 'DK',
			color: 'from-cyan-500 to-blue-600',
			metric: '3x more bookings'
		},
		{
			name: 'Lisa Thompson',
			role: 'COO',
			company: 'HealthPlus Clinics',
			quote: 'Patient no-shows dropped 60% after we started sending automated reminders. The appointment booking flow alone justified the entire cost.',
			avatar: 'LT',
			color: 'from-blue-500 to-violet-600',
			metric: '-60% no-shows'
		},
		{
			name: 'James Wilson',
			role: 'Sales Manager',
			company: 'AutoDeals Group',
			quote: 'We were losing leads to faster competitors. Dolpai responds the moment a message arrives — day or night. Our pipeline hasn\'t looked this full in years.',
			avatar: 'JW',
			color: 'from-violet-500 to-cyan-600',
			metric: '5x lead capture'
		}
	];
</script>

<section class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute top-1/3 left-1/4 w-96 h-96 rounded-full bg-blue-600/5 blur-[120px]"></div>
		<div class="absolute bottom-1/3 right-1/4 w-96 h-96 rounded-full bg-cyan-500/5 blur-[120px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">Testimonials</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Loved by <span class="gradient-text">Businesses</span>
			</h2>
			<p class="text-lg text-gray-500">
				Don't take our word for it — hear from the businesses already using Dolpai.
			</p>
		</div>

		<!-- Testimonials grid -->
		<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-5">
			{#each testimonials as t, i}
				<div class="group relative rounded-2xl border border-white/[0.06] bg-white/[0.02] p-6 sm:p-7 hover:border-white/[0.12] hover:bg-white/[0.04] transition-all duration-300 overflow-hidden flex flex-col">
					<!-- Hover glow -->
					<div class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 pointer-events-none"
						style="background: radial-gradient(circle at 100% 0%, rgba(6,182,212,0.06) 0%, transparent 60%);">
					</div>

					<!-- Quote mark -->
					<div class="absolute top-5 right-6 text-5xl font-black text-white/[0.04] leading-none select-none">"</div>

					<div class="relative flex flex-col flex-1 space-y-5">
						<!-- Stars -->
						<div class="flex gap-1">
							{#each Array(5) as _}
								<svg class="w-4 h-4 text-amber-400" fill="currentColor" viewBox="0 0 20 20">
									<path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
								</svg>
							{/each}
						</div>

						<!-- Quote -->
						<p class="text-gray-400 text-sm leading-relaxed flex-1">"{t.quote}"</p>

						<!-- Author -->
						<div class="flex items-center gap-3 pt-4 border-t border-white/[0.06]">
							<div class="w-10 h-10 rounded-xl bg-gradient-to-br {t.color} flex items-center justify-center text-white font-bold text-sm flex-shrink-0 shadow-lg">
								{t.avatar}
							</div>
							<div class="flex-1 min-w-0">
								<div class="font-semibold text-white text-sm">{t.name}</div>
								<div class="text-xs text-gray-500">{t.role} · {t.company}</div>
							</div>
							<div class="text-[10px] font-semibold text-cyan-400 bg-cyan-500/10 border border-cyan-500/20 px-2 py-1 rounded-lg whitespace-nowrap">{t.metric}</div>
						</div>
					</div>
				</div>
			{/each}
		</div>

		<!-- Trust bar -->
		<div class="mt-16 text-center">
			<p class="text-sm text-gray-600 mb-6">Trusted by businesses across industries</p>
			<div class="flex flex-wrap items-center justify-center gap-8 opacity-30">
				{#each ['E-Commerce', 'Healthcare', 'Real Estate', 'Hospitality', 'Finance', 'Retail'] as industry}
					<span class="text-sm font-semibold text-gray-400 tracking-wider uppercase">{industry}</span>
				{/each}
			</div>
		</div>
	</div>
</section>
