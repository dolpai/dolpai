<section class="section-padding">
	<div class="section-container">
		<div class="text-center space-y-4 mb-12 sm:mb-16">
			<h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold">
				Loved by Businesses Worldwide
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				See what our customers say about Dolpai
			</p>
		</div>

		<div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
			{#each testimonials as testimonial, i}
				<div class="card space-y-4 group" style="animation-delay: {i * 100}ms">
					<!-- Stars -->
					<div class="flex space-x-1">
						{#each Array(5) as _, i}
							<svg class="w-5 h-5 text-yellow-500" fill="currentColor" viewBox="0 0 20 20">
								<path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
							</svg>
						{/each}
					</div>

					<!-- Quote -->
					<p class="text-gray-300 leading-relaxed">"{testimonial.quote}"</p>

					<!-- Author -->
					<div class="flex items-center space-x-3 pt-4 border-t border-dark-800">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center text-white font-bold text-lg">
							{testimonial.name.charAt(0)}
						</div>
						<div>
							<div class="font-semibold text-white">{testimonial.name}</div>
							<div class="text-sm text-gray-400">{testimonial.role}</div>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<script>
	const testimonials = [
		{
			name: 'Sarah Johnson',
			role: 'CEO, TechStart Inc',
			quote: 'Dolpai transformed our customer service. We now respond instantly to every inquiry, even at 3 AM. Our conversion rate increased by 40%!'
		},
		{
			name: 'Michael Chen',
			role: 'Founder, GrowthLabs',
			quote: 'The AI is incredibly smart. It handles 90% of our customer conversations perfectly. Our team can finally focus on strategic work.'
		},
		{
			name: 'Emma Rodriguez',
			role: 'Marketing Director, ShopNow',
			quote: 'Best investment we made this year. Setup took 10 minutes, and we started seeing results immediately. Highly recommend!'
		},
		{
			name: 'David Kim',
			role: 'Owner, Local Cafe',
			quote: 'As a small business, I can\'t afford 24/7 staff. Dolpai handles bookings and questions while I sleep. Game changer!'
		},
		{
			name: 'Lisa Thompson',
			role: 'COO, HealthPlus',
			quote: 'The multi-channel support is amazing. WhatsApp, Instagram, Facebook - all in one place. Our response time went from hours to seconds.'
		},
		{
			name: 'James Wilson',
			role: 'Sales Manager, AutoDeals',
			quote: 'We were losing leads to competitors with faster responses. Not anymore. Dolpai captures every opportunity instantly.'
		}
	];
</script>
