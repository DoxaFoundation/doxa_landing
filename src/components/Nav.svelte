<script lang="ts">
  let isMenuOpen = false;
</script>

<!-- Navigation -->
<header class="fixed top-0 left-0 right-0 z-[9999] bg-transparent">
  <nav class="max-w-7xl mx-auto px-6 h-20 flex justify-between items-center">
    <a
      href="/"
      class="flex items-center text-2xl font-bold text-gray-900 font-['Space_Grotesk']"
    >
      <img src="/images/DOXA.svg" alt="Doxa Logo" class="h-8 mr-2" />
      Doxa
    </a>

    <!-- Mobile Menu Button -->
    <button
      class="md:hidden text-gray-900"
      on:click={() => (isMenuOpen = !isMenuOpen)}
      aria-label="Toggle menu"
    >
      <svg
        class="w-6 h-6"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
      >
        {#if isMenuOpen}
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M6 18L18 6M6 6l12 12"
          />
        {:else}
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        {/if}
      </svg>
    </button>

    <!-- Desktop Navigation -->
    <div class="hidden md:flex items-center gap-8">
      <a
        href="/partners"
        class="text-gray-700 hover:text-gray-900 font-['Inter'] font-medium transition-colors"
        >Partners</a
      >
      <a
        href="https://doxa-1.gitbook.io/doxa-guide"
        target="_blank"
        rel="noopener"
        class="text-gray-700 hover:text-gray-900 font-['Inter'] font-medium transition-colors"
        >Use</a
      >
      <a
        href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="text-gray-700 hover:text-gray-900 font-['Inter'] font-medium transition-colors"
        >Developer</a
      >
      <a
        href="https://app.doxadao.org"
        target="_blank"
        rel="noopener"
        class="inline-flex items-center justify-center px-6 py-2 bg-gray-200 hover:bg-gray-300 text-gray-800 rounded-full font-medium transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-gray-400/30"
        >Launch App</a
      >
    </div>

    <!-- Mobile Navigation -->
    {#if isMenuOpen}
      <div class="absolute top-full left-0 right-0 bg-gray-50 md:hidden">
        <div class="flex flex-col items-center gap-4 py-4">
          <a
            href="/partners"
            class="text-gray-700 hover:text-gray-900 font-['Inter'] font-medium transition-colors"
            >Partners</a
          >
          <a
            href="https://doxa-1.gitbook.io/doxa-guide"
            target="_blank"
            rel="noopener"
            class="text-gray-700 hover:text-gray-900 font-['Inter'] font-medium transition-colors"
            >Use</a
          >
          <a
            href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
            target="_blank"
            rel="noopener"
            class="text-gray-700 hover:text-gray-900 font-['Inter'] font-medium transition-colors"
            >Developer</a
          >
          <a
            href="https://app.doxadao.org"
            target="_blank"
            rel="noopener"
            class="inline-flex items-center justify-center px-6 py-2 bg-gray-200 hover:bg-gray-300 text-gray-800 rounded-full font-medium transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-gray-400/30"
            >Launch App</a
          >
        </div>
      </div>
    {/if}
  </nav>
</header>

<!-- Separator Line Removed -->

<style>
  header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: var(--color-bg-0);
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.1);
    height: 80px;
  }

  /* .separator-line style removed */
</style>
