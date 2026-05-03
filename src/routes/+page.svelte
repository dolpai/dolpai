<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import Problem from '$lib/components/Problem.svelte';
	import Solution from '$lib/components/Solution.svelte';
	import Services from '$lib/components/Services.svelte';
	import HowItWorks from '$lib/components/HowItWorks.svelte';
	import Stats from '$lib/components/Stats.svelte';
	import Benefits from '$lib/components/Benefits.svelte';
	import Demo from '$lib/components/Demo.svelte';
	import Testimonials from '$lib/components/Testimonials.svelte';
	import Pricing from '$lib/components/Pricing.svelte';
	import FAQ from '$lib/components/FAQ.svelte';
	import CTA from '$lib/components/CTA.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import WhatsAppButton from '$lib/components/WhatsAppButton.svelte';
	import ScrollToTop from '$lib/components/ScrollToTop.svelte';
</script>

<svelte:head>
	<title>Dolpai - Never Miss a Customer Again | AI-Powered Business Automation</title>
	<meta name="description" content="Automate your customer interactions with AI. Respond instantly, convert more leads, and grow your business 24/7 with Dolpai." />
</svelte:head>

<div class="min-h-screen">
	<Navbar />
	<main>
		<Hero />
		<Problem />
		<Solution />
		<Services />
		<HowItWorks />
		<Stats />
		<Benefits />
		<Demo />
		<Testimonials />
		<Pricing />
		<FAQ />
		<CTA />
	</main>
	<Footer />
	<WhatsAppButton />
	<ScrollToTop />
</div>
