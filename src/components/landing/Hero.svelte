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

  // Helper map for particle colors
  const particlePrimaryColors: Record<number, string> = {
    300: "#cccccc",
    400: "#999999",
    500: "#666666",
    600: "#4d4d4d",
    700: "#333333",
  };

  // Function to generate rgba shadow string from hex
  function getParticleShadow(index: number): string {
    const shade = ((index % 5) + 3) * 100; // 300, 400, 500, 600, 700
    const hex = particlePrimaryColors[shade];
    if (!hex) return "none"; // Fallback
    const r = parseInt(hex.slice(1, 3), 16);
    const g = parseInt(hex.slice(3, 5), 16);
    const b = parseInt(hex.slice(5, 7), 16);
    return `0 0 8px 2px rgba(${r}, ${g}, ${b}, 0.5)`; // 50% opacity
  }

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
  class="relative min-h-screen overflow-hidden bg-primary-800 text-primary-100 font-space-grotesk flex items-center"
>
  <!-- Grid Background Removed as app.css handles background -->
  <!-- <div class="grid-background absolute inset-0 z-0 opacity-30 pointer-events-none"></div> -->

  <!-- Hero Section -->
  <div class="container mx-auto px-6 py-20 relative">
    <!-- Animated Particles with grayscale effect -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      {#each Array(25) as _, i}
        {@const grayClassName = `primary-${((i % 5) + 3) * 100}`}
        <div
          class="particle absolute rounded-full bg-{grayClassName}"
          style="
            left: {Math.random() * 100}%;
            top: {Math.random() * 100}%;
            height: {Math.random() * 3 + 1}px;
            width: {Math.random() * 3 + 1}px;
            filter: blur({Math.random() * 2 + 1}px);
            opacity: {Math.random() * 0.6 + 0.2};
            box-shadow: {getParticleShadow(i)};
          "
        />
      {/each}
    </div>

    <div class="flex flex-col md:flex-row items-center gap-10">
      <div class="md:w-1/2 relative flex flex-col justify-center">
        <!-- Dark Gray Orbs -->
        <div
          class="absolute -left-20 -top-20 w-64 h-64 bg-primary-500/10 rounded-full filter blur-3xl animate-pulse"
        ></div>
        <div
          class="absolute right-0 bottom-0 w-40 h-40 bg-primary-300/10 rounded-full filter blur-3xl animate-pulse"
          style="animation-delay: 1s;"
        ></div>
        <div
          class="absolute left-40 top-20 w-20 h-20 bg-primary-600/10 rounded-full filter blur-3xl animate-pulse"
          style="animation-delay: 2s;"
        ></div>

        <div
          class="relative z-10 backdrop-blur-sm bg-primary-900/40 p-8 rounded-3xl border border-primary-500/20"
        >
          <h1
            class="hero-title text-5xl md:text-7xl font-bold text-primary-100 mb-6 leading-tight relative"
          >
            <span
              class="relative inline-block transform hover:scale-105 transition-transform duration-500"
            >
              <span
                class="text-transparent bg-clip-text bg-gradient-to-r from-primary-100 via-primary-300 to-primary-400"
                >Doxa</span
              >
              <span
                class="absolute inset-0 bg-gradient-to-r from-primary-100 via-primary-300 to-primary-400 filter blur-xl opacity-30 animate-pulse"
              ></span>
            </span>
            <span class="block md:inline relative">
              <span class="relative z-10">The</span>
              <span class="relative z-10 ml-2 font-extrabold">future</span>
              <span class="relative z-10 ml-2">of</span>
              <span
                class="relative z-10 ml-2 text-transparent bg-clip-text bg-gradient-to-br from-primary-200 to-primary-400"
                >Currency</span
              >
              <span
                class="absolute bottom-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-primary-400 to-transparent opacity-70"
              ></span>
            </span>
          </h1>

          <h2
            class="hero-subheadline text-2xl md:text-3xl mb-6 text-primary-200/90 font-semibold text-center mt-2"
          >
            <span
              class="bg-gradient-to-r from-primary-300 to-primary-400 bg-clip-text text-transparent"
              >Create</span
            >
            •
            <span
              class="bg-gradient-to-r from-primary-400 to-primary-500 bg-clip-text text-transparent"
              >Own</span
            >
            •
            <span
              class="bg-gradient-to-r from-primary-500 to-primary-300 bg-clip-text text-transparent"
              >Earn</span
            >
          </h2>

          <p
            class="hero-description text-xl text-primary-200/90 mb-10 max-w-xl mx-auto text-center mt-2 backdrop-blur-sm py-3 px-6 rounded-xl border border-primary-400/20 shadow-lg shadow-primary-400/5"
          >
            A revolutionary multi-stablecoin platform powered by Doxa USD
          </p>

          <div
            class="hero-buttons flex flex-col space-y-4 md:flex-row md:space-y-0 md:space-x-6 justify-center"
          >
            <a
              href="#"
              class="group bg-primary-500 text-primary-100 px-8 py-4 rounded-full font-medium hover:bg-primary-400 transition-all duration-300 transform hover:scale-105 hover:-rotate-1 flex items-center gap-2 shadow-lg shadow-primary-500/20"
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
              class="group bg-transparent border-2 border-primary-400/50 text-primary-100 px-8 py-3.5 rounded-full font-medium hover:bg-primary-400/10 hover:border-primary-400 transition-all duration-300 hover:scale-105 hover:rotate-1 backdrop-blur-sm shadow-lg shadow-primary-400/10"
            >
              Read Whitepaper
            </a>
          </div>
        </div>
      </div>

      <!-- Stats Cards -->
      <div class="md:w-1/2 mt-16 md:mt-0 grid grid-cols-2 gap-6 relative">
        <!-- Removed Background Glow div, using card shadows -->
        <!-- <div class="absolute inset-0 bg-gradient-to-br from-[#ff00ff]/10 via-[#7000ff]/10 to-[#00ffff]/10 filter blur-3xl"></div> -->

        <div
          class="stats-card flex flex-col justify-between bg-primary-900/50 backdrop-blur-xl p-6 rounded-2xl border border-primary-500/30 hover:border-primary-500/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-primary-500/10"
        >
          <div>
            <h3 class="text-primary-400 mb-2 truncate font-medium">
              Total Value Locked
            </h3>
            <div class="text-3xl font-bold text-primary-100 truncate">
              ${$tvl.toFixed(1)}M
            </div>
          </div>
          <div class="text-primary-300 flex items-center gap-1 mt-2">
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
          class="stats-card flex flex-col justify-between bg-primary-900/50 backdrop-blur-xl p-6 rounded-2xl border border-primary-400/30 hover:border-primary-400/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-primary-400/10"
        >
          <div>
            <h3 class="text-primary-300 mb-2 truncate font-medium">APY</h3>
            <div class="text-3xl font-bold text-primary-100 truncate">
              {$apy.toFixed(1)}%
            </div>
          </div>
          <div class="text-primary-300 mt-2 truncate">↑ 0.5%</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-primary-900/50 backdrop-blur-xl p-6 rounded-2xl border border-primary-600/30 hover:border-primary-600/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-primary-600/10"
        >
          <div>
            <h3 class="text-primary-500 mb-2 truncate font-medium">
              Weekly Rewards
            </h3>
            <div class="text-3xl font-bold text-primary-100 truncate">
              125,000 DOXA
            </div>
          </div>
          <div class="mt-2 h-5">&nbsp;</div>
        </div>

        <div
          class="stats-card flex flex-col justify-between bg-primary-900/50 backdrop-blur-xl p-6 rounded-2xl border border-primary-500/30 hover:border-primary-500/70 transition-all duration-300 transform hover:scale-105 hover:rotate-2 shadow-lg shadow-primary-500/10"
        >
          <div>
            <h3 class="text-primary-400 mb-2 truncate font-medium">
              Total Fees Collected
            </h3>
            <div class="text-3xl font-bold text-primary-100 truncate">
              $283.5K
            </div>
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
      theme("colors.primary.400"),
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
