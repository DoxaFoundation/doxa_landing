<script lang="ts">
  import { onMount } from "svelte";
  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";

  export let gsap: any;
  export let ScrollTrigger: any;

  const tvl = tweened(0, {
    duration: 3000,
    easing: cubicOut,
  });

  const apy = tweened(0, {
    duration: 3000,
    easing: cubicOut,
  });

  onMount(() => {
    if (gsap) {
      // Initialize animations
      initAnimations();

      // Start number animations with a slight delay
      setTimeout(() => {
        tvl.set(4.8);
        apy.set(8.2);
      }, 500);
    }
  });

  function initAnimations() {
    if (!gsap) return;

    // Hero Title Animation
    const heroTl = gsap.timeline();
    heroTl
      .from(".hero-title", {
        duration: 1.2,
        y: 100,
        opacity: 0,
        ease: "power4.out",
      })
      .from(
        ".hero-description",
        {
          duration: 1,
          y: 50,
          opacity: 0,
          ease: "power3.out",
        },
        "-=0.5"
      )
      .from(
        ".hero-subheadline",
        {
          duration: 1,
          y: 50,
          opacity: 0,
          ease: "power3.out",
        },
        "-=0.7"
      )
      .from(
        ".hero-buttons a",
        {
          duration: 0.8,
          y: 30,
          opacity: 0,
          stagger: 0.2,
          ease: "power3.out",
        },
        "-=0.5"
      );

    // Particle Animation
    const particles = document.querySelectorAll(".particle");
    particles.forEach((particle) => {
      gsap.to(particle, {
        x: "random(-50, 50)",
        y: "random(-50, 50)",
        duration: "random(5, 10)",
        repeat: -1,
        yoyo: true,
        ease: "none",
      });
    });

    // Stats Cards Animation
    const statsCards = document.querySelectorAll(".stats-card");
    gsap.set(statsCards, { opacity: 1 });
    gsap.from(statsCards, {
      duration: 1,
      y: 50,
      opacity: 0,
      stagger: 0.2,
      ease: "power3.out",
      scrollTrigger: {
        trigger: ".stats-card",
        start: "top 80%",
        end: "bottom 20%",
        toggleActions: "play none none reverse",
      },
    });

    // Continuous floating animation for stats cards
    statsCards.forEach((card, index) => {
      gsap.to(card, {
        y: -20,
        duration: 2,
        delay: index * 0.2,
        ease: "power1.inOut",
        repeat: -1,
        yoyo: true,
      });
    });
  }
</script>

<div
  class="relative min-h-screen overflow-hidden bg-gradient-to-br from-gray-900 via-gray-800 to-gray-900 text-gray-50 font-space-grotesk flex items-center"
>
  <!-- Dark Grid Background with subtle glow -->
  <div
    class="grid-background absolute inset-0 z-0 opacity-30 pointer-events-none"
  ></div>

  <!-- Hero Section -->
  <div class="container mx-auto px-6 py-20 relative">
    <!-- Animated Particles with neon effect -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      {#each Array(25) as _, i}
        <div
          class="particle absolute rounded-full"
          style="
            background: {[
            '#333333',
            '#4d4d4d',
            '#666666',
            '#999999',
            '#cccccc',
          ][i % 5]};
            left: {Math.random() * 100}%;
            top: {Math.random() * 100}%;
            height: {Math.random() * 3 + 1}px;
            width: {Math.random() * 3 + 1}px;
            filter: blur({Math.random() * 2 + 1}px);
            opacity: {Math.random() * 0.6 + 0.2};
            box-shadow: 0 0 8px 2px {[
            '#333333',
            '#4d4d4d',
            '#666666',
            '#999999',
            '#cccccc',
          ][i % 5]};
          "
        />
      {/each}
    </div>

    <div class="flex flex-col md:flex-row items-center gap-10">
      <div class="md:w-1/2 relative flex flex-col justify-center">
        <!-- Dark Neon Orbs -->
        <div
          class="absolute -left-20 -top-20 w-64 h-64 bg-gray-600/10 rounded-full filter blur-3xl animate-pulse"
        ></div>
        <div
          class="absolute right-0 bottom-0 w-40 h-40 bg-gray-500/10 rounded-full filter blur-3xl animate-pulse"
          style="animation-delay: 1s;"
        ></div>
        <div
          class="absolute left-40 top-20 w-20 h-20 bg-gray-700/10 rounded-full filter blur-3xl animate-pulse"
          style="animation-delay: 2s;"
        ></div>

        <div
          class="relative z-10 backdrop-blur-sm bg-black/40 p-8 rounded-3xl border border-gray-700/20"
        >
          <div class="flex justify-center mb-6">
            <img src="/images/DOXA.svg" alt="Doxa Logo" class="h-20" />
          </div>

          <h1
            class="hero-title text-5xl md:text-7xl font-bold text-gray-50 mb-6 leading-tight relative text-center"
          >
            <span
              class="relative inline-block transform hover:scale-105 transition-transform duration-500"
            >
              <span
                class="text-transparent bg-clip-text bg-gradient-to-r from-gray-300 via-gray-400 to-gray-300"
                >Doxa</span
              >
              <span
                class="absolute inset-0 bg-gradient-to-r from-gray-300 via-gray-400 to-gray-300 filter blur-xl opacity-30 animate-pulse"
              ></span>
            </span>
            <span class="block md:inline relative">
              <span class="relative z-10">The</span>
              <span class="relative z-10 ml-2 font-extrabold">future</span>
              <span class="relative z-10 ml-2">of</span>
              <span
                class="relative z-10 ml-2 text-transparent bg-clip-text bg-gradient-to-br from-gray-300 to-gray-400"
                >Currency</span
              >
              <span
                class="absolute bottom-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-gray-500 to-transparent opacity-70"
              ></span>
            </span>
          </h1>

          <h2
            class="hero-subheadline text-2xl md:text-3xl mb-6 text-gray-200/90 font-semibold text-center mt-2"
          >
            <span
              class="bg-gradient-to-r from-gray-400 to-gray-500 bg-clip-text text-transparent"
              >Create</span
            >
            •
            <span
              class="bg-gradient-to-r from-gray-500 to-gray-600 bg-clip-text text-transparent"
              >Own</span
            >
            •
            <span
              class="bg-gradient-to-r from-gray-600 to-gray-400 bg-clip-text text-transparent"
              >Earn</span
            >
          </h2>

          <p
            class="hero-description text-xl text-gray-300 mb-10 max-w-xl mx-auto text-center mt-2 backdrop-blur-sm py-3 px-6 rounded-xl border border-gray-600/20 shadow-lg shadow-gray-700/5"
          >
            A revolutionary multi-stablecoin platform powered by Doxa USD
          </p>

          <div
            class="hero-buttons flex flex-col space-y-4 md:flex-row md:space-y-0 md:space-x-6 justify-center"
          >
            <a
              href="#"
              class="group bg-gradient-to-r from-gray-700 to-gray-800 text-gray-50 px-8 py-4 rounded-full font-medium hover:from-gray-600 hover:to-gray-700 transition-all duration-300 transform hover:scale-105 hover:-rotate-1 flex items-center gap-2 shadow-lg shadow-gray-900/20"
            >
              Get Early Access
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
            <a
              href="#"
              class="group bg-transparent border-2 border-gray-600/50 text-gray-50 px-8 py-3.5 rounded-full font-medium hover:bg-gray-800/10 hover:border-gray-500 transition-all duration-300 hover:scale-105 hover:rotate-1 backdrop-blur-sm shadow-lg shadow-gray-900/10"
            >
              Read Whitepaper
            </a>
          </div>
        </div>
      </div>

      <!-- Stats Cards -->
      <div class="md:w-1/2 mt-16 md:mt-0 grid grid-cols-2 gap-6 relative">
        <!-- Enhanced Background Glow -->
        <div
          class="absolute inset-0 bg-gradient-to-br from-gray-700/10 via-gray-800/10 to-gray-600/10 filter blur-3xl"
        ></div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-gray-700/30 hover:border-gray-600/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-gray-900/10"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate font-medium">
              Total Value Locked
            </h3>
            <div class="text-3xl font-bold text-gray-50 truncate">
              ${$tvl.toFixed(1)}M
            </div>
          </div>
          <div class="text-gray-300 flex items-center gap-1 mt-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-4 w-4 flex-shrink-0"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"
              />
            </svg>
            <span class="truncate">12.5%</span>
          </div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-gray-600/30 hover:border-gray-500/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-gray-900/10"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate font-medium">APY</h3>
            <div class="text-3xl font-bold text-gray-50 truncate">
              {$apy.toFixed(1)}%
            </div>
          </div>
          <div class="text-gray-300 mt-2 truncate">↑ 0.5%</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-gray-700/30 hover:border-gray-600/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-gray-900/10"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate font-medium">
              Weekly Rewards
            </h3>
            <div class="text-3xl font-bold text-gray-50 truncate">
              125,000 DOXA
            </div>
          </div>
          <div class="mt-2 h-5">&nbsp;</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-gray-600/30 hover:border-gray-500/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-gray-900/10"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate font-medium">
              Total Fees Collected
            </h3>
            <div class="text-3xl font-bold text-gray-50 truncate">$283.5K</div>
          </div>
          <div class="mt-2 h-5">&nbsp;</div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .particle {
    will-change: transform;
    transform-style: preserve-3d;
  }

  @keyframes pulse {
    0%,
    100% {
      opacity: 0.5;
      transform: scale(1);
    }
    50% {
      opacity: 0.8;
      transform: scale(1.1);
    }
  }

  .animate-pulse {
    animation: pulse 3s infinite;
  }

  .hero-title::after {
    content: "";
    position: absolute;
    bottom: -10px;
    left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(
      to right,
      transparent,
      theme("colors.gray.500"),
      transparent
    );
    transform: scaleX(0);
    transform-origin: left;
    animation: lineReveal 1s cubic-bezier(0.4, 0, 0.2, 1) forwards;
    animation-delay: 1s;
  }

  @keyframes lineReveal {
    to {
      transform: scaleX(1);
    }
  }
</style>
