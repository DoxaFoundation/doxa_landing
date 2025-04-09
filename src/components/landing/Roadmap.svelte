<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    const roadmapItems = document.querySelectorAll(".roadmap-item");
    roadmapItems.forEach((item, index) => {
      gsap.from(item, {
        scrollTrigger: {
          trigger: item,
          start: "top 80%",
          toggleActions: "play none none reverse",
        },
        duration: 1,
        y: 50,
        opacity: 0,
        delay: index * 0.2,
        ease: "power3.out",
      });
    });
  }
</script>

<section class="py-32 relative overflow-hidden bg-primary-900">
  <div class="absolute inset-0">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
    <!-- Decorative elements -->
    <div class="absolute -left-20 -top-20 w-64 h-64 bg-primary-500/10 rounded-full filter blur-3xl animate-pulse"></div>
    <div class="absolute right-0 bottom-0 w-40 h-40 bg-primary-300/10 rounded-full filter blur-3xl animate-pulse" style="animation-delay: 1s;"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <h2
      class="text-4xl md:text-5xl font-bold text-center text-primary-100 mb-16"
    >
      Roadmap
    </h2>

    <div class="max-w-4xl mx-auto relative">
      <!-- Connecting Line -->
      <div
        class="absolute left-6 top-6 bottom-6 w-1 bg-gradient-to-b from-primary-400 via-primary-500 to-primary-600 rounded-full hidden md:block"
      ></div>

      <div class="roadmap-item mb-16 relative">
        <div class="roadmap-phase">
          <div class="phase-dot">1</div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 1: Foundation & MVP</h3>
            <p class="phase-description">Completed/Ongoing 2025</p>
          </div>
        </div>
      </div>

      <div class="roadmap-item mb-16 relative">
        <div class="roadmap-phase">
          <div class="phase-dot">2</div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 2: Expansion & Integration</h3>
            <p class="phase-description">Next 6 months</p>
          </div>
        </div>
      </div>

      <div class="roadmap-item mb-16 relative">
        <div class="roadmap-phase">
          <div class="phase-dot">3</div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 3: Growth & Ecosystem Development</h3>
            <p class="phase-description">Following 6 months</p>
          </div>
        </div>
      </div>

      <div class="roadmap-item relative">
        <div class="roadmap-phase">
          <div class="phase-dot">4</div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 4: Maturity & Scaling</h3>
            <p class="phase-description">
              Long-term, within the next 12 months
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .roadmap-phase {
    @apply flex items-start gap-6 p-6 rounded-2xl bg-primary-800/30 backdrop-blur-xl border border-primary-600/50 hover:border-primary-400 transition-all duration-500 md:ml-16;
  }

  .phase-dot {
    @apply w-12 h-12 bg-primary-500 rounded-full flex items-center justify-center text-primary-100 text-xl font-bold flex-shrink-0 absolute left-0 top-1/2 transform -translate-y-1/2 z-10 ring-4 ring-primary-900;
  }

  .phase-content {
    @apply pl-4;
  }

  .phase-title {
    @apply text-xl font-semibold text-primary-100 mb-2;
  }

  .phase-description {
    @apply text-primary-300;
  }
</style>
