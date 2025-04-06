<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    // Why Choose Section Animation
    const whyChooseTitle = document.querySelector(".why-choose-title");
    if (whyChooseTitle) {
      gsap.from(whyChooseTitle, {
        scrollTrigger: {
          trigger: whyChooseTitle,
          start: "top 80%",
          toggleActions: "play none none reverse",
        },
        duration: 1,
        y: 50,
        opacity: 0,
        ease: "power3.out",
      });
    }

    // Enhanced Feature Cards Animation with Stagger
    const featureCards = document.querySelectorAll(".feature-card");
    featureCards.forEach((card, index) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: "top 80%",
          end: "bottom 20%",
          toggleActions: "play none none reverse",
        },
        duration: 1.2,
        y: 100,
        x: index % 2 === 0 ? -50 : 50,
        opacity: 0,
        rotation: index % 2 === 0 ? -5 : 5,
        delay: index * 0.2,
        ease: "power3.out",
      });
    });
  }
</script>

<section class="py-32 relative overflow-hidden">
  <div class="absolute inset-0 bg-[#0a0118]">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <h2
      class="why-choose-title text-4xl md:text-5xl font-bold text-center text-white mb-16"
    >
      Why Choose <span
        class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-400"
        >DoxaV3</span
      >?
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <!-- Security -->
      <div class="feature-card group">
        <div
          class="relative p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
        >
          <div
            class="absolute inset-0 rounded-2xl bg-gradient-to-br from-purple-600/20 to-pink-600/20 opacity-0 group-hover:opacity-100 transition-opacity duration-500"
          ></div>
          <div class="relative">
            <div
              class="w-12 h-12 bg-gradient-to-br from-purple-500 to-pink-500 rounded-xl mb-6 flex items-center justify-center transform group-hover:scale-110 group-hover:rotate-6 transition-all duration-500"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 text-white"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"
                />
              </svg>
            </div>
            <h3
              class="text-xl font-semibold text-white mb-4 group-hover:text-purple-400 transition-colors"
            >
              Enterprise-Grade Security
            </h3>
            <p
              class="text-gray-400 group-hover:text-gray-300 transition-colors"
            >
              Built on Internet Computer with advanced cryptography and security
              measures to protect your assets.
            </p>
          </div>
        </div>
      </div>

      <!-- Stability -->
      <div class="feature-card group">
        <div
          class="relative p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
        >
          <div
            class="absolute inset-0 rounded-2xl bg-gradient-to-br from-purple-600/20 to-pink-600/20 opacity-0 group-hover:opacity-100 transition-opacity duration-500"
          ></div>
          <div class="relative">
            <div
              class="w-12 h-12 bg-gradient-to-br from-purple-500 to-pink-500 rounded-xl mb-6 flex items-center justify-center transform group-hover:scale-110 group-hover:rotate-6 transition-all duration-500"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 text-white"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"
                />
              </svg>
            </div>
            <h3
              class="text-xl font-semibold text-white mb-4 group-hover:text-purple-400 transition-colors"
            >
              Price Stability
            </h3>
            <p
              class="text-gray-400 group-hover:text-gray-300 transition-colors"
            >
              Advanced algorithmic mechanisms ensure stable value pegging and
              minimal volatility.
            </p>
          </div>
        </div>
      </div>

      <!-- Decentralization -->
      <div class="feature-card group">
        <div
          class="relative p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
        >
          <div
            class="absolute inset-0 rounded-2xl bg-gradient-to-br from-purple-600/20 to-pink-600/20 opacity-0 group-hover:opacity-100 transition-opacity duration-500"
          ></div>
          <div class="relative">
            <div
              class="w-12 h-12 bg-gradient-to-br from-purple-500 to-pink-500 rounded-xl mb-6 flex items-center justify-center transform group-hover:scale-110 group-hover:rotate-6 transition-all duration-500"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 text-white"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9"
                />
              </svg>
            </div>
            <h3
              class="text-xl font-semibold text-white mb-4 group-hover:text-purple-400 transition-colors"
            >
              True Decentralization
            </h3>
            <p
              class="text-gray-400 group-hover:text-gray-300 transition-colors"
            >
              Fully decentralized governance and operations with no central
              points of failure.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(255, 255, 255, 0.1) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(255, 255, 255, 0.1) 1px, transparent 1px);
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
</style>
