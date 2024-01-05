<script>
    // Sitemap links
    const sitemapLinks = [
        { href: '/', text: 'Home' }, 
        { href: '#portfolio', text: 'Portfolio' },
        { href: '/', text: 'About' }
    ];
</script>

<footer class="py-8">
    <div class="mx-auto flex flex-col md:flex-row justify-between items-center px-6 lg:px-8">
        <!-- Sitemap -->
        <div class="flex item-center space-x-4 text-sm pb-6 md:pb-0">
            <p class="text-sm px-2">Sitemap</p>
            {#each sitemapLinks as link}
                <a href={link.href} class="text-sm px-2 opacity-75 underline-animation">
                    {link.text}
                </a>
            {/each}
        </div>
        <!-- Copyright -->
        <span class="text-sm text-center opacity-75 pb-6 md:pb-0">
            Copyright © 2023 Ben Sohanpal | All rights reserved
        </span>
    </div>
</footer>