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

<section class="py-32 relative overflow-hidden">
  <div class="absolute inset-0 bg-[#0a0118]">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <h2 class="text-4xl md:text-5xl font-bold text-center text-white mb-16">
      Roadmap
    </h2>

    <div class="max-w-4xl mx-auto relative">
      <!-- Connecting Line -->
      <div
        class="absolute left-6 top-6 bottom-6 w-1 bg-purple-700/50 rounded-full hidden md:block"
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
    @apply flex items-start gap-6 p-6 rounded-2xl bg-purple-900/20 backdrop-blur-xl border border-purple-700/50 hover:border-purple-500 transition-all duration-500 md:ml-16;
  }

  .phase-dot {
    @apply w-12 h-12 bg-gradient-to-br from-purple-500 to-pink-500 rounded-full flex items-center justify-center text-white text-xl font-bold flex-shrink-0 absolute left-0 top-1/2 transform -translate-y-1/2 z-10 ring-4 ring-[#0a0118];
  }

  .phase-content {
    @apply pl-4;
  }

  .phase-title {
    @apply text-xl font-semibold text-white mb-2;
  }

  .phase-description {
    @apply text-gray-300;
  }
</style>
