<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  // Helper map for background element colors
  const bgElColors: Record<number, string> = {
    500: "#666666",
    600: "#4d4d4d",
    700: "#333333",
  };

  // Function to generate rgba background gradient string from hex
  function getBgElGradient(index: number): string {
    const shade = ((index % 3) + 5) * 100; // 500, 600, 700
    const hex = bgElColors[shade];
    if (!hex) return "none"; // Fallback
    const r = parseInt(hex.slice(1, 3), 16);
    const g = parseInt(hex.slice(3, 5), 16);
    const b = parseInt(hex.slice(5, 7), 16);
    // Generate radial gradient with 10% opacity color
    return `radial-gradient(circle, rgba(${r}, ${g}, ${b}, 0.1) 0%, transparent 70%)`;
  }

  const newsItems = [
    {
      title: "Doxa: The First Algorithmic Stablecoin on Internet Computer",
      date: "Jan 20, 2025",
      link: "/news/first-algorithmic-stablecoin",
    },
    {
      title: "How Doxa Maintains Price Stability Through Smart Contracts",
      date: "Jan 15, 2025",
      link: "/news/price-stability",
    },
    {
      title: "Doxa Partners with Major DeFi Protocols",
      date: "Jan 10, 2025",
      link: "/news/defi-protocols",
    },
    {
      title: "The Future of Stablecoins on Internet Computer",
      date: "Jan 5, 2025",
      link: "/news/future-stablecoins",
    },
  ];

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    // Latest News Section Animation with Enhanced Effects
    const newsSection = document.querySelector(".news-section-title");
    if (newsSection) {
      gsap.from(newsSection, {
        scrollTrigger: {
          trigger: newsSection,
          start: "top 80%",
          toggleActions: "play none none reverse",
        },
        duration: 1,
        y: 50,
        opacity: 0,
        ease: "power3.out",
      });
    }

    // Enhanced News Cards Animation
    const newsCards = document.querySelectorAll(".news-card");
    newsCards.forEach((card, index) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: "top 85%",
          toggleActions: "play none none reverse",
        },
        duration: 1.2,
        y: 100,
        x: index % 2 === 0 ? -50 : 50,
        opacity: 0,
        rotation: index % 2 === 0 ? -5 : 5,
        delay: index * 0.2,
        ease: "back.out(1.7)",
      });
    });
  }
</script>

<section class="py-32 relative overflow-hidden">
  <div class="absolute inset-0 bg-primary-900">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
    <!-- Animated Background Elements (Grayscale) -->
    {#each Array(10) as _, i}
      <div
        class="absolute h-32 w-32 rounded-full"
        style="
          background: {getBgElGradient(i)};
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          transform: scale({0.5 + Math.random()});
          animation: float {5 + Math.random() * 5}s infinite ease-in-out;
        "
      ></div>
    {/each}
  </div>

  <div class="relative container mx-auto px-6">
    <div class="flex justify-between items-center mb-16">
      <h2
        class="news-section-title text-4xl md:text-5xl font-bold text-primary-100 relative"
      >
        Latest <span
          class="text-transparent bg-clip-text bg-gradient-to-r from-primary-300 to-primary-100"
          >Updates</span
        >
        <div
          class="absolute -bottom-2 left-0 w-1/3 h-1 bg-gradient-to-r from-primary-400 to-transparent"
        ></div>
      </h2>
      <a
        href="/news"
        class="group flex items-center gap-2 text-primary-100 hover:text-primary-300 transition-colors relative overflow-hidden"
      >
        <span class="relative z-10">View All</span>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 transform group-hover:translate-x-1 transition-transform relative z-10"
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
        <div
          class="absolute inset-0 bg-primary-500/10 translate-x-[-100%] group-hover:translate-x-0 transition-transform duration-300"
        ></div>
      </a>
    </div>

    <div class="news-content">
      <h2 class="text-3xl font-bold mb-4 text-primary-100">
        Transparent. Auditable. Decentralized.
      </h2>
      <div
        class="news-grid grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6"
      >
        <div
          class="news-card p-6 rounded-lg bg-primary-800/40 border border-primary-600/50"
        >
          <div class="news-icon text-3xl mb-3 text-primary-300">🧾</div>
          <h3 class="news-title text-lg font-medium text-primary-100">
            Real-Time Reserve Dashboards
          </h3>
        </div>
        <div
          class="news-card p-6 rounded-lg bg-primary-800/40 border border-primary-600/50"
        >
          <div class="news-icon text-3xl mb-3 text-primary-300">🔐</div>
          <h3 class="news-title text-lg font-medium text-primary-100">
            Regular Security Audits
          </h3>
        </div>
        <div
          class="news-card p-6 rounded-lg bg-primary-800/40 border border-primary-600/50"
        >
          <div class="news-icon text-3xl mb-3 text-primary-300">📖</div>
          <h3 class="news-title text-lg font-medium text-primary-100">
            Open-Source Smart Contracts
          </h3>
        </div>
        <div
          class="news-card p-6 rounded-lg bg-primary-800/40 border border-primary-600/50"
        >
          <div class="news-icon text-3xl mb-3 text-primary-300">💼</div>
          <h3 class="news-title text-lg font-medium text-primary-100">
            DAO Governance via SNS
          </h3>
        </div>
      </div>
      <p class="text-lg mt-8 text-primary-400">
        You deserve to see what backs your money. With Doxa, you do.
      </p>
    </div>
  </div>
</section>

<style>
  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        theme("colors.primary.700 / 10%") 1px,
        transparent 1px
      ),
      linear-gradient(
        to bottom,
        theme("colors.primary.700 / 10%") 1px,
        transparent 1px
      );
  }

  @keyframes float {
    0%,
    100% {
      transform: translateY(0) translateX(0) scale(var(--scale));
    }
    50% {
      transform: translateY(-20px) translateX(10px) scale(var(--scale));
    }
  }

  .news-card {
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    will-change: transform, opacity;
  }

  .news-card:hover {
    transform: translateY(-10px) scale(1.02);
    box-shadow: 0 20px 40px -15px theme("colors.primary.900 / 30%");
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
      theme("colors.primary.400"),
      transparent
    );
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.5s ease;
  }

  .news-card:hover::after {
    transform: scaleX(1);
  }
</style>
