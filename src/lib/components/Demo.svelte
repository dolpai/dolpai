<script>
	import { onMount } from 'svelte';
	
	/** @type {Array<{type: string, text: string, delay: number}>} */
	let messages = $state([]);
	let isTyping = $state(false);

	const demoConversation = [
		{ type: 'user', text: 'Hi, do you have the iPhone 15 in stock?', delay: 1000 },
		{ type: 'bot', text: 'Hello! Yes, we have the iPhone 15 available in all colors. Which color are you interested in?', delay: 1500 },
		{ type: 'user', text: 'Blue, 256GB', delay: 2000 },
		{ type: 'bot', text: 'Perfect! The iPhone 15 in Blue (256GB) is $899. Would you like to reserve one or schedule a visit to our store?', delay: 2000 },
		{ type: 'user', text: 'Can I visit tomorrow at 2pm?', delay: 1500 },
		{ type: 'bot', text: '✅ Appointment confirmed for tomorrow at 2:00 PM. I\'ve sent the details to your email. See you then!', delay: 1800 }
	];

	onMount(() => {
		let currentIndex = 0;
		/** @type {ReturnType<typeof setTimeout> | undefined} */
		let timeoutId;

		function showNextMessage() {
			if (currentIndex < demoConversation.length) {
				isTyping = true;
				
				timeoutId = setTimeout(() => {
					isTyping = false;
					messages = [...messages, demoConversation[currentIndex]];
					currentIndex++;
					
					if (currentIndex < demoConversation.length) {
						showNextMessage();
					} else {
						// Reset after showing all messages
						setTimeout(() => {
							messages = [];
							currentIndex = 0;
							showNextMessage();
						}, 3000);
					}
				}, demoConversation[currentIndex].delay);
			}
		}

		showNextMessage();

		return () => {
			if (timeoutId) clearTimeout(timeoutId);
		};
	});
</script>

<section id="demo" class="section-padding">
	<div class="section-container">
		<div class="text-center space-y-4 mb-12 sm:mb-16">
			<h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold">
				See It In Action
			</h2>
			<p class="text-lg sm:text-xl text-gray-400 max-w-2xl mx-auto">
				Watch how Dolpai handles real customer conversations
			</p>
		</div>

		<div class="max-w-2xl mx-auto">
			<!-- Chat Interface -->
			<div class="card overflow-hidden">
				<!-- Chat Header -->
				<div class="flex items-center space-x-3 pb-4 border-b border-dark-800">
					<div class="w-10 h-10 rounded-full bg-gradient-to-br from-primary-500 to-cyan-500 flex items-center justify-center">
						<svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
						</svg>
					</div>
					<div class="flex-1">
						<div class="font-semibold">Dolpai AI</div>
						<div class="text-sm text-gray-400 flex items-center space-x-1">
							<span class="w-2 h-2 bg-green-500 rounded-full"></span>
							<span>Online</span>
						</div>
					</div>
				</div>

				<!-- Chat Messages -->
				<div class="py-6 space-y-4 min-h-[400px] max-h-[500px] overflow-y-auto">
					{#each messages as message}
						<div class="flex {message.type === 'user' ? 'justify-end' : 'justify-start'} animate-in fade-in slide-in-from-bottom-2 duration-300">
							<div class="max-w-[80%] sm:max-w-[70%]">
								<div class="px-4 py-3 rounded-2xl {message.type === 'user' ? 'bg-primary-600 text-white' : 'bg-dark-800 text-gray-100'}">
									{message.text}
								</div>
							</div>
						</div>
					{/each}

					{#if isTyping}
						<div class="flex justify-start animate-in fade-in duration-300">
							<div class="max-w-[80%] sm:max-w-[70%]">
								<div class="px-4 py-3 rounded-2xl bg-dark-800">
									<div class="flex space-x-2">
										<div class="w-2 h-2 bg-gray-500 rounded-full animate-bounce" style="animation-delay: 0ms"></div>
										<div class="w-2 h-2 bg-gray-500 rounded-full animate-bounce" style="animation-delay: 150ms"></div>
										<div class="w-2 h-2 bg-gray-500 rounded-full animate-bounce" style="animation-delay: 300ms"></div>
									</div>
								</div>
							</div>
						</div>
					{/if}
				</div>

				<!-- Chat Input (Disabled for demo) -->
				<div class="pt-4 border-t border-dark-800">
					<div class="flex items-center space-x-3 px-4 py-3 bg-dark-800 rounded-lg opacity-50">
						<input 
							type="text" 
							placeholder="Demo mode - watch the conversation..." 
							disabled
							class="flex-1 bg-transparent text-gray-400 outline-none"
						/>
						<button disabled class="text-gray-600" aria-label="Send message">
							<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>
