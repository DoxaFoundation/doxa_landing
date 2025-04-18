<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  // Simple roadmap data
  const roadmapItems = [
    {
      phase: "Phase 1",
      title: "Foundation & MVP",
      timeline: "Ongoing 2025",
      description:
        "Core protocol architecture and initial stablecoin mechanisms",
    },
    {
      phase: "Phase 2",
      title: "Expansion & Integration",
      timeline: "Next 6 months",
      description: "Strategic partnerships and enhanced protocol features",
    },
    {
      phase: "Phase 3",
      title: "Growth & Ecosystem",
      timeline: "Following 6 months",
      description:
        "Scaling the protocol and building a thriving application ecosystem",
    },
    {
      phase: "Phase 4",
      title: "Maturity & Scaling",
      timeline: "Within 12 months",
      description: "Full decentralization and global stablecoin adoption",
    },
  ];

  let roadmapElement: HTMLElement;

  onMount(() => {
    if (gsap && ScrollTrigger) {
      initAnimations();
    }
  });

  function initAnimations(): void {
    if (!gsap || !ScrollTrigger) return;

    // Simple fade-in animation for the title
    gsap.from(".roadmap-title", {
      y: 30,
      opacity: 0,
      duration: 0.8,
      scrollTrigger: {
        trigger: roadmapElement,
        start: "top 80%",
      },
    });

    // Simple staggered animation for roadmap items
    gsap.from(".roadmap-item", {
      y: 30,
      opacity: 0,
      stagger: 0.2,
      duration: 0.6,
      scrollTrigger: {
        trigger: ".roadmap-items",
        start: "top 80%",
      },
    });
  }
</script>

<section class="py-24 relative overflow-hidden" bind:this={roadmapElement}>
  <!-- Simple gradient background -->
  <div
    class="absolute inset-0 bg-gradient-to-br from-slate-100 to-slate-200"
  ></div>

  <!-- Simple grid pattern -->
  <div class="absolute inset-0 bg-grid opacity-10"></div>

  <div class="relative container mx-auto px-6 z-10">
    <h2
      class="roadmap-title text-4xl md:text-5xl font-bold text-center mb-16 gradient-text"
    >
      Roadmap
    </h2>

    <!-- Simple timeline layout -->
    <div class="roadmap-items max-w-4xl mx-auto">
      <!-- Vertical connecting line -->
      <div
        class="hidden md:block absolute left-[7.5rem] top-8 bottom-8 w-px bg-slate-300"
      ></div>

      {#each roadmapItems as item, i}
        <div class="roadmap-item flex mb-12 relative">
          <!-- Phase indicator -->
          <div
            class="phase-dot w-10 h-10 rounded-full bg-gradient-to-br from-slate-400 to-slate-600 flex-shrink-0 flex items-center justify-center text-white font-bold hidden md:flex z-10"
          >
            {i + 1}
          </div>

          <!-- Content card -->
          <div
            class="roadmap-card flex-1 p-6 md:ml-8 rounded-xl bg-white/50 backdrop-blur-sm border border-white/60 shadow-md hover:shadow-lg transition-all"
          >
            <div class="flex flex-wrap items-center gap-3 mb-3">
              <div
                class="phase-badge px-3 py-1 text-sm rounded-full bg-slate-200/80 text-slate-700 md:hidden"
              >
                {i + 1}
              </div>
              <h3 class="text-xl font-semibold text-slate-800">{item.title}</h3>
              <div class="ml-auto text-sm text-slate-600 whitespace-nowrap">
                {item.timeline}
              </div>
            </div>
            <p class="text-slate-700">{item.description}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .gradient-text {
    background: linear-gradient(90deg, #5a5a5a, #444444);
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }

  .bg-grid {
    background-size: 40px 40px;
    background-image: linear-gradient(
        to right,
        rgba(0, 0, 0, 0.05) 1px,
        transparent 1px
      ),
      linear-gradient(to bottom, rgba(0, 0, 0, 0.05) 1px, transparent 1px);
  }

  .roadmap-card {
    transition: all 0.3s ease;
  }

  .roadmap-card:hover {
    transform: translateY(-5px);
    background-color: rgba(255, 255, 255, 0.6);
  }

  @media (max-width: 768px) {
    .roadmap-item {
      padding-left: 0;
    }
  }
</style>
