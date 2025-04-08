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
  <!-- Gradient Background -->
  <div
    class="absolute inset-0 bg-gradient-to-r from-purple-900 via-purple-800 to-purple-900 opacity-90"
  ></div>

  <!-- Animated Circles -->
  <div class="absolute inset-0">
    <div
      class="cta-circle absolute w-96 h-96 bg-purple-500/20 rounded-full -top-48 -left-48 blur-3xl"
    ></div>
    <div
      class="cta-circle absolute w-96 h-96 bg-purple-700/20 rounded-full -bottom-48 -right-48 blur-3xl"
    ></div>
  </div>

  <div class="relative container mx-auto px-6 text-center">
    <div class="cta-content">
      <h2 class="text-4xl md:text-5xl font-bold text-white mb-8">
        Ready to Join the Future of Finance?
      </h2>
      <p class="text-xl text-gray-300 mb-12 max-w-2xl mx-auto">
        Start using Doxa today and experience the power of decentralized
        stablecoins on the Internet Computer.
      </p>
      <div class="flex flex-col md:flex-row gap-6 justify-center">
        <a
          href="#"
          class="inline-flex items-center justify-center px-8 py-3 bg-white text-purple-900 rounded-full font-medium hover:bg-gray-100 transition-colors group"
        >
          Launch App
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5 ml-2 transform group-hover:translate-x-1 transition-transform"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </a>
        <a
          href="#"
          class="inline-flex items-center justify-center px-8 py-3 border-2 border-white text-white rounded-full font-medium hover:bg-white hover:text-purple-900 transition-colors"
        >
          Read Documentation
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
</style>
