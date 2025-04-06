<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    // Integration Section Enhanced Animation
    const integrationCards = document.querySelectorAll(".integration-card");
    integrationCards.forEach((card, index) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: "top 75%",
          toggleActions: "play none none reverse",
        },
        duration: 1.5,
        y: 100,
        x: index === 0 ? -100 : 100,
        opacity: 0,
        rotation: index === 0 ? -5 : 5,
        ease: "power3.out",
      });
    });

    // Shooting stars animation
    const shootingStars = document.querySelectorAll(".shooting-star");
    shootingStars.forEach((star) => {
      gsap.to(star, {
        x: "random(100vw, 200vw)",
        y: "random(-50vh, 50vh)",
        duration: "random(2, 5)",
        repeat: -1,
        ease: "none",
        delay: "random(0, 2)",
      });
    });
  }
</script>

<section class="py-32 relative overflow-hidden">
  <div
    class="absolute inset-0 bg-gradient-to-br from-purple-900 via-[#1E0447] to-purple-900"
  ></div>
  <div class="absolute inset-0">
    {#each Array(20) as _, i}
      <div
        class="shooting-star absolute h-px opacity-20"
        style="
          background: linear-gradient(90deg, {['#FF4D4D', '#4DA6FF', '#4DFFB7'][
          i % 3
        ]}, transparent);
          width: {50 + Math.random() * 150}px;
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          transform: rotate({Math.random() * 360}deg);
        "
      />
    {/each}
  </div>

  <div class="relative container mx-auto px-6">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
      <!-- Algorithmic Stability -->
      <div
        class="integration-card p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
      >
        <h3 class="text-3xl font-bold text-white mb-6">
          Algorithmic Stability
        </h3>
        <p class="text-gray-300 text-lg mb-8">
          DoxaV3 implements advanced algorithmic mechanisms to maintain price
          stability. Our smart contracts automatically adjust supply based on
          market demand, ensuring a reliable 1:1 peg with USD.
        </p>
        <a
          href="/mechanism"
          class="inline-flex items-center gap-2 text-white hover:text-purple-400 transition-colors group"
        >
          <span>Learn How It Works</span>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 transform group-hover:translate-x-1 transition-transform"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M17 8l4 4m0 0l-4 4m4-4H3"
            />
          </svg>
        </a>
      </div>

      <!-- Integration & Development -->
      <div
        class="integration-card p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
      >
        <h3 class="text-3xl font-bold text-white mb-6">
          Integration & Development
        </h3>
        <p class="text-gray-300 text-lg mb-8">
          Built on Internet Computer, DoxaV3 offers seamless integration with
          DeFi protocols. Our SDK and APIs make it easy to integrate stablecoin
          functionality into your dapps.
        </p>
        <a
          href="/build"
          class="inline-flex items-center gap-2 text-white hover:text-purple-400 transition-colors group"
        >
          <span>Start Building</span>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 transform group-hover:translate-x-1 transition-transform"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M17 8l4 4m0 0l-4 4m4-4H3"
            />
          </svg>
        </a>
      </div>
    </div>
  </div>
</section>

<style>
  .shooting-star {
    will-change: transform;
    transform-style: preserve-3d;
  }

  .integration-card {
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
  }

  .integration-card:hover {
    transform: translateY(-10px) scale(1.02) rotate(1deg);
    box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.3);
  }

  @keyframes shooting {
    from {
      transform: translateX(-100%) rotate(var(--rotation));
      opacity: 1;
    }
    to {
      transform: translateX(200%) rotate(var(--rotation));
      opacity: 0;
    }
  }
</style>
