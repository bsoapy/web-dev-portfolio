<script>
  import Header from "$lib/components/Header.svelte";
  import Hero from "$lib/components/Hero.svelte";
  import Portfolio from "../lib/components/Portfolio.svelte";
  import Footer from "$lib/components/Footer.svelte";
  import "../app.css";

  import { injectSpeedInsights } from "@vercel/speed-insights/sveltekit"

  injectSpeedInsights();
</script>

<div class="bg-dark">
  <Header />
  <Hero />
  <Portfolio />
  <slot />
  <Footer />
</div>


