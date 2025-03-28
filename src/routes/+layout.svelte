<script lang="ts">
  import "../app.css";
  import Nav from "../components/Nav.svelte";
</script>

<svelte:head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link
    rel="preconnect"
    href="https://fonts.gstatic.com"
    crossorigin="anonymous"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600;700&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class="app overflow-hidden">
  <Nav />
  <main>
    <slot />
  </main>
  <footer class="bg-[#110a29] py-16">
    <div class="max-w-7xl mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
        <!-- About Us -->
        <div>
          <h3 class="text-xl font-bold text-white mb-4">About Us</h3>
          <p class="text-gray-300">
            Doxa is a multi-stablecoin platform built on the Internet Computer
            (IC). Our platform enables seamless integration and amazing
            applications.
          </p>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="text-xl font-bold text-white mb-4">Quick Links</h3>
          <ul class="space-y-2">
            <li>
              <a href="/partners" class="text-gray-300 no-hover">Partners</a>
            </li>
            <li><a href="/use" class="text-gray-300 no-hover">Use</a></li>
            <li>
              <a href="/developer" class="text-gray-300 no-hover">Developer</a>
            </li>
            <li>
              <a href="/launch" class="text-gray-300 no-hover">Launch App</a>
            </li>
          </ul>
        </div>

        <!-- Contact Us -->
        <div>
          <h3 class="text-xl font-bold text-white mb-4">Contact Us</h3>
          <a
            href="mailto:doxadaooperations@gmail.com"
            class="text-gray-300 no-hover"
          >
            doxadaooperations@gmail.com
          </a>
        </div>

        <!-- Follow Us -->
        <div>
          <h3 class="text-xl font-bold text-white mb-4">Follow Us</h3>
          <div class="flex gap-4">
            <a href="#" class="text-gray-300 no-hover">Twitter</a>
            <a href="#" class="text-gray-300 no-hover">Discord</a>
            <a href="#" class="text-gray-300 no-hover">GitHub</a>
            <a href="#" class="text-gray-300 no-hover">Community</a>
          </div>
        </div>
      </div>

      <!-- Copyright & Legal -->
      <div class="pt-8 border-t border-white/10">
        <div class="text-gray-300 text-center">© 2025 DoxaV3</div>
        <div class="flex justify-center gap-8 mt-4">
          <a
            href="/terms"
            style="color: #FF4C1E !important; text-decoration: none !important;"
            >Terms of Use</a
          >
          <a
            href="/privacy"
            style="color: #FF4C1E !important; text-decoration: none !important;"
            >Privacy Policy</a
          >
        </div>
      </div>
    </div>
  </footer>
</div>

<style>
  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    position: relative;
  }

  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 100%;
    margin: 0 auto;
    box-sizing: border-box;
    position: relative;
    z-index: 1;
  }

  /* Hide any system-generated content */
  :global(body::before),
  :global(.new-file-content) {
    display: none !important;
  }

  /* Remove all hover effects and transitions */
  :global(.no-hover) {
    transition: none !important;
  }
  :global(.no-hover:hover) {
    color: inherit !important;
    background: none !important;
  }

  /* Style for Terms and Privacy links */
  :global(.footer-legal) {
    color: #ff4c1e !important;
    text-decoration: none !important;
    transition: none !important;
  }
  :global(.footer-legal:hover) {
    color: #ff4c1e !important;
    background: none !important;
    text-decoration: none !important;
  }
</style>
