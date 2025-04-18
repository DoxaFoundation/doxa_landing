<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    if (gsap && ScrollTrigger) {
      initAnimations();
    }
  });

  function initAnimations() {
    if (!gsap || !ScrollTrigger) return;

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

<section class="py-32 relative overflow-hidden">
  <div class="absolute inset-0 bg-gray-100">
    <div class="absolute inset-0 bg-grid opacity-20"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <h2 class="text-4xl md:text-5xl font-bold text-center text-gray-900 mb-16">
      Roadmap
    </h2>

    <div class="max-w-4xl mx-auto relative">
      <!-- Connecting Line -->
      <div
        class="absolute left-6 top-6 bottom-6 w-1 bg-gray-300/50 rounded-full hidden md:block"
      ></div>

      <div class="roadmap-item mb-12 relative">
        <div class="roadmap-phase">
          <div class="phase-dot"></div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 1: Foundation & MVP</h3>
            <p class="phase-description">Completed/Ongoing 2025</p>
          </div>
        </div>
      </div>

      <div class="roadmap-item mb-12 relative">
        <div class="roadmap-phase">
          <div class="phase-dot"></div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 2: Expansion & Integration</h3>
            <p class="phase-description">Next 6 months</p>
          </div>
        </div>
      </div>

      <div class="roadmap-item mb-12 relative">
        <div class="roadmap-phase">
          <div class="phase-dot"></div>
          <div class="phase-content">
            <h3 class="phase-title">Phase 3: Growth & Ecosystem Development</h3>
            <p class="phase-description">Following 6 months</p>
          </div>
        </div>
      </div>

      <div class="roadmap-item relative">
        <div class="roadmap-phase">
          <div class="phase-dot"></div>
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
    @apply flex items-start gap-6 p-6 rounded-2xl bg-white/50 backdrop-blur-xl border-2 border-gray-300 hover:border-gray-200 transition-all duration-500 md:ml-16;
  }

  .phase-dot {
    @apply w-12 h-12 bg-gradient-to-br from-gray-200 to-gray-300 rounded-full flex items-center justify-center text-gray-800 text-xl font-bold flex-shrink-0 absolute left-0 top-1/2 transform -translate-y-1/2 z-10 ring-4 ring-gray-100;
  }

  .phase-content {
    @apply pl-4;
  }

  .phase-title {
    @apply text-xl font-semibold text-gray-900 mb-2;
  }

  .phase-description {
    @apply text-gray-700;
  }
</style>
