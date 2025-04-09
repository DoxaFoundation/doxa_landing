<script lang="ts">
  let isMenuOpen = false;
</script>

<!-- Navigation -->
<header class="fixed top-0 left-0 right-0 z-[9999] bg-primary-800 shadow-md">
  <nav class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
    <a
      href="/"
      class="text-2xl font-bold text-primary-100 font-['Space_Grotesk']">Doxa</a
    >

    <!-- Mobile Menu Button -->
    <button
      class="md:hidden text-primary-100"
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
        class="text-primary-300 hover:text-primary-100 font-['Inter'] font-medium transition-colors"
        >Partners</a
      >
      <a
        href="https://doxa-1.gitbook.io/doxa-guide"
        target="_blank"
        rel="noopener"
        class="text-primary-300 hover:text-primary-100 font-['Inter'] font-medium transition-colors"
        >Use</a
      >
      <a
        href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="text-primary-300 hover:text-primary-100 font-['Inter'] font-medium transition-colors"
        >Developer</a
      >
      <a
        href="https://i7m4z-gqaaa-aaaak-qddtq-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="inline-flex items-center justify-center px-6 py-2 bg-primary-500 hover:bg-primary-400 text-primary-100 rounded-full font-medium transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-primary-400/30"
        >Launch App</a
      >
    </div>

    <!-- Mobile Navigation -->
    {#if isMenuOpen}
      <div class="absolute top-full left-0 right-0 bg-primary-800 md:hidden">
        <div class="flex flex-col items-center gap-4 py-4">
          <a
            href="/partners"
            class="text-primary-300 hover:text-primary-100 font-['Inter'] font-medium transition-colors"
            >Partners</a
          >
          <a
            href="https://doxa-1.gitbook.io/doxa-guide"
            target="_blank"
            rel="noopener"
            class="text-primary-300 hover:text-primary-100 font-['Inter'] font-medium transition-colors"
            >Use</a
          >
          <a
            href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
            target="_blank"
            rel="noopener"
            class="text-primary-300 hover:text-primary-100 font-['Inter'] font-medium transition-colors"
            >Developer</a
          >
          <a
            href="https://i7m4z-gqaaa-aaaak-qddtq-cai.icp0.io/"
            target="_blank"
            rel="noopener"
            class="inline-flex items-center justify-center px-6 py-2 bg-primary-500 hover:bg-primary-400 text-primary-100 rounded-full font-medium transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-primary-400/30"
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
    /* Removed hardcoded styles, using Tailwind classes now */
    /* box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.5); */ /* Replaced with Tailwind shadow-md */
  }

  /* .separator-line style removed */
</style>
