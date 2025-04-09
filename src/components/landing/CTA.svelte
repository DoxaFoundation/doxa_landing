<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    // CTA Section Enhanced Animation
    const ctaContent = document.querySelector(".cta-content");
    if (ctaContent) {
      const ctaTl = gsap.timeline({
        scrollTrigger: {
          trigger: ctaContent,
          start: "top 75%",
          toggleActions: "play none none reverse",
        },
      });

      ctaTl
        .from(ctaContent, {
          duration: 1,
          y: 100,
          opacity: 0,
          ease: "power3.out",
        })
        .from(
          ".cta-content .inline-flex",
          {
            duration: 0.8,
            y: 30,
            opacity: 0,
            stagger: 0.2,
            ease: "back.out(1.7)",
          },
          "-=0.5"
        );

      // Animated circles
      gsap.to(".cta-circle", {
        scale: 1.2,
        opacity: 0.8,
        duration: 2,
        yoyo: true,
        repeat: -1,
        ease: "power1.inOut",
        stagger: {
          each: 0.5,
          from: "random",
        },
      });
    }
  }
</script>

<div class="relative py-20 overflow-hidden">
  <!-- Solid Primary Background -->
  <div class="absolute inset-0 bg-primary-800 opacity-90"></div>

  <!-- Grayscale Animated Circles -->
  <div class="absolute inset-0">
    <div
      class="cta-circle absolute w-96 h-96 bg-primary-500/20 rounded-full -top-48 -left-48 blur-3xl"
    ></div>
    <div
      class="cta-circle absolute w-96 h-96 bg-primary-700/20 rounded-full -bottom-48 -right-48 blur-3xl"
    ></div>
  </div>

  <div class="relative container mx-auto px-6 text-center">
    <div class="cta-content">
      <h2 class="text-4xl font-bold mb-6 text-primary-100">
        Be an Early Minter. Be a Pioneer.
      </h2>
      <p class="text-xl mb-8 text-primary-300">
        This is your chance to help shape the next generation of global finance.
      </p>
      <div
        class="flex flex-col space-y-4 md:flex-row md:space-y-0 md:space-x-6 justify-center cta-buttons"
      >
        <a href="#" class="btn-primary group">
          Launch Doxa Now
          <span class="btn-arrow group-hover:translate-x-1">→</span>
        </a>
        <a href="#" class="btn-secondary group">
          Learn More in Docs
          <span class="btn-arrow group-hover:translate-x-1">→</span>
        </a>
      </div>
    </div>
  </div>
</div>

<style>
  .cta-circle {
    will-change: transform, opacity;
    transform-style: preserve-3d;
  }

  @keyframes pulse {
    0%,
    100% {
      transform: scale(1);
      opacity: 0.2;
    }
    50% {
      transform: scale(1.2);
      opacity: 0.4;
    }
  }

  .cta-content {
    position: relative;
    z-index: 1;
  }

  .inline-flex {
    position: relative;
    overflow: hidden;
  }

  .inline-flex::after {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: linear-gradient(
      to right,
      transparent,
      rgba(255, 255, 255, 0.1),
      transparent
    );
    transform: translateX(-100%);
    transition: transform 0.5s ease;
  }

  .inline-flex:hover::after {
    transform: translateX(100%);
  }

  .cta-buttons a {
    @apply inline-flex items-center justify-center px-8 py-3 rounded-full font-medium transition-all duration-300 transform;
  }

  .btn-primary {
    @apply bg-primary-100 text-primary-900 hover:bg-primary-200 hover:scale-105 hover:-rotate-1;
  }

  .btn-secondary {
    @apply border-2 border-primary-100 text-primary-100 hover:bg-primary-100 hover:text-primary-900 hover:scale-105 hover:rotate-1;
  }

  .btn-arrow {
    @apply ml-2 transition-transform duration-300;
  }
</style>
