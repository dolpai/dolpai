<script>
	import { onMount } from 'svelte';

	const stats = [
		{ value: '500+',  label: 'Active Businesses',  sublabel: 'and growing daily' },
		{ value: '1M+',   label: 'Messages Handled',   sublabel: 'every month' },
		{ value: '<1s',   label: 'Response Time',      sublabel: 'average' },
		{ value: '95%',   label: 'Satisfaction Rate',  sublabel: 'from customers' }
	];

	let visible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => { if (entries[0].isIntersecting) visible = true; },
			{ threshold: 0.3 }
		);
		const el = document.getElementById('stats-section');
		if (el) observer.observe(el);
		return () => observer.disconnect();
	});
</script>

<section id="stats-section" class="relative overflow-hidden py-20 sm:py-24">
	<!-- Full-width gradient band -->
	<div class="absolute inset-0 bg-gradient-to-r from-cyan-500/5 via-blue-600/8 to-cyan-500/5"></div>
	<div class="absolute inset-0 grid-overlay opacity-50"></div>
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-cyan-500/30 to-transparent"></div>
	<div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-cyan-500/30 to-transparent"></div>

	<div class="section-container relative z-10">
		<div class="grid grid-cols-2 lg:grid-cols-4 gap-8 lg:gap-4">
			{#each stats as stat, i}
				<div
					class="text-center space-y-2 transition-all duration-700 {visible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'}"
					style="transition-delay: {i * 120}ms"
				>
					<div class="text-4xl sm:text-5xl lg:text-6xl font-black gradient-text leading-none">
						{stat.value}
					</div>
					<div class="text-sm sm:text-base font-semibold text-white">{stat.label}</div>
					<div class="text-xs text-gray-600">{stat.sublabel}</div>
				</div>
			{/each}
		</div>
	</div>
</section>
