<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
</script>

<svelte:head>
  <title>DoxaV3 Partners - Building the Future of DeFi Together</title>
  <meta
    name="description"
    content="Explore DoxaV3's strategic partnerships and integrations in the DeFi ecosystem."
  />
</svelte:head>

<main>
  <!-- Hero Section -->
  <section
    class="min-h-[60vh] relative flex items-center bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] overflow-hidden pt-32"
  >
    <!-- Background Grid Pattern -->
    <div class="absolute inset-0 bg-grid opacity-10"></div>

    <!-- Purple Glow Effects -->
    <div
      class="absolute top-20 -left-32 w-96 h-96 bg-purple-500 rounded-full filter blur-[128px] opacity-20"
    ></div>
    <div
      class="absolute bottom-0 right-0 w-96 h-96 bg-indigo-500 rounded-full filter blur-[128px] opacity-20"
    ></div>

    <div class="relative max-w-7xl mx-auto px-4 py-20 text-center">
      <h1 class="text-4xl md:text-6xl font-bold text-white mb-8 relative z-10">
        Building the Future of
        <span
          class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-purple-600"
          >DeFi Together</span
        >
      </h1>
      <p class="text-xl text-gray-300 max-w-3xl mx-auto mb-12 relative z-10">
        Join the growing ecosystem of partners leveraging DoxaV3's revolutionary
        stablecoin infrastructure to build innovative DeFi solutions.
      </p>
      <div class="flex flex-wrap justify-center gap-4 relative z-10">
        <a
          href="#become-partner"
          class="px-8 py-4 bg-[#8247E5] text-white rounded-xl hover:bg-[#6d35c7] transition-all"
        >
          Become a Partner
        </a>
        <a
          href="https://doxa-1.gitbook.io/doxa-guide"
          target="_blank"
          rel="noopener"
          class="px-8 py-4 bg-white/10 backdrop-blur-sm text-white rounded-xl border border-white/20 hover:bg-white/20 transition-all"
        >
          View Documentation
        </a>
      </div>
    </div>
  </section>

  <!-- Current Partners -->
  <section class="py-20 bg-[#1a0f3d] relative">
    <!-- Background Effects -->
    <div class="absolute inset-0 bg-grid opacity-5"></div>
    <div
      class="absolute top-0 right-0 w-96 h-96 bg-purple-500 rounded-full filter blur-[128px] opacity-10"
    ></div>

    <div class="relative max-w-7xl mx-auto px-4">
      <h2
        class="text-3xl md:text-4xl font-bold text-center mb-16 text-white relative z-10"
      >
        Trusted by Industry Leaders
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 relative z-10">
        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <img
            src="/partners/ic.svg"
            alt="Internet Computer"
            class="h-10 mb-6"
          />
          <h3 class="text-xl font-bold mb-3 text-white">Internet Computer</h3>
          <p class="text-gray-200 mb-6 leading-relaxed">
            Built natively on the Internet Computer blockchain, leveraging its
            unique capabilities for true decentralization.
          </p>
          <a
            href="https://internetcomputer.org"
            target="_blank"
            class="inline-flex items-center text-purple-300 hover:text-purple-200"
          >
            Learn More
            <svg class="w-4 h-4 ml-1" viewBox="0 0 20 20" fill="currentColor">
              <path
                fill-rule="evenodd"
                d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
                clip-rule="evenodd"
              />
            </svg>
          </a>
        </div>

        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <img src="/partners/sonic.svg" alt="Sonic DEX" class="h-10 mb-6" />
          <h3 class="text-xl font-bold mb-3 text-white">Sonic DEX</h3>
          <p class="text-gray-200 mb-6 leading-relaxed">
            Integrated with Sonic DEX for seamless swaps and liquidity provision
            in the DeFi ecosystem.
          </p>
          <a
            href="https://sonic.ooo"
            target="_blank"
            class="inline-flex items-center text-purple-300 hover:text-purple-200"
          >
            Learn More
            <svg class="w-4 h-4 ml-1" viewBox="0 0 20 20" fill="currentColor">
              <path
                fill-rule="evenodd"
                d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
                clip-rule="evenodd"
              />
            </svg>
          </a>
        </div>

        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <img
            src="/partners/icrc.svg"
            alt="ICRC Token Standard"
            class="h-10 mb-6"
          />
          <h3 class="text-xl font-bold mb-3 text-white">ICRC Token Standard</h3>
          <p class="text-gray-200 mb-6 leading-relaxed">
            Compliant with the ICRC token standard, ensuring compatibility and
            interoperability across the IC ecosystem.
          </p>
          <a
            href="https://internetcomputer.org/docs/current/developer-docs/integrations/icrc-1"
            target="_blank"
            class="inline-flex items-center text-purple-300 hover:text-purple-200"
          >
            Learn More
            <svg class="w-4 h-4 ml-1" viewBox="0 0 20 20" fill="currentColor">
              <path
                fill-rule="evenodd"
                d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
                clip-rule="evenodd"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>

  <!-- Benefits -->
  <section class="py-24 bg-[#110a29] relative">
    <!-- Background Effects -->
    <div class="absolute inset-0 bg-grid opacity-5"></div>
    <div
      class="absolute bottom-0 left-0 w-96 h-96 bg-purple-500 rounded-full filter blur-[128px] opacity-10"
    ></div>

    <div class="relative max-w-7xl mx-auto px-4">
      <h2 class="text-3xl md:text-4xl font-bold text-center mb-16 text-white">
        Benefits of Partnership
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <!-- Fast Integration -->
        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <div
            class="w-14 h-14 bg-[#8247E5]/30 rounded-xl flex items-center justify-center mb-6"
          >
            <svg
              class="w-7 h-7 text-purple-300"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M13 10V3L4 14h7v7l9-11h-7z"
              />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-4 text-white">
            Fast Integration
          </h3>
          <p class="text-gray-200 leading-relaxed">
            Quick and easy integration with comprehensive documentation and
            dedicated support.
          </p>
        </div>

        <!-- Enhanced Security -->
        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <div
            class="w-14 h-14 bg-[#8247E5]/30 rounded-xl flex items-center justify-center mb-6"
          >
            <svg
              class="w-7 h-7 text-purple-300"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"
              />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-4 text-white">
            Enhanced Security
          </h3>
          <p class="text-gray-200 leading-relaxed">
            Benefit from our rigorous security measures and audited smart
            contracts.
          </p>
        </div>

        <!-- Community Access -->
        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <div
            class="w-14 h-14 bg-[#8247E5]/30 rounded-xl flex items-center justify-center mb-6"
          >
            <svg
              class="w-7 h-7 text-purple-300"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"
              />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-4 text-white">
            Community Access
          </h3>
          <p class="text-gray-200 leading-relaxed">
            Join a thriving ecosystem of DeFi innovators and developers.
          </p>
        </div>

        <!-- Liquidity Access -->
        <div
          class="bg-[#2D1B69]/50 backdrop-blur-sm p-8 rounded-xl hover:bg-[#2D1B69]/70 transition-all border border-white/10"
        >
          <div
            class="w-14 h-14 bg-[#8247E5]/30 rounded-xl flex items-center justify-center mb-6"
          >
            <svg
              class="w-7 h-7 text-purple-300"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
              />
            </svg>
          </div>
          <h3 class="text-xl font-semibold mb-4 text-white">
            Liquidity Access
          </h3>
          <p class="text-gray-200 leading-relaxed">
            Access to deep liquidity pools and stable trading pairs.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- Become a Partner -->
  <section
    id="become-partner"
    class="relative py-24 bg-gradient-to-br from-[#2D1B69] to-[#1a0f3d] overflow-hidden"
  >
    <!-- Background Effects -->
    <div class="absolute inset-0 bg-grid opacity-10"></div>
    <div
      class="absolute top-0 right-0 w-96 h-96 bg-purple-500 rounded-full filter blur-[128px] opacity-20"
    ></div>
    <div
      class="absolute bottom-0 left-0 w-96 h-96 bg-indigo-500 rounded-full filter blur-[128px] opacity-20"
    ></div>

    <div class="relative max-w-4xl mx-auto px-4 text-center">
      <h2 class="text-3xl md:text-5xl font-bold text-white mb-8">
        Ready to Build the Future?
      </h2>
      <p class="text-xl text-gray-300 mb-12 max-w-2xl mx-auto">
        Join us in revolutionizing DeFi. Partner with DoxaV3 to bring stability
        and innovation to your projects.
      </p>
      <div class="flex flex-wrap justify-center gap-6">
        <a
          href="mailto:doxadaooperations@gmail.com"
          class="px-8 py-4 bg-[#8247E5] text-white rounded-xl hover:bg-[#6d35c7] transition-all text-lg"
        >
          Contact Us
        </a>
        <a
          href="https://doxa-1.gitbook.io/doxa-guide"
          target="_blank"
          rel="noopener"
          class="px-8 py-4 bg-white/10 backdrop-blur-sm text-white rounded-xl border border-white/20 hover:bg-white/20 transition-all text-lg"
        >
          Read Documentation
        </a>
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
