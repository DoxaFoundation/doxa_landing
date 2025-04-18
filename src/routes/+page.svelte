<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  import Hero from "../components/landing/Hero.svelte";
  // import Features from "../components/landing/Features.svelte";
  // import HowItWorks from "../components/landing/HowItWorks.svelte";
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
    href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class="min-h-screen bg-gradient-to-br from-slate-50 to-slate-200">
  <div class="relative min-h-screen overflow-hidden">
    <!-- Gradient Overlay -->
    <div
      class="absolute inset-0 bg-gradient-to-br from-slate-200/70 via-slate-100/30 to-white/50 z-0"
    ></div>

    <!-- Grid Background with Metallic Effect -->
    <div
      class="grid-background absolute inset-0 z-0 opacity-75 pointer-events-none"
      style="background-size: 40px 40px; background-image: linear-gradient(to right, rgba(169, 169, 169, 0.2) 1px, transparent 1px), linear-gradient(to bottom, rgba(169, 169, 169, 0.2) 1px, transparent 1px);"
    ></div>

    <!-- Background Particles with Metallic Colors -->
    {#each Array(20) as _, i}
      <div
        class="particle absolute h-2 w-2 rounded-full"
        style="
          background: {['#A9A9A9', '#BEBEBE', '#D3D3D3'][i % 3]};
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          filter: blur(1px);
          opacity: 0.6;
          box-shadow: 0 0 8px rgba(255, 255, 255, 0.6);
        "
      />
    {/each}

    <!-- Shooting Stars with Metallic Colors -->
    {#each Array(10) as _, i}
      <div
        class="shooting-star absolute h-px w-20 opacity-30"
        style="
          background: linear-gradient(90deg, {['#A9A9A9', '#BEBEBE', '#D3D3D3'][
          i % 3
        ]}, transparent);
          left: {-Math.random() * 100}%;
          top: {Math.random() * 100}%;
          transform: rotate({Math.random() * 360}deg);
          box-shadow: 0 0 10px rgba(255, 255, 255, 0.8);
        "
      />
    {/each}

    <!-- Metallic Glow Effects -->
    <div
      class="absolute top-1/3 left-1/4 w-96 h-96 rounded-full bg-gradient-to-br from-white/10 to-transparent blur-3xl"
    ></div>
    <div
      class="absolute bottom-1/4 right-1/4 w-80 h-80 rounded-full bg-gradient-to-br from-white/10 to-transparent blur-3xl"
    ></div>

    <!-- Components -->
    {#if componentsReady}
      <div class="relative z-10">
        <Hero {gsap} {ScrollTrigger} />
        <!-- <Features {gsap} {ScrollTrigger} /> -->
        <!-- <HowItWorks {gsap} {ScrollTrigger} /> -->
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
    background: linear-gradient(135deg, var(--color-bg-0), var(--color-bg-1));
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }

  :global(#svelte) {
    background: transparent;
  }

  /* Enhanced metallic grid background */
  .grid-background {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(169, 169, 169, 0.2) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(169, 169, 169, 0.2) 1px, transparent 1px);
    background-position: 0 0;
  }

  .particle {
    will-change: transform;
    transform-style: preserve-3d;
    animation: float 8s infinite ease-in-out;
  }

  .shooting-star {
    will-change: transform;
    transform-style: preserve-3d;
    animation: shooting 6s infinite ease-out;
  }

  @keyframes float {
    0%,
    100% {
      transform: translateY(0) translateX(0) rotate(0deg);
      opacity: 0.6;
    }
    25% {
      opacity: 0.9;
    }
    50% {
      transform: translateY(-20px) translateX(10px) rotate(5deg);
      opacity: 0.4;
    }
    75% {
      opacity: 0.8;
    }
  }

  @keyframes shooting {
    0% {
      transform: translateX(-100vw) translateY(0) rotate(var(--rotation, 0deg));
      opacity: 0;
    }
    10% {
      opacity: 0.7;
    }
    60% {
      opacity: 0.5;
    }
    100% {
      transform: translateX(200vw) translateY(20vh)
        rotate(var(--rotation, 0deg));
      opacity: 0;
    }
  }

  /* Enhanced background grid */
  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(169, 169, 169, 0.2) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(169, 169, 169, 0.2) 1px, transparent 1px);
  }

  /* Enhanced glow animation */
  .hero-glow {
    animation: platinumGlow 6s ease-in-out infinite;
  }

  @keyframes platinumGlow {
    0%,
    100% {
      opacity: 0.5;
      filter: blur(15px);
      transform: scale(1);
    }
    50% {
      opacity: 0.8;
      filter: blur(20px);
      transform: scale(1.2);
    }
  }

  /* Enhanced card hover effects */
  .feature-card {
    transform: translateY(0) scale(1);
    transition: all 0.6s cubic-bezier(0.34, 1.56, 0.64, 1);
    will-change: transform, opacity, box-shadow;
    box-shadow:
      0 4px 12px rgba(0, 0, 0, 0.05),
      0 1px 3px rgba(255, 255, 255, 0.3) inset;
  }

  .feature-card:hover {
    transform: translateY(-10px) scale(1.02) rotate(1deg);
    box-shadow:
      0 20px 40px -15px rgba(0, 0, 0, 0.1),
      0 0 15px rgba(255, 255, 255, 0.5);
  }

  /* More metallic animations */
  .particle {
    animation: metallicFloat 8s infinite ease-in-out;
  }

  @keyframes metallicFloat {
    0%,
    100% {
      opacity: 0.4;
      transform: translateY(0) translateX(0) scale(1);
      filter: blur(1px) brightness(1);
    }
    50% {
      opacity: 0.8;
      transform: translateY(-20px) translateX(10px) scale(1.1);
      filter: blur(0px) brightness(1.2);
    }
  }

  /* Enhanced pulse animation */
  @keyframes platinumPulse {
    0%,
    100% {
      opacity: 0.5;
      transform: scale(1);
      filter: blur(5px) brightness(1);
    }
    50% {
      opacity: 0.8;
      transform: scale(1.1);
      filter: blur(10px) brightness(1.3);
    }
  }

  .animate-pulse {
    animation: platinumPulse 5s infinite;
  }

  /* Enhanced card hover */
  .stats-card {
    transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
    will-change: transform, opacity, box-shadow;
    box-shadow:
      0 4px 12px rgba(0, 0, 0, 0.1),
      0 1px 3px rgba(255, 255, 255, 0.2) inset;
  }

  .stats-card:hover {
    transform: translateY(-10px) rotate(1deg) scale(1.05);
    box-shadow:
      0 20px 40px -15px rgba(0, 0, 0, 0.1),
      0 0 15px rgba(255, 255, 255, 0.4);
  }

  /* Enhanced title effects */
  .hero-title {
    position: relative;
    z-index: 1;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
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
      rgba(169, 169, 169, 0.8),
      transparent
    );
    transform: scaleX(0);
    transform-origin: left;
    animation: lineReveal 1.5s cubic-bezier(0.25, 1, 0.5, 1) forwards;
    animation-delay: 1s;
    box-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
  }

  @keyframes lineReveal {
    to {
      transform: scaleX(1);
    }
  }

  /* Enhanced news cards */
  .news-card {
    transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
    will-change: transform, opacity, box-shadow;
    box-shadow:
      0 4px 12px rgba(0, 0, 0, 0.1),
      0 1px 3px rgba(255, 255, 255, 0.3) inset;
    border: 1px solid rgba(255, 255, 255, 0.3);
    backdrop-filter: blur(8px);
  }

  .news-card:hover {
    transform: translateY(-10px) scale(1.02);
    box-shadow:
      0 20px 40px -15px rgba(0, 0, 0, 0.1),
      0 0 20px rgba(255, 255, 255, 0.4);
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
      rgba(169, 169, 169, 0.8),
      transparent
    );
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.5s ease;
    box-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
  }

  .news-card:hover::after {
    transform: scaleX(1);
  }

  /* Enhanced integration cards */
  .integration-card {
    transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
    will-change: transform, opacity, box-shadow;
    backdrop-filter: blur(8px);
    border: 1px solid rgba(255, 255, 255, 0.3);
    box-shadow:
      0 4px 12px rgba(0, 0, 0, 0.1),
      0 1px 3px rgba(255, 255, 255, 0.3) inset;
  }

  .integration-card:hover {
    transform: translateY(-10px) scale(1.02) rotate(1deg);
    box-shadow:
      0 20px 40px -15px rgba(0, 0, 0, 0.1),
      0 0 20px rgba(255, 255, 255, 0.5);
  }
</style>
