<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  let gsap: any;
  let ScrollTrigger: any;
  let email = "";
  let submitting = false;
  let submitStatus: { success?: boolean; message?: string } | null = null;
  let emailError: string | null = null;

  const tvl = tweened(0, {
    duration: 2000,
    easing: cubicOut,
  });

  const apy = tweened(0, {
    duration: 2000,
    easing: cubicOut,
  });

  function validateEmail(email: string): boolean {
    const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    return emailRegex.test(email);
  }

  function handleEmailChange() {
    emailError = null;
    if (email && !validateEmail(email)) {
      emailError = "Please enter a valid email address";
    }
  }

  onMount(async () => {
    if (browser) {
      const gsapModule = await import("gsap");
      const scrollTriggerModule = await import("gsap/ScrollTrigger");

      gsap = gsapModule.default;
      ScrollTrigger = scrollTriggerModule.default;
      gsap.registerPlugin(ScrollTrigger);

      // Animate hero section
      gsap.from(".hero-title", {
        duration: 1,
        y: 100,
        opacity: 0,
        ease: "power4.out",
      });

      gsap.from(".hero-description", {
        duration: 1,
        y: 50,
        opacity: 0,
        delay: 0.3,
        ease: "power4.out",
      });

      // Animate stats cards with autoAlpha instead of opacity
      const statsCards = document.querySelectorAll(".stats-card");
      gsap.set(statsCards, { autoAlpha: 1 }); // Ensure cards are visible
      gsap.from(statsCards, {
        duration: 0.8,
        y: 50,
        autoAlpha: 0,
        stagger: 0.2,
        delay: 0.5,
        ease: "power3.out",
        clearProps: "all", // Clear all GSAP-added inline styles after animation
      });

      // Animate features on scroll
      gsap.from(".feature-card", {
        scrollTrigger: {
          trigger: ".feature-card",
          start: "top 80%",
        },
        duration: 0.8,
        y: 100,
        opacity: 0,
        stagger: 0.2,
        ease: "power3.out",
      });

      // Animate news cards on scroll
      gsap.from(".news-card", {
        scrollTrigger: {
          trigger: ".news-card",
          start: "top 80%",
        },
        duration: 0.8,
        x: -100,
        opacity: 0,
        stagger: 0.2,
        ease: "power3.out",
      });
    }
    tvl.set(4.8);
    apy.set(8.2);
  });

  async function handleEmailSubmit(e: Event) {
    e.preventDefault();

    if (!email) {
      emailError = "Email is required";
      return;
    }

    if (!validateEmail(email)) {
      emailError = "Please enter a valid email address";
      return;
    }

    submitting = true;
    submitStatus = null;

    try {
      // For now, just show a success message
      // TODO: Implement actual email collection in IC canister
      submitStatus = {
        success: true,
        message: "Thanks for signing up! We'll keep you updated.",
      };
      email = "";
      emailError = null;
    } catch (error) {
      submitStatus = {
        success: false,
        message: "Something went wrong. Please try again later.",
      };
    } finally {
      submitting = false;
    }
  }
</script>

<svelte:head>
  <title>DoxaV3 - Stablecoin on Internet Computer</title>
  <meta
    name="description"
    content="A decentralized stablecoin built on Internet Computer"
  />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600;700&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div
  class="min-h-screen bg-gradient-to-br from-purple-900 via-[#1E0447] to-purple-900 relative overflow-hidden"
>
  <!-- Animated Background -->
  <div class="absolute inset-0 overflow-hidden">
    {#each Array(20) as _, i}
      <div
        class="absolute h-px opacity-20"
        style="
          background: linear-gradient(90deg, {['#FF4D4D', '#4DA6FF', '#4DFFB7'][
          i % 3
        ]}, transparent);
          width: {50 + Math.random() * 150}px;
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          transform: rotate({Math.random() * 360}deg);
          animation: shooting {2 + Math.random() * 3}s linear infinite;
        "
      />
    {/each}
  </div>

  <!-- Navigation -->
  <nav class="container mx-auto px-6 py-4 relative">
    <div class="flex items-center justify-between">
      <div class="text-2xl font-bold text-white flex items-center gap-2">
        <div
          class="w-8 h-8 bg-purple-500 rounded-lg flex items-center justify-center"
        >
          D3
        </div>
        DoxaV3
      </div>
      <div class="hidden md:flex space-x-8">
        <a href="#" class="text-gray-300 hover:text-white transition-colors"
          >Partners</a
        >
        <a href="#" class="text-gray-300 hover:text-white transition-colors"
          >Use</a
        >
        <a href="#" class="text-gray-300 hover:text-white transition-colors"
          >Developer</a
        >
        <button
          class="bg-gradient-to-r from-purple-500 to-purple-600 hover:from-purple-600 hover:to-purple-700 text-white px-6 py-2 rounded-full transition-all duration-300 transform hover:scale-105"
        >
          Launch App
        </button>
      </div>
    </div>
  </nav>

  <!-- Hero Section -->
  <div class="container mx-auto px-6 py-20 relative">
    <div class="flex flex-col md:flex-row items-center">
      <div class="md:w-1/2">
        <h1
          class="hero-title text-5xl md:text-7xl font-bold text-white mb-8 leading-tight"
        >
          The Future of <span
            class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-400"
            >Stablecoin</span
          > is Here
        </h1>
        <p class="hero-description text-xl text-gray-300 mb-8">
          DoxaV3 is a decentralized stablecoin built on the Internet Computer,
          offering stability, security, and true decentralization.
        </p>
        <div class="flex space-x-4">
          <a
            href="https://github.com"
            class="group bg-white text-purple-900 px-8 py-3 rounded-full font-medium hover:bg-gray-100 transition-all duration-300 transform hover:scale-105 flex items-center gap-2"
          >
            View on GitHub
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
            href="#learn-more"
            class="group border border-white text-white px-8 py-3 rounded-full font-medium hover:bg-white hover:text-purple-900 transition-all duration-300"
          >
            Learn More
          </a>
        </div>
      </div>

      <!-- Stats Cards -->
      <div class="md:w-1/2 mt-12 md:mt-0 grid grid-cols-2 gap-6">
        <div
          class="stats-card bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105"
        >
          <h3 class="text-gray-400 mb-2">Total Value Locked</h3>
          <div class="text-3xl font-bold text-white">${$tvl}M</div>
          <div class="text-green-400 flex items-center gap-1">
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
                d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"
              />
            </svg>
            12.5%
          </div>
        </div>
        <div
          class="stats-card bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105"
        >
          <h3 class="text-gray-400 mb-2">APY</h3>
          <div class="text-3xl font-bold text-white">{$apy}%</div>
          <div class="text-green-400">↑ 0.5%</div>
        </div>
        <div
          class="stats-card bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105"
        >
          <h3 class="text-gray-400 mb-2">Weekly Rewards</h3>
          <div class="text-3xl font-bold text-white">125,000 DOXA</div>
        </div>
        <div
          class="stats-card bg-purple-800/30 backdrop-blur-xl p-6 rounded-2xl border border-purple-700/50 hover:border-purple-500 transition-all duration-300 transform hover:scale-105"
        >
          <h3 class="text-gray-400 mb-2">Total Fees Collected</h3>
          <div class="text-3xl font-bold text-white">$283.5K</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Features Section -->
<section class="py-32 relative overflow-hidden">
  <!-- Animated Background Grid -->
  <div class="absolute inset-0 bg-[#0a0118]">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <h2 class="text-4xl md:text-5xl font-bold text-center text-white mb-16">
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

<!-- Latest News Section -->
<section class="py-32 relative overflow-hidden">
  <div class="absolute inset-0 bg-[#0a0118]">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <div class="flex justify-between items-center mb-16">
      <h2 class="text-4xl md:text-5xl font-bold text-white">
        Latest <span
          class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-400"
          >Updates</span
        >
      </h2>
      <a
        href="/news"
        class="group flex items-center gap-2 text-white hover:text-purple-400 transition-colors"
      >
        <span>View All</span>
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
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
      {#each [{ title: "DoxaV3: The First Algorithmic Stablecoin on Internet Computer", date: "Jan 20, 2025", link: "/news/first-algorithmic-stablecoin" }, { title: "How DoxaV3 Maintains Price Stability Through Smart Contracts", date: "Jan 15, 2025", link: "/news/price-stability" }, { title: "DoxaV3 Partners with Major DeFi Protocols", date: "Jan 10, 2025", link: "/news/defi-protocols" }, { title: "The Future of Stablecoins on Internet Computer", date: "Jan 5, 2025", link: "/news/future-stablecoins" }] as news}
        <a href={news.link} class="group">
          <div
            class="p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
          >
            <h3
              class="text-xl font-semibold text-white mb-4 group-hover:text-purple-400 transition-colors"
            >
              {news.title}
            </h3>
            <time class="text-purple-400">{news.date}</time>
          </div>
        </a>
      {/each}
    </div>
  </div>
</section>

<!-- Integration Section -->
<section class="py-32 relative overflow-hidden">
  <div
    class="absolute inset-0 bg-gradient-to-br from-purple-900 via-[#1E0447] to-purple-900"
  ></div>
  <div class="absolute inset-0">
    {#each Array(20) as _, i}
      <div
        class="absolute h-px opacity-20"
        style="
          background: linear-gradient(90deg, {['#FF4D4D', '#4DA6FF', '#4DFFB7'][
          i % 3
        ]}, transparent);
          width: {50 + Math.random() * 150}px;
          left: {Math.random() * 100}%;
          top: {Math.random() * 100}%;
          transform: rotate({Math.random() * 360}deg);
          animation: shooting {2 + Math.random() * 3}s linear infinite;
        "
      />
    {/each}
  </div>

  <div class="relative container mx-auto px-6">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
      <!-- Algorithmic Stability -->
      <div
        class="p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
      >
        <h3 class="text-3xl font-bold text-white mb-6">
          Algorithmic Stability
        </h3>
        <p class="text-gray-300 text-lg mb-8">
          DoxaV3 implements advanced algorithmic mechanisms to maintain price
          stability. Our smart contracts automatically adjust supply based on
          market demand, ensuring a reliable 1:1 peg with USD.
        </p>
        <a
          href="/mechanism"
          class="inline-flex items-center gap-2 text-white hover:text-purple-400 transition-colors group"
        >
          <span>Learn How It Works</span>
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
      </div>

      <!-- Integration & Development -->
      <div
        class="p-8 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500"
      >
        <h3 class="text-3xl font-bold text-white mb-6">
          Integration & Development
        </h3>
        <p class="text-gray-300 text-lg mb-8">
          Built on Internet Computer, DoxaV3 offers seamless integration with
          DeFi protocols. Our SDK and APIs make it easy to integrate stablecoin
          functionality into your dapps.
        </p>
        <a
          href="/build"
          class="inline-flex items-center gap-2 text-white hover:text-purple-400 transition-colors group"
        >
          <span>Start Building</span>
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
      </div>
    </div>
  </div>
</section>

<!-- Newsletter Section -->
<section class="py-32 relative overflow-hidden">
  <div
    class="absolute inset-0 bg-gradient-to-br from-purple-900 via-[#1E0447] to-purple-900 opacity-90"
  ></div>

  <div class="relative container mx-auto px-6 max-w-4xl">
    <div class="text-center">
      <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
        Stay Updated
      </h2>
      <p class="text-xl text-gray-300 mb-12">
        Get the latest updates about DoxaV3 and the Internet Computer ecosystem
      </p>

      <form class="max-w-md mx-auto" on:submit={handleEmailSubmit}>
        <div class="flex flex-col gap-4">
          <div class="relative">
            <input
              type="email"
              placeholder="Enter your email"
              bind:value={email}
              on:input={handleEmailChange}
              class="w-full px-6 py-4 rounded-full bg-purple-900/50 backdrop-blur-xl border border-purple-700/50 text-white placeholder-gray-400 focus:outline-none focus:border-purple-500 transition-colors {emailError
                ? 'border-red-500'
                : ''}"
            />
            <button
              type="submit"
              disabled={submitting || !!emailError}
              class="absolute right-2 top-2 px-6 py-2 bg-gradient-to-r from-purple-500 to-purple-600 hover:from-purple-600 hover:to-purple-700 text-white rounded-full transition-all duration-300 transform hover:scale-105 disabled:opacity-50 disabled:cursor-not-allowed"
            >
              {submitting ? "Subscribing..." : "Subscribe"}
            </button>
          </div>

          {#if emailError}
            <div class="text-red-400 text-sm">{emailError}</div>
          {/if}

          {#if submitStatus}
            <div
              class="text-white bg-purple-900/50 backdrop-blur-xl border border-purple-700/50 px-6 py-3 rounded-full"
            >
              {submitStatus.message}
            </div>
          {/if}
        </div>
      </form>
    </div>
  </div>
</section>

<!-- CTA Section -->
<div class="relative py-20 overflow-hidden">
  <!-- Gradient Background -->
  <div
    class="absolute inset-0 bg-gradient-to-r from-purple-900 via-purple-800 to-purple-900 opacity-90"
  ></div>

  <!-- Animated Circles -->
  <div class="absolute inset-0">
    <div
      class="absolute w-96 h-96 bg-purple-500/20 rounded-full -top-48 -left-48 blur-3xl"
    ></div>
    <div
      class="absolute w-96 h-96 bg-purple-700/20 rounded-full -bottom-48 -right-48 blur-3xl"
    ></div>
  </div>

  <div class="relative container mx-auto px-6 text-center">
    <h2 class="text-4xl md:text-5xl font-bold text-white mb-8">
      Ready to Join the Future of Finance?
    </h2>
    <p class="text-xl text-gray-300 mb-12 max-w-2xl mx-auto">
      Start using DoxaV3 today and experience the power of decentralized
      stablecoins on the Internet Computer.
    </p>
    <div class="flex flex-col md:flex-row gap-6 justify-center">
      <a
        href="#"
        class="inline-flex items-center justify-center px-8 py-3 bg-white text-purple-900 rounded-full font-medium hover:bg-gray-100 transition-colors"
      >
        Launch App
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 ml-2"
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

<style lang="postcss">
  :global(html) {
    scroll-behavior: smooth;
  }

  :global(body) {
    @apply text-gray-900;
    background: #0a0118;
  }

  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(255, 255, 255, 0.1) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(255, 255, 255, 0.1) 1px, transparent 1px);
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
      transform: translateY(0);
    }
    50% {
      transform: translateY(-20px);
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
    transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  }

  .feature-card:hover {
    transform: translateY(-10px);
  }
</style>
