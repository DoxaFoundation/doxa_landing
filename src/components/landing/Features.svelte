<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    const featureCards = document.querySelectorAll(".feature-card");
    gsap.from(featureCards, {
      scrollTrigger: {
        trigger: ".features-grid",
        start: "top 80%",
        toggleActions: "play none none reverse",
      },
      duration: 0.8,
      y: 50,
      opacity: 0,
      stagger: 0.15,
      ease: "power3.out",
    });

    // Animate intro/outro/subheading text
    gsap.from(".intro-text, .features-subheading, .outro-text", {
      scrollTrigger: {
        trigger: ".intro-text",
        start: "top 85%",
        toggleActions: "play none none reverse",
      },
      duration: 1,
      y: 30,
      opacity: 0,
      ease: "power3.out",
      stagger: 0.2,
    });
  }
</script>

<section
  class="py-24 md:py-32 bg-primary-800 text-primary-100 relative overflow-hidden"
>
  <div class="container mx-auto px-6 relative z-10">
    <!-- Decorative elements -->
    <div class="absolute -left-20 -top-20 w-64 h-64 bg-primary-500/10 rounded-full filter blur-3xl animate-pulse"></div>
    <div class="absolute right-0 bottom-0 w-40 h-40 bg-primary-300/10 rounded-full filter blur-3xl animate-pulse" style="animation-delay: 1s;"></div>
    
    <div class="text-center mb-16 md:mb-20 relative">
      <span class="block h-1 w-20 bg-gradient-to-r from-primary-500/20 to-primary-300/40 mx-auto mb-8 rounded-full"></span>
      <div class="intro-text-container flex flex-wrap justify-center gap-4 mb-6 max-w-3xl mx-auto">
        <div class="bg-primary-900/70 backdrop-blur-sm p-3 rounded-lg transform hover:scale-105 transition-all duration-300 border border-primary-700/30">
          <span class="intro-text text-xl md:text-2xl text-primary-200 font-light block">No banks</span>
        </div>
        <div class="bg-primary-900/70 backdrop-blur-sm p-3 rounded-lg transform hover:scale-105 transition-all duration-300 border border-primary-700/30">
          <span class="intro-text text-xl md:text-2xl text-primary-200 font-light block">No middlemen</span>
        </div>
        <div class="bg-primary-900/70 backdrop-blur-sm p-3 rounded-lg transform hover:scale-105 transition-all duration-300 border border-primary-700/30">
          <span class="intro-text text-xl md:text-2xl text-primary-200 font-light block">No central point</span>
        </div>
      </div>
      <div class="intro-text bg-primary-900/80 rounded-xl p-4 mb-16 max-w-3xl mx-auto transform hover:translate-y-[-5px] transition-all duration-500 border border-primary-700/20">
        <span class="block text-center text-xl md:text-2xl text-primary-100 font-light">Just programmable money — backed, secure, fast</span>
        <div class="flex justify-center gap-4 mt-2">
          <span class="text-primary-50 font-medium px-3 py-1 bg-primary-800/90 rounded-md animate-pulse">backed</span>
          <span class="text-primary-50 font-medium px-3 py-1 bg-primary-800/90 rounded-md animate-pulse" style="animation-delay: 0.5s;">secure</span>
          <span class="text-primary-50 font-medium px-3 py-1 bg-primary-800/90 rounded-md animate-pulse" style="animation-delay: 1s;">fast</span>
        </div>
      </div>
      <h2
        class="features-subheading text-3xl md:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-primary-200 to-primary-100 mb-16 inline-flex items-center gap-3"
      >
        <span class="text-5xl animate-bounce" style="animation-duration: 2s;">🚀</span> Built for Real Impact
      </h2>
      <div class="h-0.5 w-40 bg-gradient-to-r from-primary-400/20 to-primary-300/5 mx-auto mt-4 rounded-full"></div>
    </div>

    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 md:gap-10 features-grid mb-20"
    >
      <!-- Feature Cards (5 total) with improved styling -->
      <div class="feature-card group" style="opacity: 1; visibility: visible;">
        <div class="feature-icon group-hover:scale-110 transition-transform">🌍</div>
        <h3 class="feature-title group-hover:text-primary-50">Cross-Border Remittances</h3>
        <p class="feature-description group-hover:text-primary-200">
          Send money instantly, without the fees.
        </p>
      </div>
      <div class="feature-card group" style="opacity: 1; visibility: visible;">
        <div class="feature-icon group-hover:scale-110 transition-transform">🛒</div>
        <h3 class="feature-title group-hover:text-primary-50">E-Commerce Ready</h3>
        <p class="feature-description group-hover:text-primary-200">
          Stable payments for global businesses.
        </p>
      </div>
      <div class="feature-card group" style="opacity: 1; visibility: visible;">
        <div class="feature-icon group-hover:scale-110 transition-transform">📱</div>
        <h3 class="feature-title group-hover:text-primary-50">Microtransactions</h3>
        <p class="feature-description group-hover:text-primary-200">Enable tiny payments for big ideas.</p>
      </div>
      <!-- Bottom two cards in one line centered -->
      <div class="col-span-1 sm:col-span-2 lg:col-span-3 flex justify-center gap-8 md:gap-10">
        <div class="feature-card group w-full sm:w-1/2 lg:w-1/3" style="opacity: 1; visibility: visible;">
          <div class="feature-icon group-hover:scale-110 transition-transform">⚙️</div>
          <h3 class="feature-title group-hover:text-primary-50">dApp Integration</h3>
          <p class="feature-description group-hover:text-primary-200">Plug Doxa into any Web3 app.</p>
        </div>
        <div class="feature-card group w-full sm:w-1/2 lg:w-1/3" style="opacity: 1; visibility: visible;">
          <div class="feature-icon group-hover:scale-110 transition-transform">💱</div>
          <h3 class="feature-title group-hover:text-primary-50">Trading</h3>
          <p class="feature-description group-hover:text-primary-200">
            Use USDx as a reliable base asset across chains.
          </p>
        </div>
      </div>
    </div>

    <div class="text-center mt-20 relative">
      <div class="absolute left-1/2 -translate-x-1/2 top-0 w-0.5 h-10 bg-gradient-to-b from-primary-400/50 to-transparent"></div>
      <p
        class="outro-text text-2xl md:text-3xl font-semibold text-transparent bg-clip-text bg-gradient-to-r from-primary-300 to-primary-100 tracking-wide"
      >
        Your money. Your way. <span class="text-primary-100">Anywhere.</span>
      </p>
      <div class="mt-4 flex justify-center">
        <span class="inline-block h-1 w-16 bg-gradient-to-r from-primary-400/40 to-transparent rounded-full"></span>
      </div>
    </div>
  </div>
</section>

<style>
  .feature-card {
    @apply p-8 rounded-2xl bg-primary-700/30 backdrop-blur-lg border border-primary-500/40 transition-all duration-300 text-center transform hover:-translate-y-2 hover:bg-primary-700/50 hover:border-primary-400 shadow-lg hover:shadow-primary-500/20;
  }

  .feature-icon {
    @apply text-5xl mb-5 inline-block text-primary-400;
  }

  .feature-title {
    @apply text-xl font-semibold text-primary-100 mb-4;
  }

  .feature-description {
    @apply text-primary-300/90 text-base leading-relaxed;
  }
</style>
