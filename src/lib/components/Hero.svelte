<script>
  const tableRows = [
    { 
      header: 'Location',
      content: 'Leicestershire',
    },
    { 
      header: 'Age',
      content: '21',
    },
    { 
      header: 'Projects',
      content: '6',
    },
    { 
      header: 'Status',
      content: 'Available',
    },
    { 
      header: 'Qualifications',
      content: 'BSc Computer Science',
    }
  ];
</script>

<div class="relative isolate py-4 px-8">
  <!-- Background Content -->
  <div class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80" aria-hidden="true">
    <div class="animate-float overflow-hidden relative left-[calc(50%-11rem)] aspect-[1155/950] w-[100rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#E88011] to-[#1A0902] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]" 
    style="clip-path: polygon(1.0% 93.3%, 1.2% 38.0%, 11.2% 63.5%, 70.8% 32.3%, 97.4% 89.9%, 35.8% 39.8%, 83.8% 51.8%, 78.1% 22.3%, 56.9% 90.8%, 65.5% 42.6%, 48.3% 37.6%, 83.7% 69.1%, 36.2% 11.5%, 82.6% 63.5%, 29.2% 31.3%, 79.2% 26.7%, 1.0% 93.3%)"></div>
  </div>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <!-- Name Title -->
    <div class="pt-12 md:pt-20">
      <h1 class="text-[4.8rem] sm:text-[5.5rem] leading-[5rem] md:text-8xl lg:text-9xl tracking-tight">Ben<br>Sohanpal</h1>
    </div>
    <!-- Details Table -->
    <div class="pt-4 text-md md:text-lg md:pt-20 md:pl-[30%]">
      <hr class="border-t my-3">
      <div class="space-y-3">
        {#each tableRows as row}
          <div class="flex justify-between">
            <p class="pr-1">{row.header}</p>
            <p class="text-right">{row.content}</p>
          </div>
        {/each}
      </div>
    </div>
    <!-- Role Description -->
    <div class="pt-5 text-lg">
      <p class="opacity-75">Freelance Web Developer</p>
      <p class="opacity-75">Computer Science Student</p>
      <p class="opacity-75">S&P 500 Software Engineer</p>
    </div>
    <!-- CTA Buttons -->
    <div class="pt-5 flex items-center md:justify-end gap-x-6">
      <a href="/" class="cta-link flex items-center cursor-pointer" disabled>
        About
        <span class="px-1" aria-hidden="true">→</span>
      </a>
      <a href="#portfolio" class="cta-link flex items-center cursor-pointer" id="cta-alternative">
        Portfolio
        <span class="px-1" aria-hidden="true">→</span>
      </a>
    </div>
  </div>
</div>
<hr class="my-6 mx-8">

<style>
  .animate-float {
    animation: float 20s linear infinite;
  }
  .cta-link {
    border: 2px solid #F6F5E8;
    border-radius: 0.75rem; 
    padding: 0.5rem 0.875rem; 
    font-weight: 600; 
    display: flex;
    align-items: center;
    text-decoration: none;
    color: #F6F5E8; 
    transition: background-color 0.3s linear, color 0.3s linear;
  }

  .cta-link span{
    transition: color 0.3s linear;
  }

  .cta-link:hover,
  #cta-alternative {
    background-color: #F6F5E8;
    color: black;
  }

  .cta-link:hover span,
  #cta-alternative span{
    color: black;
  }

  #cta-alternative:hover {
    background-color: transparent;
    color: #F6F5E8;
  }

  #cta-alternative:hover span{
    color: #F6F5E8;
  }
</style>