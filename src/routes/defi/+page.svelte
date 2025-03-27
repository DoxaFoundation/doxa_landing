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
  <title>DoxaV3 - Making DeFi Immune to Volatility</title>
  <meta
    name="description"
    content="Learn how DoxaV3 is revolutionizing DeFi with its innovative stablecoin solution on the Internet Computer."
  />
</svelte:head>

<main class="pt-4 pb-20">
  <!-- Hero Section -->
  <section
    class="relative overflow-hidden bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] text-white"
  >
    <div class="absolute inset-0 bg-grid opacity-10"></div>
    <div class="max-w-7xl mx-auto px-4 py-20">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
        <div>
          <h1 class="text-5xl font-bold mb-6">
            Making DeFi <br />
            <span class="text-[#8247E5]">Immune to Volatility</span>
          </h1>
          <p class="text-xl text-white/90 mb-8">
            Experience the future of decentralized finance with DoxaV3's
            innovative stablecoin solution, designed to eliminate volatility
            while maintaining true decentralization.
          </p>
          <div class="flex gap-4">
            <a
              href="../mechanism"
              class="px-8 py-4 bg-[#8247E5] text-white rounded-xl hover:bg-[#6d35c7] transition-all"
            >
              Learn How It Works
            </a>
            <a
              href="https://i7m4z-gqaaa-aaaak-qddtq-cai.icp0.io/"
              target="_blank"
              rel="noopener"
              class="px-8 py-4 bg-white/10 backdrop-blur-sm text-white rounded-xl border border-white/20 hover:bg-white/20 transition-all"
            >
              Launch App
            </a>
          </div>
        </div>
        <div class="relative">
          <div
            class="aspect-square bg-white/5 rounded-full flex items-center justify-center"
          >
            <div
              class="text-[12rem] font-bold text-white/10 transform -rotate-12"
            >
              USDX
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Features Section -->
  <section class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4">
      <h2 class="text-3xl font-bold text-center mb-16">Key Features</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div
          class="p-8 bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] rounded-2xl text-white"
        >
          <h3 class="text-xl font-semibold mb-4">Price Stability</h3>
          <p>
            Advanced algorithmic mechanisms maintain a reliable 1:1 peg with USD
            through automated supply adjustments.
          </p>
        </div>
        <div
          class="p-8 bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] rounded-2xl text-white"
        >
          <h3 class="text-xl font-semibold mb-4">Zero Collateral</h3>
          <p>
            Pure algorithmic design eliminates the need for collateral backing,
            ensuring true decentralization.
          </p>
        </div>
        <div
          class="p-8 bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] rounded-2xl text-white"
        >
          <h3 class="text-xl font-semibold mb-4">Smart Contract Security</h3>
          <p>
            Built on Internet Computer with rigorous security measures and
            comprehensive audits.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- How It Works -->
  <section class="py-20 bg-gray-50">
    <div class="max-w-7xl mx-auto px-4">
      <h2 class="text-3xl font-bold text-center mb-16">How It Works</h2>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
        <div class="space-y-8">
          <div>
            <h3 class="text-2xl font-semibold mb-4">Supply Adjustment</h3>
            <p class="text-gray-600">
              Smart contracts automatically adjust token supply based on market
              demand, ensuring price stability without manual intervention.
            </p>
          </div>
          <div>
            <h3 class="text-2xl font-semibold mb-4">Market Incentives</h3>
            <p class="text-gray-600">
              Arbitrage opportunities and staking rewards create natural market
              forces that help maintain the peg.
            </p>
          </div>
          <div>
            <h3 class="text-2xl font-semibold mb-4">Governance</h3>
            <p class="text-gray-600">
              Community-driven governance ensures transparency and decentralized
              decision-making.
            </p>
          </div>
        </div>
        <div class="bg-white p-8 rounded-2xl shadow-lg">
          <pre
            class="bg-gray-900 text-green-400 p-6 rounded-xl overflow-x-auto">{`// Price Stability Mechanism
actor DoxaStability {
    stable var TARGET_PRICE = 1_000_000; // $1 with 6 decimal places
    
    public shared func adjustSupply() : async () {
        var currentPrice = await getMarketPrice();
        
        if (currentPrice > TARGET_PRICE) {
            // Increase supply to reduce price
            await mintTokens();
        } else if (currentPrice < TARGET_PRICE) {
            // Decrease supply to increase price
            await burnTokens();
        };
    };
}`}</pre>
        </div>
      </div>
    </div>
  </section>

  <!-- Integration -->
  <section
    class="py-20 bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] text-white"
  >
    <div class="max-w-7xl mx-auto px-4">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-4xl font-bold mb-6">Ready to Build?</h2>
        <p class="text-xl text-gray-300 mb-8">
          Integrate DoxaV3 into your DeFi applications with our comprehensive
          SDK and documentation.
        </p>
        <div class="flex gap-4 justify-center">
          <a
            href="/build"
            class="px-8 py-4 bg-[#8247E5] text-white rounded-xl hover:bg-[#6d35c7] transition-all"
          >
            Start Building
          </a>
          <a
            href="https://doxa-1.gitbook.io/doxa-guide"
            target="_blank"
            rel="noopener"
            class="px-8 py-4 bg-white/10 backdrop-blur-sm text-white rounded-xl border border-white/20 hover:bg-white/20 transition-all"
          >
            Read Documentation
          </a>
        </div>
      </div>
    </div>
  </section>
</main>

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
</style>
