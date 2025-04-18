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

  let heroSection: HTMLElement;
  let titleElement: HTMLElement;
  let subtitleElement: HTMLElement;
  let ctaButton: HTMLElement;
  let heroImage: HTMLElement;
  let particlesContainer: HTMLElement;

  const NUM_PARTICLES = 40;

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

    if (!gsap) return;

    // Create a captivating entrance animation
    const tl = gsap.timeline({ defaults: { ease: "power3.out" } });

    // Staggered elements entrance
    tl.from(titleElement, {
      y: 80,
      opacity: 0,
      duration: 1.2,
    })
      .from(
        subtitleElement,
        {
          y: 60,
          opacity: 0,
          duration: 1,
        },
        "-=0.8"
      )
      .from(
        ctaButton,
        {
          y: 40,
          opacity: 0,
          scale: 0.9,
          duration: 0.8,
        },
        "-=0.6"
      )
      .from(
        heroImage,
        {
          y: 100,
          opacity: 0,
          rotationY: 15,
          transformPerspective: 1000,
          duration: 1.4,
        },
        "-=1"
      );

    // Animate the 3D tilt effect based on mouse movement
    if (heroSection) {
      heroSection.addEventListener("mousemove", (e) => {
        if (!titleElement || !heroImage) return;

        const mouseX = e.clientX / window.innerWidth - 0.5;
        const mouseY = e.clientY / window.innerHeight - 0.5;

        gsap.to(titleElement, {
          rotationY: mouseX * 10,
          rotationX: -mouseY * 10,
          transformPerspective: 900,
          duration: 0.4,
        });

        gsap.to(heroImage, {
          rotationY: mouseX * 20,
          rotationX: -mouseY * 5,
          transformPerspective: 1000,
          duration: 0.6,
        });
      });
    }

    // Animate the particles
    if (particlesContainer) {
      const particles = particlesContainer.querySelectorAll(".particle");

      particles.forEach((particle, i) => {
        const delay = i * 0.05;
        const duration = 10 + Math.random() * 20;

        gsap.set(particle, {
          x: Math.random() * window.innerWidth,
          y: Math.random() * window.innerHeight,
          opacity: Math.random() * 0.6 + 0.2,
        });

        gsap.to(particle, {
          x: "+=" + (Math.random() * 200 - 100),
          y: "+=" + (Math.random() * 200 - 100),
          opacity: Math.random() * 0.6 + 0.2,
          duration: duration,
          delay: delay,
          repeat: -1,
          yoyo: true,
          ease: "sine.inOut",
        });
      });
    }

    // Subtle breathing animation for the whole hero
    gsap.to(heroSection, {
      backgroundPosition: "100% 50%",
      duration: 15,
      repeat: -1,
      yoyo: true,
      ease: "sine.inOut",
    });
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
  bind:this={heroSection}
  class="hero-section relative min-h-screen flex items-center justify-center py-24 overflow-hidden"
  style="background: linear-gradient(135deg, rgba(229,228,226,0.9), rgba(245,245,245,0.9)); background-size: 200% 200%;"
>
  <!-- Particle system -->
  <div
    bind:this={particlesContainer}
    class="absolute inset-0 overflow-hidden pointer-events-none"
  >
    {#each Array(NUM_PARTICLES) as _, i}
      <div
        class="particle absolute rounded-full shadow-md"
        style="
          width: {Math.random() * 12 + 4}px; 
          height: {Math.random() * 12 + 4}px;
          background: linear-gradient(135deg, rgba(169,169,169,{Math.random() *
          0.5 +
          0.3}), rgba(192,192,192,{Math.random() * 0.3 + 0.2}));
          filter: blur({Math.random() * 2}px);
          transform-style: preserve-3d;
        "
      ></div>
    {/each}
  </div>

  <!-- Decorative gradient circles -->
  <div
    class="absolute top-0 left-0 w-3/4 h-3/4 rounded-full bg-gradient-to-br from-white/30 to-transparent -translate-x-1/4 -translate-y-1/4 blur-3xl pointer-events-none"
  ></div>
  <div
    class="absolute bottom-0 right-0 w-1/2 h-2/3 rounded-full bg-gradient-to-tl from-slate-200/60 to-transparent translate-x-1/4 translate-y-1/3 blur-3xl pointer-events-none"
  ></div>
  <div
    class="absolute top-1/4 right-1/4 w-64 h-64 rounded-full bg-gradient-to-bl from-white/40 to-transparent blur-3xl pointer-events-none"
  ></div>

  <div
    class="container mx-auto px-6 z-10 flex flex-col lg:flex-row items-center justify-between gap-12"
  >
    <!-- Text content -->
    <div class="w-full lg:w-1/2 max-w-2xl">
      <h1
        bind:this={titleElement}
        class="text-5xl md:text-7xl font-bold mb-8 leading-tight gradient-text text-shadow-sm transform-gpu"
        style="transform-style: preserve-3d;"
      >
        <span class="block">The Future of</span>
        <span class="relative inline-block">
          <span class="relative z-10 pr-2">Currency</span>
          <span
            class="absolute bottom-2 left-0 h-4 w-full bg-gradient-to-r from-slate-300/60 via-slate-400/40 to-slate-300/60 -skew-y-3 -z-10 blur-sm"
          ></span>
        </span>
      </h1>

      <p
        bind:this={subtitleElement}
        class="text-xl md:text-2xl text-gray-700 mb-12 max-w-xl"
      >
        Create, own, and earn with Doxa's revolutionary
        <span class="font-semibold relative"
          >multi-stablecoin
          <span
            class="absolute bottom-0 left-0 w-full h-1 bg-gradient-to-r from-slate-400/70 via-slate-500/50 to-slate-400/70"
          ></span>
        </span>
        platform.
      </p>
    </div>

    <!-- Hero visual -->
    <div
      bind:this={heroImage}
      class="w-full lg:w-1/2 card-3d p-6 transform-gpu"
      style="transform-style: preserve-3d;"
    >
      <div class="card-3d-inner relative">
        <!-- Main circle -->
        <div
          class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 rounded-full bg-gradient-to-br from-slate-300 to-slate-400 blur-sm"
        ></div>

        <!-- Floating coin mockups -->
        <div
          class="coin absolute top-1/4 left-1/3 w-36 h-36 rounded-full bg-gradient-to-br from-slate-100 via-slate-200 to-slate-300 flex items-center justify-center transform-gpu"
          style="filter: drop-shadow(0 10px 15px rgba(0, 0, 0, 0.15));"
        >
          <!-- Inner coin -->
          <div
            class="w-28 h-28 rounded-full bg-gradient-radial from-slate-100 via-slate-200 to-slate-300 flex items-center justify-center relative overflow-hidden"
          >
            <!-- Currency symbol -->
            <div class="text-6xl font-medium text-gray-700">$</div>
          </div>
        </div>

        <div
          class="coin absolute top-1/2 right-1/4 w-28 h-28 rounded-full bg-gradient-to-br from-slate-200 via-slate-300 to-slate-400 flex items-center justify-center transform-gpu"
          style="filter: drop-shadow(0 8px 12px rgba(0, 0, 0, 0.12));"
        >
          <!-- Inner coin -->
          <div
            class="w-20 h-20 rounded-full bg-gradient-radial from-slate-200 via-slate-300 to-slate-400 flex items-center justify-center relative overflow-hidden"
          >
            <!-- Currency symbol -->
            <div class="text-5xl font-medium text-gray-700">€</div>
          </div>
        </div>

        <div
          class="coin absolute bottom-1/3 left-1/4 w-24 h-24 rounded-full bg-gradient-to-br from-slate-300 via-slate-400 to-slate-500 flex items-center justify-center transform-gpu"
          style="filter: drop-shadow(0 6px 10px rgba(0, 0, 0, 0.1));"
        >
          <!-- Inner coin -->
          <div
            class="w-16 h-16 rounded-full bg-gradient-radial from-slate-300 via-slate-400 to-slate-500 flex items-center justify-center relative overflow-hidden"
          >
            <!-- Currency symbol -->
            <div class="text-4xl font-medium text-white/90">£</div>
          </div>
        </div>

        <!-- Add small decorative coins in the background for depth -->
        <div
          class="coin absolute top-[15%] right-[15%] w-16 h-16 rounded-full bg-gradient-to-br from-slate-400 via-slate-500 to-slate-600 opacity-30 transform-gpu rotate-12"
        ></div>
        <div
          class="coin absolute bottom-[20%] right-[30%] w-12 h-12 rounded-full bg-gradient-to-br from-slate-200 via-slate-300 to-slate-400 opacity-20 transform-gpu -rotate-12"
        ></div>

        <!-- Connection lines -->
        <svg
          class="absolute inset-0 w-full h-full"
          viewBox="0 0 100 100"
          xmlns="http://www.w3.org/2000/svg"
        >
          <line
            x1="33"
            y1="25"
            x2="75"
            y2="50"
            stroke="rgba(211,211,211,0.5)"
            stroke-width="0.3"
          ></line>
          <line
            x1="33"
            y1="25"
            x2="25"
            y2="67"
            stroke="rgba(211,211,211,0.5)"
            stroke-width="0.3"
          ></line>
          <line
            x1="25"
            y1="67"
            x2="75"
            y2="50"
            stroke="rgba(211,211,211,0.5)"
            stroke-width="0.3"
          ></line>
        </svg>
      </div>
    </div>
  </div>
</div>

<style>
  .hero-section {
    perspective: 1000px;
  }

  .gradient-text {
    background: linear-gradient(90deg, #5a5a5a, #444444);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }

  .button {
    background: linear-gradient(135deg, #5a5a5a, #444444);
    color: white;
    font-weight: 600;
    padding: 12px 24px;
    border-radius: 8px;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }

  .button:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
  }

  .coin {
    transition: transform 0.5s ease;
    animation: float 5s infinite ease-in-out;
    transform-style: preserve-3d;
    will-change: transform;
    box-shadow:
      0 10px 30px rgba(0, 0, 0, 0.15),
      0 0 0 1px rgba(255, 255, 255, 0.1);
  }

  .coin:nth-child(2) {
    animation-delay: 0.5s;
    animation-duration: 6s;
  }

  .coin:nth-child(3) {
    animation-delay: 1s;
    animation-duration: 7s;
  }

  @keyframes float {
    0%,
    100% {
      transform: translateY(0) translateZ(0) rotateY(0deg);
    }
    25% {
      transform: translateY(-8px) translateZ(10px) rotateY(5deg);
    }
    50% {
      transform: translateY(-15px) translateZ(20px) rotateY(10deg);
    }
    75% {
      transform: translateY(-8px) translateZ(10px) rotateY(5deg);
    }
  }

  @keyframes shine {
    0% {
      background-position: -100% 0;
    }
    100% {
      background-position: 200% 0;
    }
  }

  /* Coin styling improvements */
  .coin:hover {
    transform: translateY(-10px) scale(1.05) rotateY(15deg);
    transition: transform 0.3s ease-out;
    animation-play-state: paused;
    z-index: 50;
  }

  /* Enhanced coin inner style with metallic texture */
  .coin::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: repeating-linear-gradient(
      90deg,
      rgba(255, 255, 255, 0.03) 0px,
      rgba(255, 255, 255, 0.05) 1px,
      rgba(255, 255, 255, 0.03) 2px
    );
    border-radius: 50%;
    opacity: 0.5;
    mix-blend-mode: overlay;
  }

  /* Coin ring shine animation */
  .coin::after {
    content: "";
    position: absolute;
    top: -5%;
    left: -100%;
    width: 300%;
    height: 10%;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(255, 255, 255, 0.2),
      transparent
    );
    transform: rotate(30deg);
    animation: shine 8s infinite linear;
  }

  .text-shadow-sm {
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .stat {
    position: relative;
    overflow: hidden;
    padding: 8px;
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.4);
    backdrop-filter: blur(4px);
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
    transition:
      transform 0.3s ease,
      box-shadow 0.3s ease;
  }

  .stat:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08);
  }
</style>
