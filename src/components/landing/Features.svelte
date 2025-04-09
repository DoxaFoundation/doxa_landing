<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    if (gsap && ScrollTrigger) {
      initAnimations();
    }
  });

  function initAnimations() {
    if (!gsap || !ScrollTrigger) return;

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
  class="py-24 md:py-32 bg-gradient-to-b from-gray-900 to-gray-800 text-gray-50 relative overflow-hidden"
>
  <div class="container mx-auto px-6 relative z-10">
    <div class="text-center mb-12 md:mb-16">
      <p
        class="intro-text text-xl md:text-2xl text-gray-300 mb-4 max-w-3xl mx-auto font-light leading-relaxed"
      >
        No banks. No middlemen. No central point of failure.
      </p>
      <p
        class="intro-text text-xl md:text-2xl text-gray-200 mb-16 max-w-3xl mx-auto font-light leading-relaxed"
      >
        Just programmable money—backed, secure, fast.
      </p>
      <h2
        class="features-subheading text-3xl md:text-4xl font-bold text-gray-100 mb-16 inline-flex items-center gap-3"
      >
        <span class="text-4xl">🚀</span> Built for Real Impact
      </h2>
    </div>

    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 features-grid mb-20"
    >
      <!-- Feature Cards (5 total) -->
      <div class="feature-card">
        <div class="feature-icon">🌍</div>
        <h3 class="feature-title">Cross-Border Remittances</h3>
        <p class="feature-description">
          Send money instantly, without the fees.
        </p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">🛒</div>
        <h3 class="feature-title">E-Commerce Ready</h3>
        <p class="feature-description">
          Stable payments for global businesses.
        </p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">📱</div>
        <h3 class="feature-title">Microtransactions</h3>
        <p class="feature-description">Enable tiny payments for big ideas.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">⚙️</div>
        <h3 class="feature-title">dApp Integration</h3>
        <p class="feature-description">Plug Doxa into any Web3 app.</p>
      </div>
      <div class="feature-card">
        <div class="feature-icon">💱</div>
        <h3 class="feature-title">Trading</h3>
        <p class="feature-description">
          Use USDx as a reliable base asset across chains.
        </p>
      </div>
    </div>

    <div class="text-center mt-16">
      <p
        class="outro-text text-2xl md:text-3xl font-semibold text-gray-200 tracking-wide"
      >
        Your money. Your way. Anywhere.
      </p>
    </div>
  </div>
</section>

<style>
  .feature-card {
    @apply p-8 rounded-2xl bg-gray-800/30 backdrop-blur-lg border border-gray-700/40 transition-all duration-300 text-center transform hover:-translate-y-2 hover:bg-gray-700/50 hover:border-gray-600 shadow-lg hover:shadow-gray-900/20;
  }

  .feature-icon {
    @apply text-5xl mb-5 inline-block text-gray-300;
  }

  .feature-title {
    @apply text-xl font-semibold text-gray-100 mb-4;
  }

  .feature-description {
    @apply text-gray-300/90 text-base leading-relaxed;
  }
</style>
