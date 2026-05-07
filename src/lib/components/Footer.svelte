<script>
	const productLinks = [
		{ href: '#services',      label: 'Features' },
		{ href: '#integrations',  label: 'Integrations' },
		{ href: '#workflow',      label: 'Automation' },
		{ href: '#demo',          label: 'Live Demo' },
		{ href: '#pricing',       label: 'Pricing' },
		{ href: '#use-cases',     label: 'Use Cases' }
	];

	const companyLinks = [
		{ href: '#vision',    label: 'About Dolpai' },
		{ href: '#trust',     label: 'Security' },
		{ href: '#results',   label: 'Results' },
		{ href: '#faq',       label: 'FAQ' },
		{ href: '#contact',   label: 'Contact Sales' }
	];

	const integrationsLinks = [
		{ href: '#integrations', label: 'WhatsApp' },
		{ href: '#integrations', label: 'Instagram' },
		{ href: '#integrations', label: 'Facebook' },
		{ href: '#integrations', label: 'Telegram' },
		{ href: '#integrations', label: 'Website Chat' },
		{ href: '#integrations', label: 'CRM Systems' }
	];

	const socialLinks = [
		{
			href: 'https://www.instagram.com/dolp.ai/',
			label: 'Instagram',
			hoverColor: 'hover:text-pink-400',
			icon: `<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>`
		},
		{
			href: 'https://www.linkedin.com/company/dolpai',
			label: 'LinkedIn',
			hoverColor: 'hover:text-blue-400',
			icon: `<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>`
		},
		{
			href: 'https://github.com/Dolpaii',
			label: 'GitHub',
			hoverColor: 'hover:text-white',
			icon: `<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>`
		},
		{
			href: 'https://wa.me/9779765244850',
			label: 'WhatsApp',
			hoverColor: 'hover:text-green-400',
			icon: `<svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z"/></svg>`
		}
	];
</script>

<footer class="relative bg-[#030712] border-t border-white/[0.06]">
	<div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-white/[0.06] to-transparent"></div>

	<div class="section-container pt-16 sm:pt-20 pb-8">

		<!-- Top: Brand + newsletter-style CTA -->
		<div class="flex flex-col lg:flex-row items-start justify-between gap-10 pb-14 border-b border-white/[0.06]">
			<!-- Brand -->
			<div class="space-y-4 max-w-xs">
				<div class="flex items-center gap-3">
					<div class="w-9 h-9 rounded-xl bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center shadow-lg shadow-cyan-500/20">
						<span class="text-white font-black text-base">D</span>
					</div>
					<div>
						<span class="text-xl font-bold text-white tracking-tight">Dolpai</span>
						<div class="text-[10px] text-gray-600 -mt-0.5 tracking-widest uppercase">AI Automation Platform</div>
					</div>
				</div>
				<p class="text-sm text-gray-500 leading-relaxed">
					Intelligent automation for modern businesses. We help teams respond faster, capture more leads, and scale customer communication without adding headcount.
				</p>
				<!-- Status indicator -->
				<div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-green-500/20 bg-green-500/5">
					<span class="w-1.5 h-1.5 rounded-full bg-green-500 animate-pulse"></span>
					<span class="text-[10px] text-green-400 font-semibold">All systems operational</span>
				</div>
			</div>

			<!-- Quick CTA -->
			<div class="lg:text-right space-y-3">
				<p class="text-sm text-gray-400">Ready to automate your customer communication?</p>
				<div class="flex flex-col sm:flex-row lg:justify-end gap-2">
					<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer"
						class="btn-primary text-sm px-6 py-2.5">
						Book Free Demo
						<svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
						</svg>
					</a>
					<a href="mailto:mrproductionnp@gmail.com"
						class="btn-secondary text-sm px-6 py-2.5">
						Email Us
					</a>
				</div>
			</div>
		</div>

		<!-- Main link grid -->
		<div class="grid grid-cols-2 sm:grid-cols-4 gap-8 lg:gap-10 py-12">

			<!-- Product -->
			<div class="space-y-4">
				<h4 class="text-[10px] font-bold text-gray-400 uppercase tracking-[0.15em]">Product</h4>
				<ul class="space-y-2.5">
					{#each productLinks as link}
						<li>
							<a href={link.href} class="text-sm text-gray-500 hover:text-white transition-colors duration-200 flex items-center gap-1.5 group">
								<span class="w-0 group-hover:w-2 h-px bg-cyan-500 transition-all duration-200 flex-shrink-0"></span>
								{link.label}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Integrations -->
			<div class="space-y-4">
				<h4 class="text-[10px] font-bold text-gray-400 uppercase tracking-[0.15em]">Integrations</h4>
				<ul class="space-y-2.5">
					{#each integrationsLinks as link}
						<li>
							<a href={link.href} class="text-sm text-gray-500 hover:text-white transition-colors duration-200 flex items-center gap-1.5 group">
								<span class="w-0 group-hover:w-2 h-px bg-cyan-500 transition-all duration-200 flex-shrink-0"></span>
								{link.label}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Company -->
			<div class="space-y-4">
				<h4 class="text-[10px] font-bold text-gray-400 uppercase tracking-[0.15em]">Company</h4>
				<ul class="space-y-2.5">
					{#each companyLinks as link}
						<li>
							<a href={link.href} class="text-sm text-gray-500 hover:text-white transition-colors duration-200 flex items-center gap-1.5 group">
								<span class="w-0 group-hover:w-2 h-px bg-cyan-500 transition-all duration-200 flex-shrink-0"></span>
								{link.label}
							</a>
						</li>
					{/each}
				</ul>
			</div>

			<!-- Contact -->
			<div class="space-y-4">
				<h4 class="text-[10px] font-bold text-gray-400 uppercase tracking-[0.15em]">Contact</h4>
				<ul class="space-y-2.5">
					<li>
						<a href="mailto:mrproductionnp@gmail.com"
							class="text-sm text-gray-500 hover:text-white transition-colors duration-200 break-all">
							mrproductionnp@gmail.com
						</a>
					</li>
					<li>
						<a href="https://wa.me/9779765244850" target="_blank" rel="noopener noreferrer"
							class="text-sm text-gray-500 hover:text-green-400 transition-colors duration-200 flex items-center gap-2">
							<svg class="w-3.5 h-3.5 text-green-500 flex-shrink-0" fill="currentColor" viewBox="0 0 24 24">
								<path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z"/>
							</svg>
							WhatsApp Support
						</a>
					</li>
					<!-- Social icons -->
					<li class="pt-2">
						<div class="flex gap-2">
							{#each socialLinks as social}
								<a
									href={social.href}
									target="_blank"
									rel="noopener noreferrer"
									class="w-8 h-8 rounded-lg border border-white/[0.07] bg-white/[0.03] flex items-center justify-center text-gray-600 {social.hoverColor} hover:border-white/[0.14] hover:bg-white/[0.06] transition-all duration-200"
									aria-label={social.label}
								>
									{@html social.icon}
								</a>
							{/each}
						</div>
					</li>
				</ul>
			</div>
		</div>

		<!-- Bottom bar -->
		<div class="pt-6 border-t border-white/[0.05] flex flex-col sm:flex-row items-center justify-between gap-4">
			<div class="flex items-center gap-4 text-xs text-gray-700">
				<span>&copy; {new Date().getFullYear()} Dolpai Labs. All rights reserved.</span>
				<span class="hidden sm:block text-white/10">·</span>
				<span class="hidden sm:block">Built for modern businesses</span>
			</div>
			<div class="flex items-center gap-5 text-xs text-gray-700">
				<a href="#contact" class="hover:text-gray-400 transition-colors duration-200">Privacy Policy</a>
				<a href="#contact" class="hover:text-gray-400 transition-colors duration-200">Terms of Service</a>
				<a href="#contact" class="hover:text-gray-400 transition-colors duration-200">Security</a>
			</div>
		</div>
	</div>
</footer>
