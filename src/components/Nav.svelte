<script lang="ts">
  import { onMount } from "svelte";
  let isMenuOpen = false;
  let scrolled = false;
  let navElement: HTMLElement;

  onMount(() => {
    const handleScroll = () => {
      scrolled = window.scrollY > 20;
    };

    window.addEventListener("scroll", handleScroll);

    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  });
</script>

<!-- Navigation -->
<header
  bind:this={navElement}
  class="fixed top-0 left-0 right-0 z-[9999] transition-all duration-300"
  class:scrolled
>
  <nav
    class="max-w-7xl mx-auto px-6 md:px-8 h-20 flex justify-between items-center"
  >
    <a
      href="/"
      class="logo-link flex items-center text-2xl font-bold text-gray-900 transition-all duration-300"
    >
      <div class="logo-container">
        <img src="/images/DOXA.svg" alt="Doxa Logo" class="h-8 mr-2" />
      </div>
      <span class="gradient-text font-['Inter']">Doxa</span>
    </a>

    <!-- Mobile Menu Button -->
    <button
      class="md:hidden relative z-10 w-10 h-10 flex items-center justify-center text-gray-900 rounded-full transition-colors duration-300"
      on:click={() => (isMenuOpen = !isMenuOpen)}
      aria-label="Toggle menu"
    >
      <svg
        class="w-6 h-6 transition-transform duration-300"
        class:rotate-90={isMenuOpen}
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
        class="text-gray-700 font-['Inter'] font-medium px-2 py-1"
      >
        Partners
      </a>
      <a
        href="https://doxa-1.gitbook.io/doxa-guide"
        target="_blank"
        rel="noopener"
        class="text-gray-700 font-['Inter'] font-medium px-2 py-1"
      >
        Use
      </a>
      <a
        href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="text-gray-700 font-['Inter'] font-medium px-2 py-1"
      >
        Developer
      </a>
      <a
        href="https://app.doxadao.org"
        target="_blank"
        rel="noopener"
        class="launch-btn inline-flex items-center justify-center px-7 py-2.5 rounded-full font-medium transition-all duration-300"
      >
        <span>Launch App</span>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-4 w-4 ml-2"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M14 5l7 7m0 0l-7 7m7-7H3"
          />
        </svg>
      </a>
    </div>

    <!-- Mobile Navigation -->
    <div
      class="mobile-menu fixed top-20 left-0 right-0 transition-all duration-300 transform backdrop-blur-lg"
      class:translate-x-0={isMenuOpen}
      class:translate-x-full={!isMenuOpen}
    >
      <div class="flex flex-col items-center gap-6 py-6">
        <a href="/partners" class="text-gray-800 font-['Inter'] font-medium">
          Partners
        </a>
        <a
          href="https://doxa-1.gitbook.io/doxa-guide"
          target="_blank"
          rel="noopener"
          class="text-gray-800 font-['Inter'] font-medium"
        >
          Use
        </a>
        <a
          href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
          target="_blank"
          rel="noopener"
          class="text-gray-800 font-['Inter'] font-medium"
        >
          Developer
        </a>
        <a
          href="https://app.doxadao.org"
          target="_blank"
          rel="noopener"
          class="mobile-launch-btn inline-flex items-center justify-center px-7 py-2.5 rounded-full font-medium transition-all duration-300 w-4/5 max-w-xs mt-2"
        >
          <span>Launch App</span>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-4 w-4 ml-2"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M14 5l7 7m0 0l-7 7m7-7H3"
            />
          </svg>
        </a>
      </div>
    </div>
  </nav>
</header>

<style>
  header {
    background-color: transparent;
    box-shadow: none;
    transition: all 0.3s ease;
  }

  header.scrolled {
    background-color: rgba(245, 245, 245, 0.8);
    backdrop-filter: blur(8px);
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  }

  .gradient-text {
    background: linear-gradient(135deg, #5a5a5a, #444444);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }

  /* Add specific rule to disable hover effects on logo */
  .logo-link {
    text-decoration: none;
  }

  .logo-link::after {
    display: none;
  }

  .logo-link:hover::after {
    transform: none;
  }

  .launch-btn {
    background: linear-gradient(135deg, #5a5a5a, #444444);
    color: white;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  .mobile-menu {
    background-color: rgba(245, 245, 245, 0.95);
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    height: auto;
    overflow: hidden;
    z-index: 8888;
  }

  .mobile-launch-btn {
    background: linear-gradient(135deg, #5a5a5a, #444444);
    color: white;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }
</style>
