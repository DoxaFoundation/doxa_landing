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
    // Initialize animations
    initAnimations();

    // Start number animations with a slight delay
    setTimeout(() => {
      tvl.set(4.8);
      apy.set(8.2);
    }, 500);
  });

  function initAnimations() {
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
        ".hero-buttons",
        {
          duration: 0.8,
          y: 30,
          opacity: 0,
          ease: "power3.out",
        },
        "-=0.5"
      );

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
  class="relative min-h-screen overflow-hidden bg-gradient-to-br from-purple-900 to-[#0a0118] text-white font-space-grotesk"
>
  <!-- Grid Background -->
  <div
    class="grid-background absolute inset-0 z-0 opacity-50 pointer-events-none"
  ></div>

  <!-- Hero Section -->
  <div class="container mx-auto px-6 py-20 relative">
    <!-- Animated Particles -->
    <div class="absolute inset-0 overflow-hidden">
      {#each Array(20) as _, i}
        <div
          class="particle absolute h-2 w-2 rounded-full"
          style="
            background: {['#FF4D4D', '#4DA6FF', '#4DFFB7'][i % 3]};
            left: {Math.random() * 100}%;
            top: {Math.random() * 100}%;
            filter: blur(1px);
            opacity: 0.6;
          "
        />
      {/each}
    </div>

    <div class="flex flex-col md:flex-row items-stretch">
      <div class="md:w-1/2 relative flex flex-col justify-center">
        <!-- Gradient Orb -->
        <div
          class="absolute -left-20 -top-20 w-40 h-40 bg-purple-500/30 rounded-full filter blur-3xl animate-pulse"
        ></div>

        <h1
          class="hero-title text-5xl md:text-7xl font-bold text-white mb-8 leading-tight relative"
        >
          The Future of
          <span class="relative inline-block">
            <span
              class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-yellow-400"
              >Stablecoin</span
            >
            <div
              class="absolute inset-0 bg-gradient-to-r from-purple-400 to-yellow-400 filter blur-xl opacity-30 animate-pulse"
            ></div>
          </span>
          is Here
        </h1>

        <p class="hero-description text-xl text-gray-300 mb-8">
          DoxaV3 is a decentralized stablecoin built on the Internet Computer,
          offering stability, security, and true decentralization.
        </p>

        <div class="flex space-x-4 hero-buttons">
          <a
            href="https://github.com"
            target="_blank"
            class="group bg-white text-purple-900 px-8 py-3 rounded-full font-medium hover:bg-gray-100 transition-all duration-300 transform hover:scale-105 hover:-rotate-1 flex items-center gap-2"
          >
            View on GitHub
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
            href="#learn-more"
            class="group border border-white text-white px-8 py-3 rounded-full font-medium hover:bg-white hover:text-purple-900 transition-all duration-300 hover:scale-105 hover:rotate-1"
          >
            Learn More
          </a>
        </div>
      </div>

      <!-- Stats Cards -->
      <div class="md:w-1/2 mt-12 md:mt-0 grid grid-cols-2 gap-6 relative">
        <!-- Background Glow -->
        <div
          class="absolute inset-0 bg-gradient-to-br from-purple-500/20 to-pink-500/20 filter blur-3xl"
        ></div>

        <div
          class="stats-card flex flex-col justify-between bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105 hover:rotate-2"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate">Total Value Locked</h3>
            <div class="text-3xl font-bold text-white truncate">${$tvl}M</div>
          </div>
          <div class="text-green-400 flex items-center gap-1 mt-2">
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
          class="stats-card flex flex-col justify-between bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105 hover:rotate-2"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate">APY</h3>
            <div class="text-3xl font-bold text-white truncate">{$apy}%</div>
          </div>
          <div class="text-green-400 mt-2 truncate">↑ 0.5%</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105 hover:rotate-2"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate">Weekly Rewards</h3>
            <div class="text-3xl font-bold text-white truncate">
              125,000 DOXA
            </div>
          </div>
          <div class="mt-2 h-5">&nbsp;</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105 hover:rotate-2"
        >
          <div>
            <h3 class="text-gray-400 mb-2 truncate">Total Fees Collected</h3>
            <div class="text-3xl font-bold text-white truncate">$283.5K</div>
          </div>
          <div class="mt-2 h-5">&nbsp;</div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  /* Removed initial styles for animated elements */
  /* 
  .hero-title,
  .hero-description,
  .hero-buttons,
  .stats-card {
    opacity: 0;
  }
  */

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
      theme("colors.purple.400"),
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
