<script>
	import Navbar from '$lib/components/Navbar.svelte';
	import Hero from '$lib/components/Hero.svelte';
	import Problem from '$lib/components/Problem.svelte';
	import Vision from '$lib/components/Vision.svelte';
	import Solution from '$lib/components/Solution.svelte';
	import Services from '$lib/components/Services.svelte';
	import Integrations from '$lib/components/Integrations.svelte';
	import Workflow from '$lib/components/Workflow.svelte';
	import HowItWorks from '$lib/components/HowItWorks.svelte';
	import Stats from '$lib/components/Stats.svelte';
	import BusinessResults from '$lib/components/BusinessResults.svelte';
	import Benefits from '$lib/components/Benefits.svelte';
	import Demo from '$lib/components/Demo.svelte';
	import TryDolpai from '$lib/components/TryDolpai.svelte';
	import UseCases from '$lib/components/UseCases.svelte';
	import TrustInfrastructure from '$lib/components/TrustInfrastructure.svelte';
	import Testimonials from '$lib/components/Testimonials.svelte';
	import OnboardingFunnel from '$lib/components/OnboardingFunnel.svelte';
	import Pricing from '$lib/components/Pricing.svelte';
	import FAQ from '$lib/components/FAQ.svelte';
	import CTA from '$lib/components/CTA.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import WhatsAppButton from '$lib/components/WhatsAppButton.svelte';
	import ScrollToTop from '$lib/components/ScrollToTop.svelte';
</script>

<svelte:head>
	<title>Dolpai — AI Automation Platform for Modern Businesses</title>
	<meta name="description" content="Dolpai deploys intelligent AI agents that respond instantly, qualify leads, and book appointments 24/7 — across WhatsApp, Instagram, Facebook, and your website." />
	<meta property="og:title" content="Dolpai — AI Automation Platform for Modern Businesses" />
	<meta property="og:description" content="Never miss a customer again. AI agents that respond instantly, qualify leads, and book appointments 24/7." />
	<link rel="canonical" href="https://dolpai.com" />
</svelte:head>

<div class="min-h-screen">
	<Navbar />
	<main id="main-content">
		<Hero />
		<Problem />
		<Vision />
		<Solution />
		<Services />
		<Integrations />
		<Workflow />
		<HowItWorks />
		<Stats />
		<BusinessResults />
		<Benefits />
		<Demo />
		<TryDolpai />
		<UseCases />
		<TrustInfrastructure />
		<Testimonials />
		<OnboardingFunnel />
		<Pricing />
		<FAQ />
		<CTA />
	</main>
	<Footer />
	<WhatsAppButton />
	<ScrollToTop />
</div>
