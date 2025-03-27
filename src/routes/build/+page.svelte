<script lang="ts">
  import { onMount } from "svelte";
  import { browser } from "$app/environment";
</script>

<svelte:head>
  <title>Build with DoxaV3 - Developer Documentation</title>
  <meta
    name="description"
    content="Start building on DoxaV3 with our comprehensive developer documentation and tools"
  />
</svelte:head>

<main class="pt-32 pb-20">
  <div class="max-w-7xl mx-auto px-4">
    <!-- Hero Section -->
    <div class="text-center mb-16">
      <h1 class="text-5xl font-bold mb-6">
        Build on <span class="text-[#8247E5]">DoxaV3</span>
      </h1>
      <p class="text-xl text-gray-600 max-w-3xl mx-auto">
        Get started with DoxaV3 on the Internet Computer blockchain
      </p>
    </div>

    <!-- Quick Start Guide -->
    <div class="bg-white rounded-2xl shadow-lg p-8 mb-12">
      <h2 class="text-2xl font-bold mb-6">Quick Start Guide</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div class="space-y-4">
          <div
            class="w-12 h-12 bg-[#8247E5]/10 rounded-xl flex items-center justify-center"
          >
            <span class="text-2xl font-bold text-[#8247E5]">1</span>
          </div>
          <h3 class="text-xl font-semibold">Install IC SDK</h3>
          <div class="bg-gray-100 rounded-lg p-4">
            <pre
              class="text-sm text-gray-800">sh -ci "$(curl -fsSL https://internetcomputer.org/install.sh)"</pre>
          </div>
        </div>

        <div class="space-y-4">
          <div
            class="w-12 h-12 bg-[#8247E5]/10 rounded-xl flex items-center justify-center"
          >
            <span class="text-2xl font-bold text-[#8247E5]">2</span>
          </div>
          <h3 class="text-xl font-semibold">Clone DoxaV3</h3>
          <div class="bg-gray-100 rounded-lg p-4">
            <pre
              class="text-sm text-gray-800">git clone https://github.com/DoxaFoundation/doxa-v3.git
cd doxa-v3</pre>
          </div>
        </div>

        <div class="space-y-4">
          <div
            class="w-12 h-12 bg-[#8247E5]/10 rounded-xl flex items-center justify-center"
          >
            <span class="text-2xl font-bold text-[#8247E5]">3</span>
          </div>
          <h3 class="text-xl font-semibold">Start Development</h3>
          <div class="bg-gray-100 rounded-lg p-4">
            <pre class="text-sm text-gray-800"># Start local IC network
dfx start --background

# Deploy locally
dfx deploy</pre>
          </div>
        </div>
      </div>
    </div>

    <!-- Prerequisites Notice -->
    <div class="bg-blue-50 rounded-xl p-6 mb-12">
      <h3 class="text-lg font-semibold text-blue-800 mb-2">Prerequisites</h3>
      <ul class="list-disc list-inside text-blue-700 space-y-2">
        <li>Node.js v16.0.0 or higher</li>
        <li>Git</li>
        <li>Internet Computer SDK (dfx)</li>
      </ul>
    </div>

    <!-- Main Content -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-16">
      <!-- Documentation -->
      <div class="bg-white rounded-2xl shadow-lg p-8">
        <h2 class="text-2xl font-bold mb-6">Documentation</h2>
        <ul class="space-y-4">
          <li>
            <a
              href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-between p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition-all group"
            >
              <div>
                <h3 class="font-semibold text-gray-900">Getting Started</h3>
                <p class="text-sm text-gray-600">
                  Learn the basics of DoxaV3 integration
                </p>
              </div>
              <svg
                class="w-6 h-6 text-gray-400 group-hover:text-[#8247E5] transition-colors"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </a>
          </li>
          <li>
            <a
              href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-between p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition-all group"
            >
              <div>
                <h3 class="font-semibold text-gray-900">API Reference</h3>
                <p class="text-sm text-gray-600">Complete API documentation</p>
              </div>
              <svg
                class="w-6 h-6 text-gray-400 group-hover:text-[#8247E5] transition-colors"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </a>
          </li>
          <li>
            <a
              href="https://sgv54-gyaaa-aaaag-qngxa-cai.icp0.io/"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-between p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition-all group"
            >
              <div>
                <h3 class="font-semibold text-gray-900">Tutorials</h3>
                <p class="text-sm text-gray-600">
                  Step-by-step integration guides
                </p>
              </div>
              <svg
                class="w-6 h-6 text-gray-400 group-hover:text-[#8247E5] transition-colors"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </a>
          </li>
        </ul>
      </div>

      <!-- Resources -->
      <div class="bg-white rounded-2xl shadow-lg p-8">
        <h2 class="text-2xl font-bold mb-6">Developer Resources</h2>
        <ul class="space-y-4">
          <li>
            <a
              href="https://github.com/DoxaFoundation/doxa-v3"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-between p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition-all group"
            >
              <div>
                <h3 class="font-semibold text-gray-900">GitHub Repository</h3>
                <p class="text-sm text-gray-600">Access our open-source code</p>
              </div>
              <svg
                class="w-6 h-6 text-gray-400 group-hover:text-[#8247E5] transition-colors"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </a>
          </li>
          <li>
            <a
              href="https://discord.gg/8qtVwtmV"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-between p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition-all group"
            >
              <div>
                <h3 class="font-semibold text-gray-900">Developer Community</h3>
                <p class="text-sm text-gray-600">
                  Join our Discord for support
                </p>
              </div>
              <svg
                class="w-6 h-6 text-gray-400 group-hover:text-[#8247E5] transition-colors"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </a>
          </li>
          <li>
            <a
              href="https://motoko-book.dev/project-deployment/installing-sdk.html"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-between p-4 bg-gray-50 rounded-xl hover:bg-gray-100 transition-all group"
            >
              <div>
                <h3 class="font-semibold text-gray-900">SDK Installation Guide</h3>
                <p class="text-sm text-gray-600">Motoko-Book</p>
              </div>
              <svg
                class="w-6 h-6 text-gray-400 group-hover:text-[#8247E5] transition-colors"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </a>
          </li>
        </ul>
      </div>
    </div>

    <!-- Support Section -->
    <div class="bg-[#8247E5] rounded-2xl p-8 text-white">
      <div class="max-w-3xl mx-auto text-center">
        <h2 class="text-2xl font-bold mb-4">Need Help?</h2>
        <p class="mb-8">
          Our developer support team is always ready to help you with your
          integration
        </p>
        <div class="flex flex-wrap justify-center gap-4">
          <a
            href="https://discord.gg/8qtVwtmV"
            target="_blank"
            rel="noopener"
            class="px-6 py-3 bg-white text-[#8247E5] rounded-xl hover:bg-gray-100 transition-all font-medium"
          >
            Join Discord
          </a>
          <a
            href="mailto:doxadaooperations@gmail.com"
            class="px-6 py-3 bg-white/10 backdrop-blur-sm rounded-xl border border-white/20 hover:bg-white/20 transition-all font-medium"
          >
            Contact Support
          </a>
        </div>
      </div>
    </div>
  </div>
</main>
