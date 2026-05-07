<script>
	import { onMount } from 'svelte';

	let isVisible = $state(false);

	onMount(() => {
		const handleScroll = () => { isVisible = window.scrollY > 600; };
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function scrollToTop() {
		window.scrollTo({ top: 0, behavior: 'smooth' });
	}
</script>

{#if isVisible}
	<button
		onclick={scrollToTop}
		class="fixed bottom-24 right-6 z-40 w-11 h-11 rounded-xl border border-white/[0.08] bg-white/[0.05] backdrop-blur-sm
		flex items-center justify-center text-gray-500 hover:text-white hover:border-cyan-500/30 hover:bg-cyan-500/10
		hover:scale-110 active:scale-95 transition-all duration-200 shadow-lg
		animate-in fade-in slide-in-from-bottom-4 duration-300"
		aria-label="Scroll to top"
	>
		<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
			<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M5 10l7-7m0 0l7 7m-7-7v18" />
		</svg>
	</button>
{/if}
