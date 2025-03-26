<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
  let gsap: any;
  let ScrollTrigger: any;

  onMount(async () => {
    if (browser) {
      const gsapModule = await import("gsap");
      const scrollTriggerModule = await import("gsap/ScrollTrigger");

      gsap = gsapModule.default;
      ScrollTrigger = scrollTriggerModule.default;

      gsap.registerPlugin(ScrollTrigger);
    }
  });
</script>

<svelte:head>
  <title>DoxaV3 - Stablecoin on Internet Computer</title>
  <meta
    name="description"
    content="A decentralized stablecoin built on Internet Computer"
  />
</svelte:head>

<!-- Navigation -->
<header class="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-sm">
  <nav class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
    <a href="/" class="text-[2rem] font-bold text-[#8247E5]">DoxaV3</a>
    <div class="flex items-center gap-8">
      <a href="#learn" class="text-gray-600 hover:text-[#8247E5]">Learn</a>
      <a href="#use" class="text-gray-600 hover:text-[#8247E5]">Use</a>
      <a href="#develop" class="text-gray-600 hover:text-[#8247E5]">Develop</a>
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
            href="https://github.com/Tswaanda/doxav3"
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
          class="inline-block px-6 py-3 border border-white/20 text-white rounded-full hover:bg-white/10 transition-all"
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
          href="/developers"
          class="inline-block px-6 py-3 border border-white/20 text-white rounded-full hover:bg-white/10 transition-all"
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
      <form class="flex gap-4 max-w-md mx-auto">
        <input
          type="email"
          placeholder="Email"
          class="flex-1 px-6 py-3 rounded-full bg-white/10 text-white placeholder-gray-400 border border-white/20 focus:outline-none focus:border-[#8247E5]"
        />
        <button
          type="submit"
          class="px-8 py-3 bg-[#8247E5] text-white rounded-full hover:bg-[#6d35c7] transition-all font-semibold whitespace-nowrap"
        >
          GET UPDATES
        </button>
      </form>
    </div>
  </div>
</section>

<!-- White Space Section -->
<section class="py-32 bg-white">
  <div class="max-w-7xl mx-auto px-4"></div>
</section>

<!-- Footer -->
<footer class="py-32 bg-[#3B0764] text-white">
  <div class="max-w-7xl mx-auto px-4">
    <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-16">
      <!-- Column 1 -->
      <div class="space-y-4">
        <a href="/docs" class="block hover:text-[#8247E5] transition-colors"
          >Documentation ↗</a
        >
        <a
          href="/whitepaper"
          class="block hover:text-[#8247E5] transition-colors">Whitepaper ↗</a
        >
        <a
          href="/contracts"
          class="block hover:text-[#8247E5] transition-colors"
          >Smart Contracts</a
        >
        <a href="/api" class="block hover:text-[#8247E5] transition-colors"
          >API Reference ↗</a
        >
      </div>

      <!-- Column 2 -->
      <div class="space-y-4">
        <a
          href="/integration"
          class="block hover:text-[#8247E5] transition-colors"
          >Integration Guide ↗</a
        >
        <a href="/bounty" class="block hover:text-[#8247E5] transition-colors"
          >Bug Bounty ↗</a
        >
        <a
          href="/community"
          class="block hover:text-[#8247E5] transition-colors">Community ↗</a
        >
        <a
          href="/governance"
          class="block hover:text-[#8247E5] transition-colors">Governance ↗</a
        >
      </div>

      <!-- Column 3: Social Icons -->
      <div class="col-span-2 md:col-span-2">
        <div class="flex flex-wrap gap-4">
          <a
            href="https://twitter.com/DoxaV3"
            class="hover:opacity-80 transition-opacity"
          >
            <svg
              class="w-8 h-8 text-white"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"
              />
            </svg>
          </a>
          <a
            href="https://t.me/DoxaV3"
            class="hover:opacity-80 transition-opacity"
          >
            <svg
              class="w-8 h-8 text-white"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm4.64 6.8c-.15 1.58-.8 5.47-1.13 7.25-.14.74-.42 1-.68 1.02-.58.05-1.02-.38-1.58-.75-.88-.58-1.38-.94-2.23-1.5-.99-.65-.35-1.01.22-1.59.15-.15 2.71-2.48 2.76-2.69a.2.2 0 00-.05-.18c-.06-.05-.14-.03-.21-.02-.09.02-1.49.95-4.22 2.79-.4.27-.76.41-1.08.4-.36-.01-1.04-.2-1.55-.37-.63-.2-1.12-.31-1.08-.66.02-.18.27-.36.74-.55 2.92-1.27 4.86-2.11 5.83-2.51 2.78-1.16 3.35-1.36 3.73-1.36.08 0 .27.02.39.12.1.08.13.19.14.27-.01.06.01.24 0 .38z"
              />
            </svg>
          </a>
          <a
            href="https://github.com/Tswaanda/doxav3"
            class="hover:opacity-80 transition-opacity"
          >
            <svg
              class="w-8 h-8 text-white"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M12 2C6.477 2 2 6.477 2 12c0 4.42 2.865 8.17 6.839 9.49.5.092.682-.217.682-.482 0-.237-.008-.866-.013-1.7-2.782.604-3.369-1.34-3.369-1.34-.454-1.156-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.114 2.504.336 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.578.688.48C19.138 20.167 22 16.418 22 12c0-5.523-4.477-10-10-10z"
              />
            </svg>
          </a>
          <a
            href="https://discord.gg/doxav3"
            class="hover:opacity-80 transition-opacity"
          >
            <svg
              class="w-8 h-8 text-white"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M20.317 4.37a19.791 19.791 0 00-4.885-1.515.074.074 0 00-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 00-5.487 0 12.64 12.64 0 00-.617-1.25.077.077 0 00-.079-.037A19.736 19.736 0 003.677 4.37a.07.07 0 00-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 00.031.057 19.9 19.9 0 005.993 3.03.078.078 0 00.084-.028c.462-.63.874-1.295 1.226-1.994.021-.041.001-.09-.041-.106a13.107 13.107 0 01-1.872-.892.077.077 0 01-.008-.128 10.2 10.2 0 00.372-.292.074.074 0 01.077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 01.078.01c.12.098.246.198.373.292a.077.077 0 01-.006.127 12.299 12.299 0 01-1.873.892.077.077 0 00-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 00.084.028 19.839 19.839 0 006.002-3.03.077.077 0 00.032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 00-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"
              />
            </svg>
          </a>
        </div>

        <!-- Email Signup -->
        <div class="mt-12">
          <h3 class="text-xl mb-4">
            Stay updated with DoxaV3's latest developments and announcements
          </h3>
          <form class="flex gap-4">
            <input
              type="email"
              placeholder="Email"
              class="flex-1 px-6 py-3 rounded-full bg-white/10 text-white placeholder-gray-400 border border-white/20 focus:outline-none focus:border-[#8247E5]"
            />
            <button
              type="submit"
              class="px-8 py-3 bg-white text-[#3B0764] rounded-full hover:bg-gray-100 transition-all font-semibold whitespace-nowrap"
            >
              GET UPDATES!
            </button>
          </form>
        </div>
      </div>
    </div>

    <!-- Copyright -->
    <div class="flex flex-wrap gap-8 text-sm text-gray-400">
      <span>© 2025 DoxaV3</span>
      <a href="/terms" class="hover:text-white transition-colors"
        >Terms of Use</a
      >
      <a href="/privacy" class="hover:text-white transition-colors"
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
</style>
