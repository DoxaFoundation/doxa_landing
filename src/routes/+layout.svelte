<script lang="ts">
  import "../app.css";
</script>

<div class="app overflow-hidden">
  <main>
    <slot />
  </main>
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
</style>
