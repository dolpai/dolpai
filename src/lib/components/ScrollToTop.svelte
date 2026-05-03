<script>
	import { onMount } from 'svelte';
	
	let isVisible = $state(false);

	onMount(() => {
		const handleScroll = () => {
			isVisible = window.scrollY > 500;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function scrollToTop() {
		window.scrollTo({
			top: 0,
			behavior: 'smooth'
		});
	}
</script>

{#if isVisible}
	<button
		onclick={scrollToTop}
		class="fixed bottom-24 right-6 z-40 w-12 h-12 bg-dark-800 hover:bg-primary-600 border border-dark-700 hover:border-primary-500 rounded-full flex items-center justify-center shadow-lg hover:shadow-xl transition-all duration-300 hover:scale-110 active:scale-95 group animate-in fade-in slide-in-from-bottom-4 duration-300"
		aria-label="Scroll to top"
	>
		<svg class="w-6 h-6 text-gray-400 group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
			<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
		</svg>
	</button>
{/if}
