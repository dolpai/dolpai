<script>
	import { onMount } from 'svelte';

	let isOpen = $state(false);
	let isScrolled = $state(false);
	let logoError = $state(false);

	function toggleMenu() { isOpen = !isOpen; }
	function closeMenu() { isOpen = false; }
	function handleLogoError() { logoError = true; }

	onMount(() => {
		const handleScroll = () => { isScrolled = window.scrollY > 40; };
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	const navLinks = [
		{ href: '#services',      label: 'Features' },
		{ href: '#integrations',  label: 'Integrations' },
		{ href: '#use-cases',     label: 'Use Cases' },
		{ href: '#pricing',       label: 'Pricing' }
	];
</script>

<nav
	class="fixed top-0 left-0 right-0 z-50 transition-all duration-500
	{isScrolled
		? 'bg-[#030712]/80 backdrop-blur-2xl border-b border-white/[0.06] shadow-2xl shadow-black/40'
		: 'bg-transparent'}"
>
	<!-- Skip to content (accessibility) -->
	<a href="#main-content"
		class="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 focus:z-[100] focus:px-4 focus:py-2 focus:rounded-lg focus:bg-cyan-500 focus:text-white focus:text-sm focus:font-semibold">
		Skip to content
	</a>
	<div class="section-container">
		<div class="flex items-center justify-between h-16 sm:h-[72px]">

			<!-- Logo -->
			<a href="/" class="flex items-center gap-3 group" aria-label="Dolpai home">
				{#if !logoError}
					<img
						src="/logo.png"
						alt="Dolpai"
						class="h-8 sm:h-9 w-auto transition-all duration-300 group-hover:brightness-110"
						onerror={handleLogoError}
					/>
				{:else}
					<div class="w-8 h-8 sm:w-9 sm:h-9 rounded-lg bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center shadow-lg shadow-cyan-500/30 group-hover:shadow-cyan-500/50 transition-all duration-300">
						<span class="text-white font-bold text-base">D</span>
					</div>
				{/if}
				<span class="text-lg sm:text-xl font-bold tracking-tight text-white group-hover:text-cyan-400 transition-colors duration-200">
					Dolpai
				</span>
			</a>

			<!-- Desktop nav -->
			<div class="hidden md:flex items-center gap-1">
				{#each navLinks as link}
					<a
						href={link.href}
						class="relative px-4 py-2 text-sm font-medium text-gray-400 hover:text-white transition-colors duration-200 rounded-lg hover:bg-white/5 group"
					>
						{link.label}
						<span class="absolute bottom-1 left-4 right-4 h-px bg-gradient-to-r from-cyan-500 to-blue-500 scale-x-0 group-hover:scale-x-100 transition-transform duration-300 origin-left"></span>
					</a>
				{/each}
			</div>

			<!-- Desktop CTA -->
			<div class="hidden md:flex items-center gap-3">
				<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer" class="btn-secondary text-sm px-5 py-2.5">
					Contact
				</a>
				<a href="#contact" class="btn-primary text-sm px-5 py-2.5">
					Get Free Demo
					<svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
					</svg>
				</a>
			</div>

			<!-- Mobile hamburger -->
			<button
				onclick={toggleMenu}
				class="md:hidden relative w-10 h-10 flex items-center justify-center rounded-lg border border-white/10 bg-white/5 hover:bg-white/10 transition-all duration-200"
				aria-label="Toggle menu"
				aria-expanded={isOpen}
			>
				<div class="w-5 flex flex-col gap-1.5 transition-all duration-300">
					<span class="block h-px bg-white transition-all duration-300 {isOpen ? 'rotate-45 translate-y-2' : ''}"></span>
					<span class="block h-px bg-white transition-all duration-300 {isOpen ? 'opacity-0 scale-x-0' : ''}"></span>
					<span class="block h-px bg-white transition-all duration-300 {isOpen ? '-rotate-45 -translate-y-2' : ''}"></span>
				</div>
			</button>
		</div>
	</div>

	<!-- Mobile menu -->
	{#if isOpen}
		<div class="md:hidden bg-[#030712]/95 backdrop-blur-2xl border-t border-white/[0.06]">
			<div class="section-container py-5 space-y-1">
				{#each navLinks as link}
					<a
						href={link.href}
						onclick={closeMenu}
						class="flex items-center px-4 py-3 text-sm font-medium text-gray-400 hover:text-white hover:bg-white/5 rounded-xl transition-all duration-200"
					>
						{link.label}
					</a>
				{/each}
				<div class="pt-4 space-y-3 border-t border-white/[0.06] mt-4">
					<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer" onclick={closeMenu} class="btn-secondary w-full justify-center text-sm">
						Contact
					</a>
					<a href="#contact" onclick={closeMenu} class="btn-primary w-full justify-center text-sm">
						Get Free Demo
					</a>
				</div>
			</div>
		</div>
	{/if}
</nav>
