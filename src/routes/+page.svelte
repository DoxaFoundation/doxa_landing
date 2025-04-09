<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  import Hero from "../components/landing/Hero.svelte";
  import Features from "../components/landing/Features.svelte";
  import HowItWorks from "../components/landing/HowItWorks.svelte";
  import Roadmap from "../components/landing/Roadmap.svelte";
  import Testimonials from "../components/landing/Testimonials.svelte";
  import Newsletter from "../components/landing/Newsletter.svelte";
  import CTA from "../components/landing/CTA.svelte";

  let componentsReady = false;
  let gsap: any;
  let ScrollTrigger: any;

  onMount(() => {
    if (browser) {
      // Access GSAP from the global window object
      gsap = window.gsap;
      ScrollTrigger = window.ScrollTrigger;

      // Register the ScrollTrigger plugin
      gsap.registerPlugin(ScrollTrigger);

      componentsReady = true;
      initBackgroundAnimations();
    }
  });

  function initBackgroundAnimations() {
    if (!gsap) return;

    // Animated grid background
    gsap.to(".grid-background", {
      backgroundPosition: "40px 40px",
      duration: 20,
      repeat: -1,
      ease: "none",
    });

    // Floating particles
    const particles = document.querySelectorAll(".particle");
    particles.forEach((particle) => {
      gsap.to(particle, {
        x: "random(-100, 100)",
        y: "random(-100, 100)",
        rotation: "random(-180, 180)",
        duration: "random(3, 6)",
        repeat: -1,
        yoyo: true,
        ease: "none",
      });
    });

    // Shooting stars effect
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

<svelte:head>
  <title>Doxa - The Future of Currency</title>
  <meta
    name="description"
    content="Doxa - Create, own, and earn with a revolutionary multi-stablecoin platform."
  />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link
    rel="preconnect"
    href="https://fonts.gstatic.com"
    crossorigin="anonymous"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600;700&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class="min-h-screen bg-gray-900">
  <div class="relative min-h-screen overflow-hidden">
    <!-- Gradient Overlay -->
    <div
      class="absolute inset-0 bg-gradient-to-br from-gray-800/50 to-transparent z-0"
    ></div>

    <!-- Grid Background -->
    <div
      class="grid-background absolute inset-0 z-0 opacity-50 pointer-events-none"
      style="background-size: 40px 40px; background-image: linear-gradient(to right, rgba(204, 204, 204, 0.1) 1px, transparent 1px), linear-gradient(to bottom, rgba(204, 204, 204, 0.1) 1px, transparent 1px);"
    ></div>

    <!-- Background Particles -->
    {#each Array(20) as _, i}
      <div
        class="particle absolute h-2 w-2 rounded-full"
        style="
          background: {['#666666', '#999999', '#4d4d4d'][i % 3]};
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          filter: blur(1px);
          opacity: 0.6;
        "
      />
    {/each}

    <!-- Shooting Stars -->
    {#each Array(10) as _, i}
      <div
        class="shooting-star absolute h-px w-20 opacity-20"
        style="
          background: linear-gradient(90deg, {['#666666', '#999999', '#4d4d4d'][
          i % 3
        ]}, transparent);
          left: {-Math.random() * 100}%;
          top: {Math.random() * 100}%;
          transform: rotate({Math.random() * 360}deg);
        "
      />
    {/each}

    <!-- Components -->
    {#if componentsReady}
      <div class="relative z-10">
        <Hero {gsap} {ScrollTrigger} />
        <Features {gsap} {ScrollTrigger} />
        <HowItWorks {gsap} {ScrollTrigger} />
        <Roadmap {gsap} {ScrollTrigger} />
        <Testimonials {gsap} {ScrollTrigger} />
        <CTA {gsap} {ScrollTrigger} />
        <Newsletter {gsap} {ScrollTrigger} />
      </div>
    {/if}
  </div>
</div>

<style lang="postcss">
  :global(html) {
    scroll-behavior: smooth;
  }

  :global(body) {
    @apply text-gray-200;
    background: #000000;
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }

  :global(#svelte) {
    background: #000000;
  }

  .grid-background {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(204, 204, 204, 0.1) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(204, 204, 204, 0.1) 1px, transparent 1px);
    background-position: 0 0;
  }

  .particle {
    will-change: transform;
    transform-style: preserve-3d;
  }

  .shooting-star {
    will-change: transform;
    transform-style: preserve-3d;
  }

  @keyframes float {
    0%,
    100% {
      transform: translateY(0) translateX(0);
    }
    50% {
      transform: translateY(-20px) translateX(10px);
    }
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

  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(204, 204, 204, 0.1) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(204, 204, 204, 0.1) 1px, transparent 1px);
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

  @keyframes float {
    0%,
    100% {
      transform: translateY(0) translateX(0);
    }
    50% {
      transform: translateY(-20px) translateX(10px);
    }
  }

  .hero-glow {
    animation: glow 3s ease-in-out infinite;
  }

  @keyframes glow {
    0%,
    100% {
      opacity: 0.5;
      transform: scale(1);
    }
    50% {
      opacity: 1;
      transform: scale(1.1);
    }
  }

  .feature-card {
    transform: translateY(0);
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
  }

  .feature-card:hover {
    transform: translateY(-10px) rotate(2deg);
    box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.3);
  }

  .particle {
    animation: float 3s infinite ease-in-out;
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

  .stats-card {
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
  }

  .stats-card:hover {
    transform: translateY(-10px) rotate(2deg) scale(1.05);
    box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.3);
  }

  .hero-title {
    position: relative;
    z-index: 1;
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
      theme("colors.gray.400"),
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

  .news-card {
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
  }

  .news-card:hover {
    transform: translateY(-10px) scale(1.02);
    box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.3);
  }

  .news-card::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(
      to right,
      transparent,
      theme("colors.gray.400"),
      transparent
    );
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.5s ease;
  }

  .news-card:hover::after {
    transform: scaleX(1);
  }

  .integration-card {
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
  }

  .integration-card:hover {
    transform: translateY(-10px) scale(1.02) rotate(1deg);
    box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.3);
  }
</style>
