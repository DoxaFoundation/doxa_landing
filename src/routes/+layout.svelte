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
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<div class="app overflow-hidden">
  <Nav />
  <main class="pt-20 bg-gray-50">
    <slot />
  </main>
  <footer class="bg-gray-100 py-16">
    <div class="max-w-7xl mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
        <!-- About Us -->
        <div>
          <h3 class="text-xl font-bold text-gray-900 mb-4">About Us</h3>
          <p class="text-gray-700">
            Doxa is a multi-stablecoin platform built on the Internet Computer
            (IC). Our platform enables seamless integration and amazing
            applications.
          </p>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="text-xl font-bold text-gray-900 mb-4">Quick Links</h3>
          <ul class="space-y-2">
            <li>
              <a href="/partners" class="text-gray-700 hover:text-gray-900"
                >Partners</a
              >
            </li>
            <li>
              <a href="/use" class="text-gray-700 hover:text-gray-900">Use</a>
            </li>
            <li>
              <a href="/developer" class="text-gray-700 hover:text-gray-900"
                >Developer</a
              >
            </li>
            <li>
              <a
                href="https://app.doxadao.org"
                target="_blank"
                rel="noopener"
                class="text-gray-700 hover:text-gray-900">Launch App</a
              >
            </li>
          </ul>
        </div>

        <!-- Contact Us -->
        <div>
          <h3 class="text-xl font-bold text-gray-900 mb-4">Contact Us</h3>
          <a
            href="mailto:doxadaooperations@gmail.com"
            class="text-gray-700 hover:text-gray-900"
          >
            doxadaooperations@gmail.com
          </a>
        </div>

        <!-- Follow Us -->
        <div>
          <h3 class="text-xl font-bold text-gray-900 mb-4">Follow Us</h3>
          <div class="flex gap-4">
            <a
              href="https://x.com/DoxaUSD"
              target="_blank"
              rel="noopener"
              class="text-gray-700 hover:text-gray-900">X</a
            >
            <a
              href="https://discord.gg/h7Exzz96Xd"
              target="_blank"
              rel="noopener"
              class="text-gray-700 hover:text-gray-900">Discord</a
            >
            <a
              href="https://github.com/DoxaFoundation"
              target="_blank"
              rel="noopener"
              class="text-gray-700 hover:text-gray-900">GitHub</a
            >
            <a
              href="https://oc.app/community/4opco-piaaa-aaaaf-bmytq-cai/?ref=65m7d-siaaa-aaaaf-azprq-cai"
              target="_blank"
              rel="noopener"
              class="text-gray-700 hover:text-gray-900">OpenChat</a
            >

            <a
              href="https://www.linkedin.com/company/doxausd"
              target="_blank"
              rel="noopener"
              class="text-gray-700 hover:text-gray-900">LinkedIn</a
            >
          </div>
        </div>
      </div>

      <!-- Copyright & Legal -->
      <div class="pt-8 border-t-2 border-gray-300">
        <div class="text-gray-700 text-center">© 2025 Doxa</div>
        <div class="flex justify-center gap-8 mt-4">
          <a href="/terms" class="text-gray-600 hover:text-gray-800"
            >Terms of Use</a
          >
          <a href="/privacy" class="text-gray-600 hover:text-gray-800"
            >Privacy Policy</a
          >
        </div>
      </div>
    </div>
  </footer>
</div>

<style>
  :global(html),
  :global(body) {
    background-color: var(--color-bg-0);
    overflow-x: hidden;
    font-family: "Inter", sans-serif;
  }

  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    position: relative;
    background-color: var(--color-bg-0);
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
</style>
