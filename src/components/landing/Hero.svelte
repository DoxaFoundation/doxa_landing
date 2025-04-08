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
  class="relative min-h-screen overflow-hidden bg-gradient-to-br from-[#0f0514] via-[#1a0933] to-[#0a0118] text-white font-space-grotesk flex items-center"
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
            background: {['#ff00ff', '#00ffff', '#7000ff', '#ff2a6d', '#01ffc3'][i % 5]};
            left: {Math.random() * 100}%;
            top: {Math.random() * 100}%;
            height: {Math.random() * 3 + 1}px;
            width: {Math.random() * 3 + 1}px;
            filter: blur({Math.random() * 2 + 1}px);
            opacity: {Math.random() * 0.6 + 0.2};
            box-shadow: 0 0 8px 2px {['#ff00ff', '#00ffff', '#7000ff', '#ff2a6d', '#01ffc3'][i % 5]};
          "
        />
      {/each}
    </div>

    <div class="flex flex-col md:flex-row items-center gap-10">
      <div class="md:w-1/2 relative flex flex-col justify-center">
        <!-- Dark Neon Orbs -->
        <div
          class="absolute -left-20 -top-20 w-64 h-64 bg-[#ff00ff]/10 rounded-full filter blur-3xl animate-pulse"
        ></div>
        <div
          class="absolute right-0 bottom-0 w-40 h-40 bg-[#00ffff]/10 rounded-full filter blur-3xl animate-pulse"
          style="animation-delay: 1s;"
        ></div>
        <div
          class="absolute left-40 top-20 w-20 h-20 bg-[#7000ff]/10 rounded-full filter blur-3xl animate-pulse"
          style="animation-delay: 2s;"
        ></div>

        <div class="relative z-10 backdrop-blur-sm bg-black/40 p-8 rounded-3xl border border-[#ff00ff]/20">
          <h1
            class="hero-title text-5xl md:text-7xl font-bold text-white mb-6 leading-tight relative"
          >
            <span class="relative inline-block transform hover:scale-105 transition-transform duration-500">
              <span
                class="text-transparent bg-clip-text bg-gradient-to-r from-[#ff00ff] via-[#ff2a6d] to-[#ff9500]"
                >Doxa</span
              >
              <span
                class="absolute inset-0 bg-gradient-to-r from-[#ff00ff] via-[#ff2a6d] to-[#ff9500] filter blur-xl opacity-30 animate-pulse"
              ></span>
            </span>
            <span class="block md:inline relative">
              <span class="relative z-10">The</span>
              <span class="relative z-10 ml-2 font-extrabold">future</span>
              <span class="relative z-10 ml-2">of</span>
              <span class="relative z-10 ml-2 text-transparent bg-clip-text bg-gradient-to-br from-[#00ffff] to-[#01ffc3]">Currency</span>
              <span class="absolute bottom-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-[#ff00ff] to-transparent opacity-70"></span>
            </span>
          </h1>

          <h2
            class="hero-subheadline text-2xl md:text-3xl mb-6 text-gray-200/90 font-semibold text-center mt-2"
          >
            <span class="bg-gradient-to-r from-[#ff2a6d] to-[#00ffff] bg-clip-text text-transparent">Create</span> • 
            <span class="bg-gradient-to-r from-[#00ffff] to-[#7000ff] bg-clip-text text-transparent">Own</span> • 
            <span class="bg-gradient-to-r from-[#7000ff] to-[#ff2a6d] bg-clip-text text-transparent">Earn</span>
          </h2>

          <p class="hero-description text-xl text-gray-200/90 mb-10 max-w-xl mx-auto text-center mt-2 backdrop-blur-sm py-3 px-6 rounded-xl border border-[#00ffff]/20 shadow-lg shadow-[#00ffff]/5">
            A revolutionary multi-stablecoin platform powered by Doxa USD
          </p>

          <div
            class="hero-buttons flex flex-col space-y-4 md:flex-row md:space-y-0 md:space-x-6 justify-center"
          >
            <a
              href="#"
              class="group bg-gradient-to-r from-[#ff00ff] to-[#7000ff] text-white px-8 py-4 rounded-full font-medium hover:from-[#ff2a6d] hover:to-[#9000ff] transition-all duration-300 transform hover:scale-105 hover:-rotate-1 flex items-center gap-2 shadow-lg shadow-[#ff00ff]/20"
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
              class="group bg-transparent border-2 border-[#00ffff]/50 text-white px-8 py-3.5 rounded-full font-medium hover:bg-[#00ffff]/10 hover:border-[#00ffff] transition-all duration-300 hover:scale-105 hover:rotate-1 backdrop-blur-sm shadow-lg shadow-[#00ffff]/10"
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
          class="absolute inset-0 bg-gradient-to-br from-[#ff00ff]/10 via-[#7000ff]/10 to-[#00ffff]/10 filter blur-3xl"
        ></div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-[#ff00ff]/30 hover:border-[#ff00ff]/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-[#ff00ff]/10"
        >
          <div>
            <h3 class="text-[#ff00ff] mb-2 truncate font-medium">Total Value Locked</h3>
            <div class="text-3xl font-bold text-white truncate">
              ${$tvl.toFixed(1)}M
            </div>
          </div>
          <div class="text-[#01ffc3] flex items-center gap-1 mt-2">
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
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-[#00ffff]/30 hover:border-[#00ffff]/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-[#00ffff]/10"
        >
          <div>
            <h3 class="text-[#00ffff] mb-2 truncate font-medium">APY</h3>
            <div class="text-3xl font-bold text-white truncate">
              {$apy.toFixed(1)}%
            </div>
          </div>
          <div class="text-[#01ffc3] mt-2 truncate">↑ 0.5%</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-[#7000ff]/30 hover:border-[#7000ff]/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-[#7000ff]/10"
        >
          <div>
            <h3 class="text-[#7000ff] mb-2 truncate font-medium">Weekly Rewards</h3>
            <div class="text-3xl font-bold text-white truncate">
              125,000 DOXA
            </div>
          </div>
          <div class="mt-2 h-5">&nbsp;</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-black/50 backdrop-blur-xl p-6 rounded-2xl border border-[#ff2a6d]/30 hover:border-[#ff2a6d]/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-[#ff2a6d]/10"
        >
          <div>
            <h3 class="text-[#ff2a6d] mb-2 truncate font-medium">Total Fees Collected</h3>
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
