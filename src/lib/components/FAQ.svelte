<script>
	/** @type {number | null} */
	let openIndex = $state(null);

	/**
	 * @param {number} index
	 */
	function toggle(index) {
		openIndex = openIndex === index ? null : index;
	}

	const faqs = [
		{
			question: 'How quickly can I set up Dolpai?',
			answer: 'Most businesses are up and running in under 10 minutes. Simply connect your messaging channels, train the AI on your business basics, and you\'re ready to go. No technical skills required.'
		},
		{
			question: 'Which messaging platforms does Dolpai support?',
			answer: 'Dolpai integrates with WhatsApp, Facebook Messenger, Instagram DMs, your website chat, and more. All conversations are managed from one unified dashboard.'
		},
		{
			question: 'Can the AI handle complex customer questions?',
			answer: 'Yes! Dolpai uses advanced AI to understand context and provide accurate responses. For complex issues it can\'t handle, it seamlessly escalates to your team with full conversation history.'
		},
		{
			question: 'How much does Dolpai cost?',
			answer: 'We offer flexible pricing plans starting from $49/month for small businesses. Enterprise plans are available for larger organizations. Contact us for a custom quote.'
		},
		{
			question: 'Is my customer data secure?',
			answer: 'Absolutely. We use bank-level encryption and comply with GDPR, CCPA, and other data protection regulations. Your data is never shared with third parties.'
		},
		{
			question: 'Can I customize the AI\'s responses?',
			answer: 'Yes! You can train Dolpai on your brand voice, products, services, and policies. The AI learns from your feedback and improves over time.'
		},
		{
			question: 'What if I need help or support?',
			answer: 'We offer 24/7 customer support via chat, email, and phone. Our team is always ready to help you get the most out of Dolpai.'
		},
		{
			question: 'Can I try Dolpai before committing?',
			answer: 'Yes! We offer a 14-day free trial with full access to all features. No credit card required to start.'
		}
	];
</script>

<section id="faq" class="section-padding relative">
	<div class="absolute inset-0 section-overlay"></div>
	
	<div class="section-container relative z-10">
		<div class="text-center space-y-4 mb-12 sm:mb-16">
			<h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold">
				Frequently Asked <span class="gradient-text">Questions</span>
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				Everything you need to know about Dolpai
			</p>
		</div>

		<div class="max-w-3xl mx-auto space-y-4">
			{#each faqs as faq, i}
				<div class="card cursor-pointer" onclick={() => toggle(i)} role="button" tabindex="0" onkeydown={(e) => e.key === 'Enter' && toggle(i)}>
					<div class="flex items-start justify-between space-x-4">
						<h3 class="text-lg font-semibold text-white flex-1">
							{faq.question}
						</h3>
						<div 
							class="flex-shrink-0 w-6 h-6 rounded-full bg-primary-500/10 flex items-center justify-center transition-transform duration-300 {openIndex === i ? 'rotate-180' : ''}"
							aria-label="Toggle answer"
						>
							<svg class="w-4 h-4 text-primary-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
							</svg>
						</div>
					</div>
					
					{#if openIndex === i}
						<div class="mt-4 text-gray-400 leading-relaxed animate-in slide-in-from-top-2 duration-300">
							{faq.answer}
						</div>
					{/if}
				</div>
			{/each}
		</div>

		<!-- Still have questions? -->
		<div class="text-center mt-12">
			<p class="text-gray-400 mb-4">Still have questions?</p>
			<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer" class="btn-primary inline-block">
				Chat with Us
			</a>
		</div>
	</div>
</section>
