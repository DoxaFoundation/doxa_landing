<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  let gsap: any;
  let ScrollTrigger: any;
  let email = "";
  let submitting = false;
  let submitStatus: { success?: boolean; message?: string } | null = null;
  let emailError: string | null = null;

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
    }
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

<!-- Navigation -->
<header
  class="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-md border-b border-gray-100"
>
  <nav class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
    <a
      href="/"
      class="text-[2rem] font-bold text-[#8247E5] font-['Space_Grotesk']"
      >DoxaV3</a
    >
    <div class="flex items-center gap-8">
      <a
        href="#partners"
        class="text-gray-600 hover:text-[#8247E5] font-['Inter'] font-medium transition-colors"
        >Partners</a
      >
      <a
        href="https://doxa-1.gitbook.io/doxa-guide"
        target="_blank"
        rel="noopener"
        class="text-gray-600 hover:text-[#8247E5] font-['Inter'] font-medium transition-colors"
        >Use</a
      >
      <a
        href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="text-gray-600 hover:text-[#8247E5] font-['Inter'] font-medium transition-colors"
        >Developer</a
      >
      <a
        href="https://i7m4z-gqaaa-aaaak-qddtq-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="px-4 py-2 bg-[#8247E5] text-white rounded-full hover:bg-[#6d35c7] transition-all font-['Inter'] font-medium"
        >Launch App</a
      >
    </div>
  </nav>
</header>

<!-- Hero Section -->
<main class="pt-32 pb-20">
  <div class="max-w-7xl mx-auto px-4">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
      <div>
        <h1 class="text-[4rem] font-bold leading-tight">
          The Future of <span class="text-[#8247E5]">Stablecoin</span> is Here
        </h1>
        <p class="mt-6 text-xl text-gray-600">
          DoxaV3 is a decentralized stablecoin built on the Internet Computer,
          offering stability, security, and true decentralization.
        </p>
        <div class="mt-8 flex gap-4">
          <a
            href="https://github.com/DoxaFoundation/doxa-v3"
            class="px-8 py-3 bg-[#8247E5] text-white rounded-full hover:bg-[#6d35c7] transition-all"
          >
            View on GitHub
          </a>
          <a
            href="#learn-more"
            class="px-8 py-3 border-2 border-[#8247E5] text-[#8247E5] rounded-full hover:bg-[#8247E5]/5 transition-all"
          >
            Learn More
          </a>
        </div>
      </div>
      <div class="grid grid-cols-2 gap-4">
        <div
          class="bg-gradient-to-br from-[#1E0447] to-[#3B0764] p-6 rounded-2xl"
        >
          <p class="text-gray-300 text-sm mb-1">Total Value Locked</p>
          <p class="text-white text-2xl font-bold flex items-center">
            $4.8M
            <span class="text-green-400 text-sm ml-2">↑ 12.5%</span>
          </p>
        </div>
        <div
          class="bg-gradient-to-br from-[#1E0447] to-[#3B0764] p-6 rounded-2xl"
        >
          <p class="text-gray-300 text-sm mb-1">APY</p>
          <p class="text-white text-2xl font-bold flex items-center">
            8.2%
            <span class="text-green-400 text-sm ml-2">↑ 0.5%</span>
          </p>
        </div>
        <div
          class="bg-gradient-to-br from-[#1E0447] to-[#3B0764] p-6 rounded-2xl"
        >
          <p class="text-gray-300 text-sm mb-1">Weekly Rewards</p>
          <p class="text-white text-2xl font-bold">125,000 DOXA</p>
        </div>
        <div
          class="bg-gradient-to-br from-[#1E0447] to-[#3B0764] p-6 rounded-2xl"
        >
          <p class="text-gray-300 text-sm mb-1">Total Fees Collected</p>
          <p class="text-white text-2xl font-bold">$283.5K</p>
        </div>
      </div>
    </div>
  </div>
</main>

<!-- Features -->
<section class="py-32 bg-gray-50">
  <div class="max-w-7xl mx-auto px-4">
    <h2 class="text-3xl font-bold text-center mb-16">Why Choose DoxaV3?</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div class="bg-white p-8 rounded-xl shadow-lg">
        <div
          class="w-12 h-12 bg-[#8247E5]/10 rounded-lg flex items-center justify-center mb-6"
        >
          <svg
            class="w-6 h-6 text-[#8247E5]"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
            ></path>
          </svg>
        </div>
        <h3 class="text-xl font-semibold mb-3">Price Stability</h3>
        <p class="text-gray-600">
          Maintains a stable 1:1 peg with USD through advanced algorithmic
          mechanisms.
        </p>
      </div>

      <div class="bg-white p-8 rounded-xl shadow-lg">
        <div
          class="w-12 h-12 bg-[#8247E5]/10 rounded-lg flex items-center justify-center mb-6"
        >
          <svg
            class="w-6 h-6 text-[#8247E5]"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"
            ></path>
          </svg>
        </div>
        <h3 class="text-xl font-semibold mb-3">Secure & Audited</h3>
        <p class="text-gray-600">
          Built on Internet Computer with rigorous security measures and audits.
        </p>
      </div>

      <div class="bg-white p-8 rounded-xl shadow-lg">
        <div
          class="w-12 h-12 bg-[#8247E5]/10 rounded-lg flex items-center justify-center mb-6"
        >
          <svg
            class="w-6 h-6 text-[#8247E5]"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
            ></path>
          </svg>
        </div>
        <h3 class="text-xl font-semibold mb-3">Decentralized</h3>
        <p class="text-gray-600">
          Fully decentralized architecture with no central point of failure.
        </p>
      </div>
    </div>
  </div>
</section>

<!-- Latest News -->
<section class="py-32 bg-[#1E0447]">
  <div class="max-w-7xl mx-auto px-4">
    <div class="flex justify-between items-center mb-12">
      <h2 class="text-3xl font-bold text-white">Latest Global Press</h2>
      <a
        href="/news"
        class="text-white flex items-center gap-2 hover:opacity-80 transition-all"
      >
        More News →
      </a>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-4 gap-12">
      <a href="/news/first-algorithmic-stablecoin" class="group block">
        <article>
          <h3
            class="text-2xl font-semibold text-white mb-4 group-hover:text-[#8247E5] transition-colors"
          >
            DoxaV3: The First Algorithmic Stablecoin on Internet Computer
          </h3>
          <time class="text-[#8247E5] text-lg">Jan 20, 2025</time>
        </article>
      </a>
      <a href="/news/price-stability" class="group block">
        <article>
          <h3
            class="text-2xl font-semibold text-white mb-4 group-hover:text-[#8247E5] transition-colors"
          >
            How DoxaV3 Maintains Price Stability Through Smart Contracts
          </h3>
          <time class="text-[#8247E5] text-lg">Jan 15, 2025</time>
        </article>
      </a>
      <a href="/news/defi-protocols" class="group block">
        <article>
          <h3
            class="text-2xl font-semibold text-white mb-4 group-hover:text-[#8247E5] transition-colors"
          >
            DoxaV3 Partners with Major DeFi Protocols
          </h3>
          <time class="text-[#8247E5] text-lg">Jan 10, 2025</time>
        </article>
      </a>
      <a href="/news/future-stablecoins" class="group block">
        <article>
          <h3
            class="text-2xl font-semibold text-white mb-4 group-hover:text-[#8247E5] transition-colors"
          >
            The Future of Stablecoins on Internet Computer
          </h3>
          <time class="text-[#8247E5] text-lg">Jan 5, 2025</time>
        </article>
      </a>
    </div>
  </div>
</section>

<!-- White Space Section -->
<section class="py-32 bg-white">
  <div class="max-w-7xl mx-auto px-4">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <!-- Block 1 -->
      <div class="bg-[#1c1c1c] p-12 rounded-3xl">
        <h2 class="text-3xl font-bold text-white mb-6">
          Algorithmic Stability
        </h2>
        <p class="text-gray-300 text-lg mb-8">
          DoxaV3 implements advanced algorithmic mechanisms to maintain price
          stability. Our smart contracts automatically adjust supply based on
          market demand, ensuring a reliable 1:1 peg with USD without requiring
          collateral.
        </p>
        <a
          href="/mechanism"
          class="inline-block px-8 py-4 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 hover:bg-white/20 transition-all text-xl"
        >
          LEARN HOW IT WORKS
        </a>
      </div>

      <!-- Block 2 -->
      <div class="bg-[#1c1c1c] p-12 rounded-3xl">
        <h2 class="text-3xl font-bold text-white mb-6">
          Integration & Development
        </h2>
        <p class="text-gray-300 text-lg mb-8">
          Built on Internet Computer, DoxaV3 offers seamless integration with
          DeFi protocols. Our SDK and APIs make it easy to integrate stablecoin
          functionality into your dapps with minimal overhead.
        </p>
        <a
          href="/build"
          class="inline-block px-8 py-4 bg-[#8247E5] text-white rounded-xl hover:bg-[#6d35c7] transition-all text-xl font-medium"
        >
          START BUILDING
        </a>
      </div>
    </div>
  </div>
</section>

<!-- Email Signup -->
<section class="py-32 bg-gradient-to-br from-[#1E0447] to-[#3B0764]">
  <div class="max-w-7xl mx-auto px-4">
    <div class="max-w-3xl mx-auto text-center">
      <h2 class="text-3xl md:text-4xl font-bold text-white mb-6">
        Sign up for email updates
      </h2>
      <p class="text-xl text-gray-300 mb-8">
        to keep up to date with the Internet Computer and DoxaV3 stablecoin
      </p>
      <form
        class="flex flex-col gap-4 max-w-md mx-auto"
        on:submit={handleEmailSubmit}
      >
        <div class="flex flex-col gap-2">
          <div class="flex gap-4">
            <input
              type="email"
              placeholder="Email"
              bind:value={email}
              on:input={handleEmailChange}
              required
              class="flex-1 px-6 py-3 rounded-full bg-[#2D1B69] text-white placeholder-gray-400 border border-white/20 focus:outline-none focus:border-[#8247E5] {emailError
                ? 'border-red-500'
                : ''}"
            />
            <button
              type="submit"
              disabled={submitting || !!emailError}
              class="px-8 py-3 bg-[#8247E5] text-white rounded-full hover:bg-[#6d35c7] transition-all font-semibold whitespace-nowrap disabled:opacity-50 disabled:cursor-not-allowed"
            >
              {submitting ? "SUBMITTING..." : "GET UPDATES"}
            </button>
          </div>
          {#if emailError}
            <div class="text-red-400 text-sm text-left px-4">
              {emailError}
            </div>
          {/if}
        </div>
        {#if submitStatus}
          <div
            class="text-white/90 px-6 py-3 rounded-lg bg-[#2D1B69] border border-white/10"
          >
            {submitStatus.message}
          </div>
        {/if}
      </form>
    </div>
  </div>
</section>

<!-- Security & Features Section -->
<section class="relative overflow-hidden rounded-[48px] mx-8 my-24">
  <div
    class="absolute inset-0 bg-gradient-to-br from-emerald-400 via-teal-500 to-blue-600"
  ></div>
  <div class="absolute inset-0 bg-grid opacity-20"></div>

  <div
    class="relative p-14 md:p-12 flex flex-col md:flex-row items-center justify-between gap-10"
  >
    <!-- 3D Background Image -->
    <div class="w-full md:w-1/2 relative">
      <div class="aspect-[3/2] relative">
        <div class="absolute inset-0">
          <!-- 3D USDX Text -->
          <div
            class="text-[14rem] font-bold text-white/10 transform -rotate-12 translate-y-12 select-none leading-none"
          >
            USDX
          </div>
        </div>
      </div>
    </div>

    <!-- Content -->
    <div class="w-full md:w-1/2 text-white">
      <h2 class="text-6xl font-bold mb-6 leading-[1.1]">
        Make DeFi<br />
        immune to<br />
        volatility
      </h2>
      <p class="text-xl mb-10 text-white/90 leading-relaxed">
        USDX, the first algorithmic stablecoin on Internet Computer, designed
        for true price stability and decentralization
      </p>
      <a
        href="/defi"
        class="inline-block px-6 py-3 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 hover:bg-white/20 transition-all text-lg font-medium"
      >
        EXPLORE DEFI
      </a>
    </div>
  </div>
</section>

<!-- DoxaV3 Fusion Section -->
<section class="relative overflow-hidden rounded-[48px] mx-8 mb-32">
  <!-- Background with animated lines -->
  <div class="absolute inset-0 bg-[#1E0447]">
    {#each Array(20) as _, i}
      <div
        class="absolute h-1 opacity-50"
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

  <div
    class="relative p-16 flex flex-col md:flex-row items-center justify-between"
  >
    <!-- Left Content -->
    <div class="w-full md:w-1/2 flex items-center">
      <div>
        <img src="/infinity.svg" alt="Infinity" class="w-16 h-16 mb-6" />
        <h2 class="text-[3.5rem] font-bold text-white leading-none mb-8">
          DOXA<br />FUSION
        </h2>
      </div>
    </div>

    <!-- Right Content -->
    <div class="w-full md:w-1/2 text-white">
      <p class="text-2xl leading-relaxed mb-8">
        Experience true DeFi stability with DoxaV3's innovative features: zero
        collateral requirements, self-stabilizing mechanisms, instant finality,
        and seamless cross-chain integration.
      </p>
      <div class="grid grid-cols-2 gap-6 mb-8">
        <div class="bg-white/5 backdrop-blur-sm rounded-xl p-4">
          <div class="text-xl font-semibold mb-2">Price Stability</div>
          <div class="text-white/80">
            Maintains 1:1 USD peg through advanced algorithmic mechanisms
          </div>
        </div>
        <div class="bg-white/5 backdrop-blur-sm rounded-xl p-4">
          <div class="text-xl font-semibold mb-2">Zero Collateral</div>
          <div class="text-white/80">
            Pure algorithmic design without collateral requirements
          </div>
        </div>
      </div>
      <a
        href="/mechanism"
        class="inline-block px-8 py-4 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 hover:bg-white/20 transition-all text-xl"
      >
        EXPLORE MECHANISM
      </a>
    </div>
  </div>
</section>

<!-- Footer -->
<footer
  class="py-20 bg-gradient-to-br from-[#0F172A] via-[#1E1B4B] to-[#3B0764] text-white relative overflow-hidden"
>
  <div class="absolute inset-0 bg-grid opacity-10"></div>
  <div
    class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent"
  ></div>
  <div class="max-w-7xl mx-auto px-4 relative">
    <div class="grid grid-cols-1 md:grid-cols-4 gap-16 mb-12">
      <!-- About Us -->
      <div class="space-y-4 md:pr-8">
        <h5 class="text-lg font-semibold mb-4">About Us</h5>
        <p class="text-gray-300 text-sm leading-relaxed">
          Doxa is a multi-stablecoin platform built on the Internet Computer
          (IC). Our platform enables seamless integration and amazing
          applications.
        </p>
      </div>

      <!-- Quick Links -->
      <div class="space-y-4">
        <h5 class="text-lg font-semibold mb-4">Quick Links</h5>
        <ul class="space-y-2">
          <li>
            <a
              href="#partners"
              class="text-gray-300 hover:text-[#8247E5] transition-colors duration-300"
              >Partners</a
            >
          </li>
          <li>
            <a
              href="https://doxa-1.gitbook.io/doxa-guide"
              target="_blank"
              rel="noopener"
              class="text-gray-300 hover:text-[#8247E5] transition-colors duration-300"
              >Use</a
            >
          </li>
          <li>
            <a
              href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
              target="_blank"
              rel="noopener"
              class="text-gray-300 hover:text-[#8247E5] transition-colors duration-300"
              >Developer</a
            >
          </li>
          <li>
            <a
              href="https://i7m4z-gqaaa-aaaak-qddtq-cai.icp0.io/"
              target="_blank"
              rel="noopener"
              class="text-gray-300 hover:text-[#8247E5] transition-colors duration-300"
              >Launch App</a
            >
          </li>
        </ul>
      </div>

      <!-- Contact Us -->
      <div class="space-y-3">
        <h5 class="text-lg font-semibold mb-4">Contact Us</h5>
        <a
          href="mailto:doxadaooperations@gmail.com"
          class="block text-gray-300 hover:text-[#8247E5] transition-colors duration-300 flex items-center gap-2 mb-2"
        >
          <svg
            class="w-4 h-4"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
            />
          </svg>
          doxadaooperations@gmail.com
        </a>
      </div>

      <!-- Social Links -->
      <div class="space-y-3">
        <h5 class="text-lg font-semibold mb-4">Follow Us</h5>
        <div class="grid grid-cols-2 gap-4">
          <a
            href="https://twitter.com/DoxaUSD?t=Wq2e3fcxhzAngSZ5Pve9ww&s=09"
            target="_blank"
            rel="noopener"
            class="flex items-center gap-2 text-gray-300 hover:text-[#8247E5] transition-all duration-300"
          >
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"
              />
            </svg>
            Twitter
          </a>
          <a
            href="https://discord.gg/zmUArkqy"
            target="_blank"
            rel="noopener"
            class="flex items-center gap-2 text-gray-300 hover:text-[#8247E5] transition-all duration-300"
          >
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M20.317 4.37a19.791 19.791 0 00-4.885-1.515.074.074 0 00-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 00-5.487 0 12.64 12.64 0 00-.617-1.25.077.077 0 00-.079-.037A19.736 19.736 0 003.677 4.37a.07.07 0 00-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 00.031.057 19.9 19.9 0 005.993 3.03.078.078 0 00.084-.028c.462-.63.874-1.295 1.226-1.994.021-.041.001-.09-.041-.106a13.107 13.107 0 01-1.872-.892.077.077 0 01-.008-.128 10.2 10.2 0 00.372-.292.074.074 0 01.077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 01.078.01c.12.098.246.198.373.292a.077.077 0 01-.006.127 12.299 12.299 0 01-1.873.892.077.077 0 00-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 00.084.028 19.839 19.839 0 006.002-3.03.077.077 0 00.032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 00-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"
              />
            </svg>
            Discord
          </a>
          <a
            href="https://github.com/DoxaFoundation/doxa-v3"
            target="_blank"
            rel="noopener"
            class="flex items-center gap-2 text-gray-300 hover:text-[#8247E5] transition-all duration-300"
          >
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 2C6.477 2 2 6.477 2 12c0 4.42 2.865 8.17 6.839 9.49.5.092.682-.217.682-.482 0-.237-.008-.866-.013-1.7-2.782.604-3.369-1.34-3.369-1.34-.454-1.156-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.114 2.504.336 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.578.688.48C19.138 20.167 22 16.418 22 12c0-5.523-4.477-10-10-10z"
              />
            </svg>
            GitHub
          </a>
          <a
            href="https://oc.app/community/4opco-piaaa-aaaaf-bmytq-cai/?ref=luvob-jqaaa-aaaar-aymqa-cai"
            target="_blank"
            rel="noopener"
            class="flex items-center gap-2 text-gray-300 hover:text-[#8247E5] transition-all duration-300"
          >
            <svg
              class="w-5 h-5"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"
              />
            </svg>
            Community
          </a>
        </div>
      </div>
    </div>

    <!-- Copyright -->
    <div
      class="flex flex-wrap justify-center gap-6 text-sm text-gray-400 border-t border-white/10 pt-6"
    >
      <span>© 2025 DoxaV3</span>
      <a
        href="/terms"
        class="hover:text-[#8247E5] transition-colors duration-300"
        >Terms of Use</a
      >
      <a
        href="/privacy"
        class="hover:text-[#8247E5] transition-colors duration-300"
        >Privacy Policy</a
      >
    </div>
  </div>
</footer>

<style lang="postcss">
  :global(html) {
    scroll-behavior: smooth;
  }

  :global(body) {
    @apply text-gray-900;
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
</style>
