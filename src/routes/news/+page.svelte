<script lang="ts">
  import { page } from "$app/stores";
</script>

<div class="max-w-7xl mx-auto px-4 py-32">
  <h1 class="text-4xl font-bold mb-8">DoxaV3 News</h1>
  <p class="text-xl mb-4">
    Latest updates and announcements from the DoxaV3 team.
  </p>

  <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mt-12">
    <a
      href="/news/first-algorithmic-stablecoin"
      class="p-6 rounded-lg bg-slate-300 hover:bg-slate-400"
    >
      <h2 class="text-2xl font-bold mb-2">
        DoxaV3: The First Algorithmic Stablecoin on Internet Computer
      </h2>
      <p class="text-gray-300">Jan 20, 2025</p>
    </a>

    <a
      href="/news/price-stability"
      class="p-6 rounded-lg bg-slate-300 hover:bg-slate-400"
    >
      <h2 class="text-2xl font-bold mb-2">
        How DoxaV3 Maintains Price Stability Through Smart Contracts
      </h2>
      <p class="text-gray-300">Jan 15, 2025</p>
    </a>

    <a
      href="/news/defi-protocols"
      class="p-6 rounded-lg bg-slate-300 hover:bg-slate-400"
    >
      <h2 class="text-2xl font-bold mb-2">
        DoxaV3 Partners with Major DeFi Protocols
      </h2>
      <p class="text-gray-300">Jan 10, 2025</p>
    </a>

    <a
      href="/news/future-stablecoins"
      class="p-6 rounded-lg bg-slate-300 hover:bg-slate-400"
    >
      <h2 class="text-2xl font-bold mb-2">
        The Future of Stablecoins on Internet Computer
      </h2>
      <p class="text-gray-300">Jan 5, 2025</p>
    </a>
  </div>
</div>

<style lang="postcss">
  :global(body) {
    @apply bg-gradient-to-br from-slate-100 to-slate-200 text-gray-800 min-h-screen;
  }

  /* Shiny styles */
  h1 {
    @apply bg-gradient-to-r from-gray-600 to-gray-800 bg-clip-text text-transparent drop-shadow-sm;
  }

  .max-w-7xl {
    @apply pt-24 pb-16;
  }

  a {
    @apply border border-white/50 shadow-lg transition-all duration-300 backdrop-blur-sm bg-gradient-to-br from-slate-200/80 to-slate-300/80 text-gray-700;
  }

  a:hover {
    @apply shadow-xl translate-y-[-5px] bg-gradient-to-br from-slate-300/90 to-slate-400/90;
  }

  a h2 {
    @apply bg-gradient-to-r from-gray-700 to-gray-800 bg-clip-text text-transparent;
  }

  p {
    @apply text-gray-600;
  }
</style>
