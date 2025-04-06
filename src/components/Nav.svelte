<script lang="ts">
</script>

<!-- Navigation -->
<header
  class="fixed top-0 left-0 right-0 z-50 bg-[#110a29]/95 backdrop-blur-lg border-b border-white/5 shadow-lg transition-all duration-300"
>
  <nav class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
    <a href="/" class="text-2xl font-bold text-white font-['Space_Grotesk']"
      >DoxaV3</a
    >
    <div class="flex items-center gap-8">
      <a
        href="/partners"
        class="text-gray-300 hover:text-white font-['Inter'] font-medium transition-colors"
        >Partners</a
      >
      <a
        href="https://doxa-1.gitbook.io/doxa-guide"
        target="_blank"
        rel="noopener"
        class="text-gray-300 hover:text-white font-['Inter'] font-medium transition-colors"
        >Use</a
      >
      <a
        href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="text-gray-300 hover:text-white font-['Inter'] font-medium transition-colors"
        >Developer</a
      >
      <a
        href="https://i7m4z-gqaaa-aaaak-qddtq-cai.icp0.io/"
        target="_blank"
        rel="noopener"
        class="inline-flex items-center justify-center px-6 py-2 bg-gradient-to-r from-purple-600 to-pink-600 hover:from-pink-600 hover:to-purple-600 text-white rounded-full font-medium transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-pink-500/30"
        >Launch App</a
      >
    </div>
  </nav>
</header>

<style>
  header {
    background-color: rgba(17, 10, 41, 0.95);
    -webkit-backdrop-filter: blur(8px);
    backdrop-filter: blur(8px);
  }

  header::before {
    content: "";
    position: absolute;
    inset: 0;
    background: #110a29;
    z-index: -1;
  }
</style>
