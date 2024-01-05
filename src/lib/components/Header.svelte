<script>
  import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
  import { faBars, faXmark } from '@fortawesome/free-solid-svg-icons';
  import { cubicOut } from 'svelte/easing';

  // State to track if the menu is open
  let isMenuOpen = false;

  // Navigation links
  const navLinks = [
    { href: '#portfolio', text: 'Portfolio' },
    { href: '/', text: 'About' }
  ];

  /**
   * Custom transition to slide the menu from the right.
   **/
  function slideRight(node, { delay = 0, duration = 400 }) {
    return {
      delay,
      duration,
      css: (t) => `transform: translateX(${(1 - cubicOut(t)) * 100}%);`
    };
  }
</script>

<header class="absolute inset-x-0 top-0 z-50">
  <nav class="flex justify-end p-6 px-8">
    <!-- Desktop Menu -->
    <div class="hidden lg:flex gap-x-10">
      {#each navLinks as link}
        <a href={link.href} class="text-sm underline-animation">
          {link.text}
        </a>
      {/each}
    </div>
    <!-- Hamburger Button -->
    <div class="flex lg:hidden">
      <button 
        type="button"
        class="text-primary"
        aria-label="Open menu"
        aria-expanded={isMenuOpen}
        on:click={() => isMenuOpen = !isMenuOpen} >
        <FontAwesomeIcon icon={faBars} aria-hidden="true"/>
      </button>
    </div>
  </nav>
  {#if isMenuOpen}
    <!-- Overlay -->
    <div
      class="fixed inset-0 bg-black bg-opacity-50 z-40"
      role="button"
      tabindex="0"
      on:click={() => isMenuOpen = false}
      on:keydown={(e) => e.key === 'Enter' && (isMenuOpen = false)}>
    </div>
    <!-- Mobile Menu -->
    <div
      class="fixed p-6 inset-y-0 right-0 z-50 w-full bg-dark sm:max-w-sm lg:hidden"
      role="dialog"
      aria-modal="true"
      in:slideRight
      out:slideRight>
      <div class="flex items-center px-6">
        <button 
          type="button"
          class="text-primary"
          aria-label="Close menu"
          on:click={() => isMenuOpen = false}>
          <FontAwesomeIcon icon={faXmark} aria-hidden="true"/>
        </button>
      </div>
      <div class="space-y-2 p-6 mt-[50%]">
        {#each navLinks as link}
          <a
            href={link.href}
            class="text-[4rem] block transition-opacity duration-300 hover:opacity-50"
            on:click={() => isMenuOpen = false}>
            {link.text}
          </a>
        {/each}
      </div>
    </div>
  {/if}
</header>