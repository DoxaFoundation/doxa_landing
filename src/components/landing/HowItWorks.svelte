<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
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

<section class="py-24 md:py-32 relative overflow-hidden bg-primary-800">
  <div class="absolute inset-0 bg-grid opacity-10"></div>

  <div class="relative container mx-auto px-6">
    <h2
      class="section-title text-4xl md:text-5xl font-bold text-center text-primary-100 mb-4"
    >
      🧠 How It Works
    </h2>
    <p
      class="section-subtitle text-xl md:text-2xl text-center text-primary-300 mb-6 max-w-2xl mx-auto"
    >
      One protocol. Three core canisters.
    </p>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-10 steps-grid mb-16 mt-8">
      <div class="step-card p-8 rounded-2xl bg-primary-700/40 backdrop-blur-lg border border-primary-500/40 transition-all duration-300 hover:-translate-y-2 hover:bg-primary-700/60 hover:border-primary-400 shadow-lg" style="opacity: 1; transform: translateY(0);">
        <div class="step-icon text-5xl mb-6 text-primary-300">✅</div>
        <h3 class="step-title text-primary-100 text-2xl font-semibold mb-4">Stablecoin Minter</h3>
        <p class="step-description text-primary-200 text-lg leading-relaxed">
          You deposit collateral (ICP, ckBTC, ckETH)
        </p>
      </div>
      <div class="step-card p-8 rounded-2xl bg-primary-700/40 backdrop-blur-lg border border-primary-500/40 transition-all duration-300 hover:-translate-y-2 hover:bg-primary-700/60 hover:border-primary-400 shadow-lg" style="opacity: 1; transform: translateY(0);">
        <div class="step-icon text-5xl mb-6 text-primary-300">✅</div>
        <h3 class="step-title text-primary-100 text-2xl font-semibold mb-4">Reserve Pool</h3>
        <p class="step-description text-primary-200 text-lg leading-relaxed">
          Collateral is converted to ckUSDC and locked
        </p>
      </div>
      <div class="step-card p-8 rounded-2xl bg-primary-700/40 backdrop-blur-lg border border-primary-500/40 transition-all duration-300 hover:-translate-y-2 hover:bg-primary-700/60 hover:border-primary-400 shadow-lg" style="opacity: 1; transform: translateY(0);">
        <div class="step-icon text-5xl mb-6 text-primary-300">✅</div>
        <h3 class="step-title text-primary-100 text-2xl font-semibold mb-4">DoxaUSD (USDx)</h3>
        <p class="step-description text-primary-200 text-lg leading-relaxed">
          Instantly minted and sent to your wallet
        </p>
      </div>
    </div>

    <p class="conclusion-text text-lg mt-8 mb-10 text-center text-primary-300">
      And the peg? Maintained 24/7 by an intelligent ckUSDC pool.
    </p>

    <!-- Visual Separator -->
    <div
      class="my-12 h-px bg-gradient-to-r from-transparent via-primary-400 to-transparent"
    ></div>

    <!-- New Sections Start -->
    <div class="space-y-12">
      <!-- Transparency Section -->
      <div class="info-card transparency-section max-w-4xl mx-auto">
        <h3
          class="new-section-title text-3xl md:text-4xl font-bold text-primary-100 mb-6"
        >
          🛡️ Transparent. Auditable. Decentralized.
        </h3>
        <ul
          class="new-section-content space-y-3 text-lg text-primary-200 mb-4 list-none p-0"
        >
          <li>🧾 Real-Time Reserve Dashboards</li>
          <li>🔐 Regular Security Audits</li>
          <li>📖 Open-Source Smart Contracts</li>
          <li>💼 DAO Governance via SNS</li>
        </ul>
        <p class="new-section-content text-xl text-primary-300 italic">
          You deserve to see what backs your money. With Doxa, you do.
        </p>
      </div>

      <!-- Staking Section -->
      <div class="info-card staking-section max-w-4xl mx-auto">
        <h3
          class="new-section-title text-3xl md:text-4xl font-bold text-primary-100 mb-6"
        >
          🌱 Stake. Earn. Grow.
        </h3>
        <p class="new-section-content text-lg text-primary-200 mb-4">
          Doxa isn't just about spending—it's about growing your assets.
        </p>
        <p class="new-section-content text-lg text-primary-200 mb-6">
          Stake and lock your DoxaUSD to earn real yield from protocol revenue
          and future staking rewards.
        </p>
        <ul
          class="new-section-content space-y-3 text-lg text-primary-200 mb-4 list-none p-0 font-medium"
        >
          <li>
            💰 <span class="text-primary-400">30%</span> of all protocol fees
          </li>
          <li>
            🌐 Yield from <span class="text-primary-400">ICP Neuron</span> staking
          </li>
          <li>📈 Passive income, powered by decentralization</li>
        </ul>
      </div>

      <!-- Regulation Section -->
      <div class="info-card regulation-section max-w-4xl mx-auto">
        <h3
          class="new-section-title text-3xl md:text-4xl font-bold text-primary-100 mb-6"
        >
          🏛️ Regulated, Without Compromise
        </h3>
        <p class="new-section-content text-lg text-primary-200 mb-6">
          We believe decentralization and compliance can co-exist.
        </p>
        <p
          class="new-section-content text-lg text-primary-200 mb-2 font-semibold"
        >
          🔍 Committed to obtaining:
        </p>
        <ul
          class="new-section-content space-y-2 text-lg text-primary-200 mb-6 list-none p-0"
        >
          <li>FSCA, FCA, FINMA, NYDFS licenses</li>
          <li>ISO 20022 & ISO 22739 financial messaging standards</li>
        </ul>
        <p class="new-section-content text-xl text-primary-300 italic">
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
        theme("colors.primary.300 / 7%") 1px,
        transparent 1px
      ),
      linear-gradient(
        to bottom,
        theme("colors.primary.300 / 7%") 1px,
        transparent 1px
      );
  }

  .step-card {
    @apply p-8 rounded-2xl bg-primary-800/50 backdrop-blur-xl border-primary-600/50 hover:border-primary-400 transition-all duration-500 text-center transform hover:-translate-y-2 hover:shadow-primary-glow-dark;
  }

  .step-icon {
    @apply text-primary-200;
  }

  .step-title {
    @apply text-xl font-semibold text-white mb-3;
  }

  .step-description {
    @apply text-gray-300;
  }

  .info-card {
    @apply p-8 md:p-10 rounded-2xl bg-primary-700/50 backdrop-blur-xl border-primary-500/50 hover:border-primary-300 transition-all duration-500 text-center transform hover:-translate-y-1 hover:shadow-primary-glow-light;
  }

  /* Styles for new sections */
  .new-section-title {
    @apply text-shadow-primary;
  }

  .new-section-content li::before {
    content: "✓";
    @apply mr-2 text-primary-400 inline-block;
  }

  /* Optional: Add a text shadow for titles */
  .text-shadow-primary {
    text-shadow: 0 2px 15px theme("colors.primary.300 / 30%");
  }

  /* Custom glow effect for cards on hover */
  @tailwind utilities;
  @layer utilities {
    /* Renamed and use Tailwind color */
    .shadow-primary-glow-dark {
      box-shadow: 0 0 25px 5px theme("colors.primary.400 / 40%");
    }
    /* Renamed and use Tailwind color */
    .shadow-primary-glow-light {
      box-shadow: 0 0 25px 5px theme("colors.primary.300 / 40%");
    }
  }
</style>
