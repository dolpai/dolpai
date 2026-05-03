<script>
	import { onMount } from 'svelte';
	
	let isVisible = $state(false);
	let logoError = $state(false);

	onMount(() => {
		setTimeout(() => {
			isVisible = true;
		}, 100);
	});

	function handleLogoError() {
		logoError = true;
	}
</script>

<section class="relative min-h-screen flex items-center justify-center overflow-hidden">
	<!-- Dark overlay for text readability -->
	<div class="absolute inset-0 bg-gradient-to-b from-[#0a0e27]/60 via-[#0a0e27]/80 to-[#000000]"></div>
	
	<!-- Centered glow effect -->
	<div class="absolute top-1/3 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] bg-primary-500/20 rounded-full blur-[120px] animate-pulse"></div>

	<div class="section-container relative z-10 py-32">
		<div class="max-w-5xl mx-auto text-center space-y-10 {isVisible ? 'animate-in fade-in slide-in-from-bottom-4 duration-1000' : 'opacity-0'}">
			
			<!-- Logo -->
			<div class="flex justify-center mb-8">
				{#if !logoError}
					<img src="/logo.png" alt="Dolpai Logo" class="h-16 sm:h-20 w-auto" onerror={handleLogoError} />
				{:else}
					<div class="w-16 h-16 sm:w-20 sm:h-20 bg-gradient-to-br from-primary-500 to-cyan-500 rounded-2xl flex items-center justify-center shadow-lg shadow-primary-500/50">
						<span class="text-white font-bold text-3xl sm:text-4xl">D</span>
					</div>
				{/if}
			</div>

			<!-- Main Headline with glow -->
			<div class="glow-effect">
				<h1 class="text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-bold leading-tight tracking-tight">
					Never Miss a
					<span class="gradient-text block mt-2">Customer Again</span>
				</h1>
			</div>

			<!-- Subheadline - shorter -->
			<p class="text-xl sm:text-2xl md:text-3xl text-gray-300 max-w-3xl mx-auto leading-relaxed font-light">
				AI automation that responds instantly, 24/7
			</p>

			<!-- CTA Buttons -->
			<div class="flex flex-col sm:flex-row items-center justify-center gap-4 pt-6">
				<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer" class="btn-primary w-full sm:w-auto text-center group">
					<span class="flex items-center justify-center space-x-2">
						<span>Get Free Demo</span>
						<svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
						</svg>
					</span>
				</a>
			</div>

			<!-- Microtext -->
			<p class="text-sm text-gray-500 pt-4">
				Setup in minutes. No technical skills needed.
			</p>

			<!-- Product Preview - Chat UI Mock -->
			<div class="pt-16 max-w-3xl mx-auto">
				<div class="glass-card p-6 sm:p-8 shadow-2xl shadow-primary-500/20 animate-float">
					<!-- Chat Header -->
					<div class="flex items-center space-x-3 pb-4 border-b border-white/10">
						<div class="w-10 h-10 rounded-full bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center">
							<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
							</svg>
						</div>
						<div class="flex-1">
							<div class="font-semibold text-white">Dolpai AI Assistant</div>
							<div class="text-xs text-gray-400 flex items-center space-x-1">
								<span class="w-2 h-2 bg-green-500 rounded-full animate-pulse"></span>
								<span>Active now</span>
							</div>
						</div>
					</div>

					<!-- Chat Messages -->
					<div class="py-6 space-y-4">
						<div class="flex justify-end">
							<div class="max-w-[70%] px-4 py-3 rounded-2xl bg-primary-600 text-white text-sm">
								Do you have the iPhone 15 in stock?
							</div>
						</div>
						<div class="flex justify-start">
							<div class="max-w-[80%] px-4 py-3 rounded-2xl bg-white/10 backdrop-blur-sm text-gray-100 text-sm">
								Yes! We have all colors available. Which one interests you?
							</div>
						</div>
						<div class="flex justify-end">
							<div class="max-w-[70%] px-4 py-3 rounded-2xl bg-primary-600 text-white text-sm">
								Blue, 256GB
							</div>
						</div>
						<div class="flex justify-start">
							<div class="max-w-[80%] px-4 py-3 rounded-2xl bg-white/10 backdrop-blur-sm text-gray-100 text-sm">
								Perfect! iPhone 15 Blue 256GB is $899. Would you like to reserve it?
							</div>
						</div>
					</div>

					<!-- Typing indicator -->
					<div class="flex items-center space-x-2 text-xs text-gray-500">
						<div class="flex space-x-1">
							<div class="w-2 h-2 bg-primary-500 rounded-full animate-bounce" style="animation-delay: 0ms"></div>
							<div class="w-2 h-2 bg-primary-500 rounded-full animate-bounce" style="animation-delay: 150ms"></div>
							<div class="w-2 h-2 bg-primary-500 rounded-full animate-bounce" style="animation-delay: 300ms"></div>
						</div>
						<span>AI is typing...</span>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Scroll indicator -->
	<div class="absolute bottom-8 left-1/2 -translate-x-1/2 animate-bounce">
		<svg class="w-6 h-6 text-primary-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
			<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
		</svg>
	</div>
</section>
