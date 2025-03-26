<script lang="ts">
  import { page } from "$app/stores";
</script>

<div
  class="min-h-screen flex items-center justify-center bg-gradient-to-br from-[#1E0447] to-[#3B0764] text-white px-4"
>
  <div class="text-center">
    <h1 class="text-9xl font-bold mb-4">{$page.status}</h1>
    <p class="text-2xl mb-8">{$page.error?.message || "Page not found"}</p>
    <a
      href="/"
      class="inline-block px-8 py-3 bg-purple-600 hover:bg-purple-700 rounded-lg text-lg transition-colors"
    >
      Go Home
    </a>
  </div>
</div>
