<script lang="ts">
  import { page } from "$app/stores";
</script>

<div class="max-w-4xl mx-auto px-4 py-32">
  <h1 class="text-4xl font-bold mb-8">
    The Future of Stablecoins on Internet Computer
  </h1>
  <p class="text-gray-400 mb-8">January 5, 2025</p>

  <div class="prose prose-lg prose-invert">
    <p>
      The Internet Computer ecosystem is poised for a revolution in stablecoin
      technology. DoxaV3 is leading the way with its innovative approach to
      price stability and decentralization.
    </p>

    <h2>Key Innovations</h2>
    <ul>
      <li>Self-stabilizing mechanisms</li>
      <li>Zero collateral requirements</li>
      <li>Instant finality</li>
      <li>Low transaction costs</li>
    </ul>

    <p>Join us in shaping the future of decentralized finance.</p>
  </div>

  <div class="mt-12">
    <a href="/news" class="text-purple-400 hover:text-purple-300"
      >← Back to News</a
    >
  </div>
</div>

<style lang="postcss">
  :global(body) {
    @apply bg-gradient-to-br from-slate-100 to-slate-200 text-gray-800 min-h-screen;
  }

  article {
    @apply prose prose-lg;
  }

  /* Add shiny effects */
  .max-w-4xl {
    @apply shadow-xl rounded-lg backdrop-blur-sm bg-white/70 border border-white/50;
  }

  h1 {
    @apply bg-gradient-to-r from-gray-600 to-gray-800 bg-clip-text text-transparent drop-shadow-sm;
  }

  .prose {
    @apply text-gray-700;
  }

  a {
    @apply text-gray-600 hover:text-gray-800 transition-colors relative;
  }

  a::after {
    content: "";
    @apply absolute bottom-0 left-0 w-full h-0.5 bg-gradient-to-r from-gray-400 to-gray-600 scale-x-0 origin-bottom-left transition-transform duration-300;
  }

  a:hover::after {
    @apply scale-x-100;
  }
</style>
