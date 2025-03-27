<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
</script>

# New File Content
<svelte:head>
  <title>DoxaV3 Mechanism - How It Works</title>
  <meta
    name="description"
    content="Learn about DoxaV3's algorithmic stability mechanism and how it maintains price stability"
  />
</svelte:head>

<main class="pt-32 pb-20">
  <div class="max-w-7xl mx-auto px-4">
    <!-- Hero Section -->
    <div class="text-center mb-16">
      <h1 class="text-5xl font-bold mb-6">
        How <span class="text-[#8247E5]">DoxaV3</span> Works
      </h1>
      <p class="text-xl text-gray-600 max-w-3xl mx-auto">
        Understand the innovative mechanisms behind DoxaV3's price stability and
        algorithmic design
      </p>
    </div>

    <!-- Main Content -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-16 mb-20">
      <!-- Left Column -->
      <div class="space-y-8">
        <div class="bg-white rounded-2xl shadow-lg p-8">
          <h2 class="text-2xl font-bold mb-4">Price Stability Mechanism</h2>
          <p class="text-gray-600 mb-6">
            DoxaV3 uses an advanced algorithmic mechanism to maintain its 1:1
            USD peg:
          </p>
          <ul class="space-y-4 text-gray-600">
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span
                >Supply Adjustment: Smart contracts automatically adjust token
                supply based on market demand</span
              >
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span
                >Zero Collateral: Pure algorithmic design eliminates the need
                for collateral backing</span
              >
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span
                >Market Incentives: Arbitrage opportunities help maintain the
                peg</span
              >
            </li>
          </ul>
        </div>

        <div class="bg-white rounded-2xl shadow-lg p-8">
          <h2 class="text-2xl font-bold mb-4">Staking & Rewards</h2>
          <p class="text-gray-600 mb-6">
            Participate in DoxaV3's staking program to earn rewards and help
            maintain stability:
          </p>
          <ul class="space-y-4 text-gray-600">
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Earn weekly DOXA rewards for staking your tokens</span>
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Participate in governance decisions</span>
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Access to exclusive features and benefits</span>
            </li>
          </ul>
        </div>
      </div>

      <!-- Right Column -->
      <div class="space-y-8">
        <div class="bg-white rounded-2xl shadow-lg p-8">
          <h2 class="text-2xl font-bold mb-4">Smart Contract Architecture</h2>
          <p class="text-gray-600 mb-6">
            DoxaV3's smart contracts are built on Internet Computer with
            security and efficiency in mind:
          </p>
          <ul class="space-y-4 text-gray-600">
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Modular design for easy upgrades and maintenance</span>
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Rigorous security measures and audits</span>
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Transparent and verifiable code</span>
            </li>
          </ul>
        </div>

        <div class="bg-white rounded-2xl shadow-lg p-8">
          <h2 class="text-2xl font-bold mb-4">Integration & Development</h2>
          <p class="text-gray-600 mb-6">
            Build on top of DoxaV3 with our comprehensive development tools:
          </p>
          <ul class="space-y-4 text-gray-600">
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Easy-to-use SDK and APIs</span>
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Comprehensive documentation</span>
            </li>
            <li class="flex items-start gap-3">
              <svg
                class="w-6 h-6 text-[#8247E5] mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <span>Active developer community</span>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <!-- CTA Section -->
    <div class="text-center">
      <a
        href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="inline-block px-8 py-4 bg-[#8247E5] text-white rounded-xl hover:bg-[#6d35c7] transition-all text-xl font-medium"
      >
        Start Building Now
      </a>
    </div>
  </div>
</main>
