<script>
	/** @type {number | null} */
	let openIndex = $state(null);

	/** @param {number} index */
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
			answer: 'We offer flexible pricing plans starting from $49/month for small businesses. Enterprise plans are available for larger organizations. All plans include a 14-day free trial.'
		},
		{
			question: 'Is my customer data secure?',
			answer: 'Absolutely. We use bank-level encryption and comply with GDPR, CCPA, and other data protection regulations. Your data is never shared with third parties.'
		},
		{
			question: 'Can I customize the AI\'s responses?',
			answer: 'Yes! You can train Dolpai on your brand voice, products, services, and policies. The AI learns from your feedback and continuously improves over time.'
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

<section id="faq" class="section-padding relative overflow-hidden bg-[#030712]">
	<!-- Divider -->
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<!-- Background -->
	<div class="absolute inset-0 pointer-events-none">
		<div class="absolute bottom-0 right-1/4 w-80 h-80 rounded-full bg-cyan-500/4 blur-[120px]"></div>
	</div>

	<div class="section-container relative z-10">
		<!-- Header -->
		<div class="max-w-2xl mx-auto text-center space-y-5 mb-16 sm:mb-20">
			<div class="section-label">FAQ</div>
			<h2 class="text-4xl sm:text-5xl font-extrabold tracking-tight text-white">
				Frequently Asked <span class="gradient-text">Questions</span>
			</h2>
			<p class="text-lg text-gray-500">
				Everything you need to know about Dolpai.
			</p>
		</div>

		<!-- FAQ list -->
		<div class="max-w-3xl mx-auto space-y-3">
			{#each faqs as faq, i}
				<div
					class="group rounded-2xl border transition-all duration-300 overflow-hidden cursor-pointer
						{openIndex === i
							? 'border-cyan-500/20 bg-cyan-500/[0.04]'
							: 'border-white/[0.06] bg-white/[0.02] hover:border-white/[0.10] hover:bg-white/[0.03]'}"
					onclick={() => toggle(i)}
					role="button"
					tabindex="0"
					onkeydown={(e) => e.key === 'Enter' && toggle(i)}
					aria-expanded={openIndex === i}
				>
					<div class="flex items-center justify-between gap-4 px-6 py-5">
						<h3 class="font-semibold text-white text-sm sm:text-base leading-snug flex-1 {openIndex === i ? 'text-cyan-300' : ''}">
							{faq.question}
						</h3>
						<div class="flex-shrink-0 w-7 h-7 rounded-lg border border-white/[0.08] bg-white/[0.04] flex items-center justify-center transition-all duration-300 {openIndex === i ? 'rotate-180 border-cyan-500/30 bg-cyan-500/10' : ''}">
							<svg class="w-3.5 h-3.5 {openIndex === i ? 'text-cyan-400' : 'text-gray-500'}" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M19 9l-7 7-7-7" />
							</svg>
						</div>
					</div>

					{#if openIndex === i}
						<div class="px-6 pb-5 text-sm text-gray-400 leading-relaxed animate-in slide-in-from-top-2 duration-200 border-t border-white/[0.05] pt-4">
							{faq.answer}
						</div>
					{/if}
				</div>
			{/each}
		</div>

		<!-- Still have questions -->
		<div class="text-center mt-12">
			<p class="text-gray-500 text-sm mb-4">Still have questions?</p>
			<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer" class="btn-secondary inline-flex">
				<svg class="w-4 h-4 text-green-400" fill="currentColor" viewBox="0 0 24 24">
					<path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z"/>
				</svg>
				Chat with Us on WhatsApp
			</a>
		</div>
	</div>
</section>
