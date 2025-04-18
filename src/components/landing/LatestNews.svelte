<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  interface NewsItem {
    title: string;
    date: string;
    link: string;
  }

  interface Circle {
    size: number;
    left: number;
    top: number;
    delay: number;
    duration: number;
  }

  const newsItems: NewsItem[] = [
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

  let circles: Circle[] = [];

  onMount(() => {
    // Create animated background circles
    for (let i = 0; i < 8; i++) {
      circles.push({
        size: Math.random() * 300 + 100,
        left: Math.random() * 100,
        top: Math.random() * 100,
        delay: Math.random() * 5,
        duration: Math.random() * 10 + 15,
      });
    }

    initAnimations();
  });

  function initAnimations() {
    // Enhanced headline animation
    const newsSection = document.querySelector(".news-section-title");
    if (newsSection) {
      gsap.from(newsSection, {
        scrollTrigger: {
          trigger: newsSection,
          start: "top 80%",
          toggleActions: "play none none reverse",
        },
        duration: 1.2,
        y: 80,
        opacity: 0,
        ease: "power4.out",
      });
    }

    // Enhanced News Cards Animation with 3D effect
    const newsCards = document.querySelectorAll(".news-card");
    newsCards.forEach((card, index) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: "top 85%",
          toggleActions: "play none none reverse",
        },
        duration: 1.5,
        y: 120,
        x: index % 2 === 0 ? -60 : 60,
        opacity: 0,
        rotationY: index % 2 === 0 ? -10 : 10,
        rotationX: 5,
        transformPerspective: 1000,
        delay: index * 0.15,
        ease: "power3.out",
      });
    });

    // Add hover effects to cards
    newsCards.forEach((card) => {
      card.addEventListener("mousemove", (e: Event) => {
        const mouseEvent = e as MouseEvent;
        const rect = card.getBoundingClientRect();
        const x = mouseEvent.clientX - rect.left;
        const y = mouseEvent.clientY - rect.top;

        const centerX = rect.width / 2;
        const centerY = rect.height / 2;

        const rotateX = (y - centerY) / 20;
        const rotateY = (centerX - x) / 20;

        gsap.to(card, {
          rotateX: rotateX,
          rotateY: rotateY,
          transformPerspective: 1000,
          duration: 0.5,
          ease: "power1.out",
        });
      });

      card.addEventListener("mouseleave", () => {
        gsap.to(card, {
          rotateX: 0,
          rotateY: 0,
          duration: 0.8,
          ease: "elastic.out(1, 0.5)",
        });
      });
    });
  }
</script>

<section class="relative py-24 overflow-hidden">
  <!-- Advanced animated background -->
  <div class="animated-bg">
    {#each circles as circle}
      <div
        class="animated-bg-circle absolute"
        style="
          width: {circle.size}px; 
          height: {circle.size}px; 
          left: {circle.left}%; 
          top: {circle.top}%; 
          animation-delay: {circle.delay}s;
          animation-duration: {circle.duration}s;
        "
      ></div>
    {/each}

    <!-- Glass gradient overlay -->
    <div
      class="absolute inset-0 bg-gradient-to-br from-slate-100/90 to-slate-200/95 backdrop-blur-sm"
    ></div>
  </div>

  <div class="relative container mx-auto px-6 z-10">
    <!-- Premium section header -->
    <div class="flex justify-between items-center mb-16">
      <div class="premium-highlight">
        <h2
          class="news-section-title text-4xl md:text-5xl font-bold relative gradient-text text-shadow-sm"
        >
          Latest <span class="relative"
            >Updates
            <span
              class="absolute -bottom-2 -left-1 -right-1 h-1 bg-gradient-to-r from-slate-300 via-slate-400 to-slate-300 rounded-full opacity-70"
            ></span>
          </span>
        </h2>
      </div>

      <a
        href="/news"
        class="button group flex items-center gap-2 relative overflow-hidden"
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
      </a>
    </div>

    <div class="news-content">
      <h2
        class="text-3xl font-bold mb-12 gradient-text text-shadow-sm text-center mx-auto max-w-3xl"
      >
        Transparent. Auditable. Decentralized.
      </h2>

      <!-- Advanced 3D card grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div
          class="news-card card-3d p-8 rounded-xl border border-white/60 backdrop-blur-md bg-white/40 shadow-lg relative overflow-hidden"
        >
          <div class="card-3d-inner">
            <div
              class="news-icon text-5xl mb-6 bg-gradient-to-br from-slate-300 to-slate-100 w-16 h-16 flex items-center justify-center rounded-full shadow-md"
            >
              🧾
            </div>
            <h3 class="news-title text-xl font-semibold text-gray-800 mb-4">
              Real-Time Reserve Dashboards
            </h3>
            <p class="text-gray-600 mb-6">
              Track every asset backing Doxa in real-time with our transparent
              dashboard system.
            </p>
            <div class="flex justify-end">
              <a
                href="#"
                class="text-gray-700 hover:text-gray-900 flex items-center gap-1"
              >
                <span>Learn more</span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 5l7 7-7 7"
                  />
                </svg>
              </a>
            </div>
          </div>
          <!-- Highlight effect -->
          <div
            class="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-white/30 to-transparent rounded-full -mr-16 -mt-16 opacity-60"
          ></div>
          <div
            class="absolute bottom-0 left-0 w-24 h-24 bg-gradient-to-tr from-white/20 to-transparent rounded-full -ml-12 -mb-12 opacity-40"
          ></div>
        </div>

        <div
          class="news-card card-3d p-8 rounded-xl border border-white/60 backdrop-blur-md bg-white/40 shadow-lg relative overflow-hidden"
        >
          <div class="card-3d-inner">
            <div
              class="news-icon text-5xl mb-6 bg-gradient-to-br from-slate-300 to-slate-100 w-16 h-16 flex items-center justify-center rounded-full shadow-md"
            >
              🔐
            </div>
            <h3 class="news-title text-xl font-semibold text-gray-800 mb-4">
              Regular Security Audits
            </h3>
            <p class="text-gray-600 mb-6">
              Top security firms audit our smart contracts quarterly to ensure
              maximum safety.
            </p>
            <div class="flex justify-end">
              <a
                href="#"
                class="text-gray-700 hover:text-gray-900 flex items-center gap-1"
              >
                <span>Learn more</span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 5l7 7-7 7"
                  />
                </svg>
              </a>
            </div>
          </div>
          <!-- Highlight effect -->
          <div
            class="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-white/30 to-transparent rounded-full -mr-16 -mt-16 opacity-60"
          ></div>
          <div
            class="absolute bottom-0 left-0 w-24 h-24 bg-gradient-to-tr from-white/20 to-transparent rounded-full -ml-12 -mb-12 opacity-40"
          ></div>
        </div>

        <div
          class="news-card card-3d p-8 rounded-xl border border-white/60 backdrop-blur-md bg-white/40 shadow-lg relative overflow-hidden"
        >
          <div class="card-3d-inner">
            <div
              class="news-icon text-5xl mb-6 bg-gradient-to-br from-slate-300 to-slate-100 w-16 h-16 flex items-center justify-center rounded-full shadow-md"
            >
              📖
            </div>
            <h3 class="news-title text-xl font-semibold text-gray-800 mb-4">
              Open-Source Smart Contracts
            </h3>
            <p class="text-gray-600 mb-6">
              Every line of code is open-source and available for anyone to
              review and validate.
            </p>
            <div class="flex justify-end">
              <a
                href="#"
                class="text-gray-700 hover:text-gray-900 flex items-center gap-1"
              >
                <span>Learn more</span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 5l7 7-7 7"
                  />
                </svg>
              </a>
            </div>
          </div>
          <!-- Highlight effect -->
          <div
            class="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-white/30 to-transparent rounded-full -mr-16 -mt-16 opacity-60"
          ></div>
          <div
            class="absolute bottom-0 left-0 w-24 h-24 bg-gradient-to-tr from-white/20 to-transparent rounded-full -ml-12 -mb-12 opacity-40"
          ></div>
        </div>

        <div
          class="news-card card-3d p-8 rounded-xl border border-white/60 backdrop-blur-md bg-white/40 shadow-lg relative overflow-hidden"
        >
          <div class="card-3d-inner">
            <div
              class="news-icon text-5xl mb-6 bg-gradient-to-br from-slate-300 to-slate-100 w-16 h-16 flex items-center justify-center rounded-full shadow-md"
            >
              💼
            </div>
            <h3 class="news-title text-xl font-semibold text-gray-800 mb-4">
              DAO Governance via SNS
            </h3>
            <p class="text-gray-600 mb-6">
              Community governance with complete transparency through Service
              Nervous System.
            </p>
            <div class="flex justify-end">
              <a
                href="#"
                class="text-gray-700 hover:text-gray-900 flex items-center gap-1"
              >
                <span>Learn more</span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-4 w-4"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 5l7 7-7 7"
                  />
                </svg>
              </a>
            </div>
          </div>
          <!-- Highlight effect -->
          <div
            class="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-white/30 to-transparent rounded-full -mr-16 -mt-16 opacity-60"
          ></div>
          <div
            class="absolute bottom-0 left-0 w-24 h-24 bg-gradient-to-tr from-white/20 to-transparent rounded-full -ml-12 -mb-12 opacity-40"
          ></div>
        </div>
      </div>

      <!-- Call to action -->
      <div class="mt-16 text-center">
        <p class="text-lg text-gray-700 max-w-2xl mx-auto mb-6">
          You deserve to see what backs your money. With Doxa, you do.
        </p>
        <a href="#" class="button inline-flex items-center gap-2">
          <span>Start Exploring</span>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M14 5l7 7m0 0l-7 7m7-7H3"
            />
          </svg>
        </a>
      </div>
    </div>
  </div>
</section>

<style>
  .card-3d {
    transform-style: preserve-3d;
    perspective: 1000px;
  }

  .card-3d-inner {
    transition: transform 0.6s;
    transform-style: preserve-3d;
  }

  @keyframes float-around {
    0%,
    100% {
      transform: translate(0, 0) scale(1);
      opacity: 0.2;
    }
    25% {
      transform: translate(5%, -10%) scale(1.1);
      opacity: 0.3;
    }
    50% {
      transform: translate(10%, 5%) scale(0.9);
      opacity: 0.2;
    }
    75% {
      transform: translate(-5%, 10%) scale(1.05);
      opacity: 0.3;
    }
  }

  .animated-bg-circle {
    position: absolute;
    border-radius: 50%;
    background: linear-gradient(
      180deg,
      rgba(211, 211, 211, 0.15),
      rgba(169, 169, 169, 0)
    );
    animation: float-around 20s infinite ease-in-out;
    opacity: 0.2;
  }

  .gradient-text {
    background: linear-gradient(
      90deg,
      var(--color-theme-2),
      var(--color-theme-1)
    );
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
    border: none;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }

  .button::before {
    content: "";
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      90deg,
      rgba(255, 255, 255, 0.1),
      rgba(255, 255, 255, 0.4),
      rgba(255, 255, 255, 0.1)
    );
    transition: transform 0.5s ease;
    transform: skewX(-15deg);
  }

  .button:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
  }

  .button:hover::before {
    transform: translateX(200%) skewX(-15deg);
  }
</style>
