<script>
  import { onMount } from 'svelte';
  import { register } from 'swiper/element/bundle';

  // Register Swiper components
  register();

  // Project cards
  const cardContent = [
    {
      title: 'Patel & Co',
      subtitle: 'Barbershop',
      url: 'patel-co.co.uk',
      bg: 'patel-co/mockup.png',
      favicon: 'patel-co/favicon.png',
    },
    {
      title: 'Legally Literate',
      subtitle: 'Legal Advice for Students',
      url: 'legallyliterate.site',
      bg: 'legally-literate/mockup.jpg',
      favicon: 'legally-literate/favicon.png',
    },
    {
      title: 'Refine Aesthetics',
      subtitle: 'Nurse Practitioner',
      url: 'refineaestheticsbyalison.com',
      bg: 'refine-aesthetics/mockup.png',
      favicon: 'refine-aesthetics/favicon.png',
    },
  ];

  onMount(() => {
    // swiper element
    const swiperEl = document.querySelector('swiper-container');

    // swiper parameters
    const swiperParams = {
      slidesPerView: 1,
      breakpoints: {
        576: {
          slidesPerView: 2,
        },
        769: {
          slidesPerView: 3,
        },
      },
      spaceBetween: 5,
      autoplay: {
        delay: 1000,
        waitForTransition: true,
        disableOnInteraction: false,
      },
      speed: 3000,
      effect: 'slide',
      loop: true,
    };
    
    // now we need to assign all parameters to Swiper element
    Object.assign(swiperEl, swiperParams);
    
    // now we can initialize Swiper
    swiperEl.initialize();
  });
</script>

<div class="relative isolate py-1" id="portfolio">
  <h3 class="text-2xl tracking-tight px-8">All projects</h3>
  <swiper-container class="py-4 px-6" init="false">
    {#each cardContent as card}
      <swiper-slide class="p-2 h-auto">
        <a href="/" class="project-card bg-dark border-2 border-opaque border-primary pt-12 pb-8 px-16 rounded-3xl shadow-lg flex flex-col" style="--bg-image: url('{card.bg}');">
          <img src="{card.favicon}" alt="{card.title} logo">
          <div class="pt-12 pb-6">
            <p class="text-2xl mb-4">{card.title}</p>
            <p class="text-sm opacity-75">{card.subtitle}</p>
            <p class="text-sm opacity-75">{card.url}</p>
          </div>
        </a>
      </swiper-slide>
    {/each}
  </swiper-container>
</div>

<style>
  .project-card {
    /* Transition for scale and background image */
    transition: transform 0.5s ease-in-out, background-image 0.5s ease-in-out;
    overflow: hidden;
    position: relative;
    z-index: 0;
    height: 100%;
  }

  /* Overlay for project card */
  .project-card::before {
    /* Black overlay with 50% opacity */
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
    opacity: 0;
    transition: opacity 0.5s ease-in-out;
    z-index: -1;
  }

  /* Background image for project card */
  .project-card::after{
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-image: var(--bg-image);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    opacity: 0;
    transition: opacity 0.5s ease-in-out;
    z-index: -2;
  }

  /* Slight scale up on hover */
  .project-card:hover {
    transform: scale(1.02); 
  }

  /* Show overlay and background image on hover */
  .project-card:hover::before,
  .project-card:hover::after {
    opacity: 1;
  }
</style>
