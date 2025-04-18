<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    if (gsap && ScrollTrigger) {
      initAnimations();
    }
  });

  function initAnimations() {
    if (!gsap || !ScrollTrigger) return;

    // Animation for step cards
    const stepCards = document.querySelectorAll(".step-card");
    gsap.from(stepCards, {
      scrollTrigger: {
        trigger: ".steps-grid", // Trigger when the grid comes into view
        start: "top 80%",
        toggleActions: "play none none reverse",
      },
      duration: 1,
      y: 50,
      opacity: 0,
      stagger: 0.2,
      ease: "power3.out",
    });

    // Animation for titles and subtitles (including new sections content)
    gsap.from(
      ".section-title, .section-subtitle, .conclusion-text, .new-section-title, .new-section-content",
      {
        scrollTrigger: {
          trigger: ".section-title", // Keep the main trigger
          start: "top 85%",
          toggleActions: "play none none reverse",
        },
        duration: 1,
        y: 30,
        opacity: 0,
        ease: "power3.out",
        stagger: 0.15,
      }
    );
  }
</script>

<section class="py-24 md:py-32 relative overflow-hidden bg-gray-100">
  <div class="absolute inset-0 bg-grid opacity-20"></div>

  <div class="relative container mx-auto px-6">
    <h2
      class="section-title text-4xl md:text-5xl font-bold text-center text-gray-900 mb-4"
    >
      🧠 How It Works
    </h2>
    <p
      class="section-subtitle text-xl md:text-2xl text-center text-gray-600 mb-6 max-w-2xl mx-auto"
    >
      One protocol. Three core canisters.
    </p>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 steps-grid mb-12">
      <div class="step-card">
        <div class="step-icon">✅</div>
        <h3 class="step-title">Stablecoin Minter</h3>
        <p class="step-description">
          You deposit collateral (ICP, ckBTC, ckETH)
        </p>
      </div>
      <div class="step-card">
        <div class="step-icon">✅</div>
        <h3 class="step-title">Reserve Pool</h3>
        <p class="step-description">
          Collateral is converted to ckUSDC and locked
        </p>
      </div>
      <div class="step-card">
        <div class="step-icon">✅</div>
        <h3 class="step-title">DoxaUSD (USDx)</h3>
        <p class="step-description">Instantly minted and sent to your wallet</p>
      </div>
    </div>

    <p class="conclusion-text text-lg mt-8 mb-10 text-center text-gray-600">
      And the peg? Maintained 24/7 by an intelligent ckUSDC pool.
    </p>

    <!-- Visual Separator -->
    <div
      class="my-12 h-px bg-gradient-to-r from-transparent via-gray-300 to-transparent"
    ></div>

    <!-- New Sections Start -->
    <div class="space-y-12">
      <!-- Transparency Section -->
      <div class="info-card transparency-section max-w-4xl mx-auto">
        <h3
          class="new-section-title text-3xl md:text-4xl font-bold text-gray-900 mb-6"
        >
          🛡️ Transparent. Auditable. Decentralized.
        </h3>
        <ul
          class="new-section-content space-y-3 text-lg text-gray-700 mb-4 list-none p-0"
        >
          <li>🧾 Real-Time Reserve Dashboards</li>
          <li>🔐 Regular Security Audits</li>
          <li>📖 Open-Source Smart Contracts</li>
          <li>💼 DAO Governance via SNS</li>
        </ul>
        <p class="new-section-content text-xl text-gray-700 italic">
          You deserve to see what backs your money. With Doxa, you do.
        </p>
      </div>

      <!-- Staking Section -->
      <div class="info-card staking-section max-w-4xl mx-auto">
        <h3
          class="new-section-title text-3xl md:text-4xl font-bold text-gray-900 mb-6"
        >
          🌱 Stake. Earn. Grow.
        </h3>
        <p class="new-section-content text-lg text-gray-700 mb-4">
          Doxa isn't just about spending—it's about growing your assets.
        </p>
        <p class="new-section-content text-lg text-gray-700 mb-6">
          Stake and lock your DoxaUSD to earn real yield from protocol revenue
          and future staking rewards.
        </p>
        <ul
          class="new-section-content space-y-3 text-lg text-gray-700 mb-4 list-none p-0 font-medium"
        >
          <li>
            💰 <span class="text-gray-500">30%</span> of all protocol fees
          </li>
          <li>
            🌐 Yield from <span class="text-gray-500">ICP Neuron</span> staking
          </li>
          <li>📈 Passive income, powered by decentralization</li>
        </ul>
      </div>

      <!-- Regulation Section -->
      <div class="info-card regulation-section max-w-4xl mx-auto">
        <h3
          class="new-section-title text-3xl md:text-4xl font-bold text-gray-900 mb-6"
        >
          🏛️ Regulated, Without Compromise
        </h3>
        <p class="new-section-content text-lg text-gray-700 mb-6">
          We believe decentralization and compliance can co-exist.
        </p>
        <p class="new-section-content text-lg text-gray-700 mb-2 font-semibold">
          🔍 Committed to obtaining:
        </p>
        <ul
          class="new-section-content space-y-2 text-lg text-gray-700 mb-6 list-none p-0"
        >
          <li>FSCA, FCA, FINMA, NYDFS licenses</li>
          <li>ISO 20022 & ISO 22739 financial messaging standards</li>
        </ul>
        <p class="new-section-content text-xl text-gray-700 italic">
          Doxa is your bridge between the decentralized world and traditional
          finance.
        </p>
      </div>
    </div>
    <!-- New Sections End -->
  </div>
</section>

<style>
  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(51, 51, 51, 0.1) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(51, 51, 51, 0.1) 1px, transparent 1px);
  }

  .step-card {
    @apply p-8 rounded-2xl bg-white/50 backdrop-blur-xl border-2 border-gray-300 hover:border-gray-200 transition-all duration-500 text-center transform hover:-translate-y-2 hover:shadow-light-glow;
  }

  .step-icon {
    @apply text-4xl mb-4 inline-block;
  }

  .step-title {
    @apply text-xl font-semibold text-gray-900 mb-3;
  }

  .step-description {
    @apply text-gray-700;
  }

  .info-card {
    @apply p-8 md:p-10 rounded-2xl bg-white/50 backdrop-blur-xl border-2 border-gray-300 hover:border-gray-200 transition-all duration-500 text-center transform hover:-translate-y-1 hover:shadow-light-glow;
  }

  /* Styles for new sections */
  .new-section-title {
    @apply text-shadow-light;
  }

  .new-section-content li::before {
    content: "✓";
    @apply mr-2 text-gray-500 inline-block;
  }

  /* Optional: Add a text shadow for titles */
  .text-shadow-light {
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }

  /* Custom glow effect for cards on hover */
  @tailwind utilities;
  @layer utilities {
    /* Define base utility */
    .shadow-light-glow {
      box-shadow: 0 0 20px 5px rgba(0, 0, 0, 0.08);
    }
  }
</style>
