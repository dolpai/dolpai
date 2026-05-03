<script>
	import { onMount } from 'svelte';
	
	let isOpen = $state(false);
	let isScrolled = $state(false);
	let logoError = $state(false);

	function toggleMenu() {
		isOpen = !isOpen;
	}

	function closeMenu() {
		isOpen = false;
	}

	function handleLogoError() {
		logoError = true;
	}

	onMount(() => {
		const handleScroll = () => {
			isScrolled = window.scrollY > 20;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	const navLinks = [
		{ href: '#services', label: 'Services' },
		{ href: '#how-it-works', label: 'How It Works' },
		{ href: '#benefits', label: 'Benefits' },
		{ href: '#pricing', label: 'Pricing' }
	];
</script>

<nav class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 {isScrolled ? 'bg-[#0a0e27]/80 backdrop-blur-xl border-b border-white/10 shadow-lg shadow-primary-500/10' : 'bg-transparent'}">
	<div class="section-container">
		<div class="flex items-center justify-between h-16 sm:h-20">
			<!-- Logo -->
			<a href="/" class="flex items-center space-x-3 group">
				{#if !logoError}
					<img src="/logo.png" alt="Dolpai" class="h-8 sm:h-10 w-auto group-hover:scale-110 transition-transform duration-300" onerror={handleLogoError} />
				{:else}
					<div class="w-8 h-8 sm:w-10 sm:h-10 bg-gradient-to-br from-primary-500 to-cyan-500 rounded-lg flex items-center justify-center group-hover:scale-110 group-hover:rotate-6 transition-all duration-300 shadow-lg shadow-primary-500/30">
						<span class="text-white font-bold text-lg sm:text-xl">D</span>
					</div>
				{/if}
				<span class="text-xl sm:text-2xl font-bold text-white group-hover:text-primary-400 transition-colors">Dolpai</span>
			</a>

			<!-- Desktop Navigation -->
			<div class="hidden md:flex items-center space-x-8">
				{#each navLinks as link}
					<a 
						href={link.href} 
						class="text-gray-300 hover:text-primary-400 transition-colors duration-200 font-medium relative group"
					>
						{link.label}
						<span class="absolute bottom-0 left-0 w-0 h-0.5 bg-gradient-to-r from-primary-500 to-cyan-500 group-hover:w-full transition-all duration-300"></span>
					</a>
				{/each}
				<a href="#contact" class="btn-primary">
					Get Started
				</a>
			</div>

			<!-- Mobile Menu Button -->
			<button
				onclick={toggleMenu}
				class="md:hidden p-2 text-gray-300 hover:text-white transition-colors"
				aria-label="Toggle menu"
			>
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					{#if isOpen}
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
					{:else}
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
					{/if}
				</svg>
			</button>
		</div>
	</div>

	<!-- Mobile Menu -->
	{#if isOpen}
		<div class="md:hidden bg-[#0a0e27]/95 backdrop-blur-xl border-t border-white/10 animate-in slide-in-from-top duration-300">
			<div class="section-container py-4 space-y-3">
				{#each navLinks as link}
					<a 
						href={link.href}
						onclick={closeMenu}
						class="block py-2 text-gray-300 hover:text-white transition-colors duration-200 font-medium"
					>
						{link.label}
					</a>
				{/each}
				<a href="#contact" onclick={closeMenu} class="block w-full text-center btn-primary mt-4">
					Get Started
				</a>
			</div>
		</div>
	{/if}
</nav>
