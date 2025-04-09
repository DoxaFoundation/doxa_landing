<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    const testimonials = document.querySelectorAll(".testimonial-card");
    testimonials.forEach((card, index) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
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
  <div class="absolute inset-0 bg-primary-900">
    <div class="absolute inset-0 bg-grid opacity-10"></div>
  </div>

  <div class="relative container mx-auto px-6">
    <h2
      class="text-4xl md:text-5xl font-bold text-center text-primary-100 mb-16"
    >
      What Our Users Say
    </h2>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
      <div class="testimonial-card relative">
        <div class="quote-icon">“</div>
        <div class="testimonial-content">
          <p class="testimonial-text">
            "Doxa has revolutionized how I handle cross-border payments. The
            speed and low fees are unmatched."
          </p>
          <div class="testimonial-author">
            <div class="author-avatar">👤</div>
            <div class="author-info">
              <h4 class="author-name">Sarah Chen</h4>
              <p class="author-role">E-commerce Entrepreneur</p>
            </div>
          </div>
        </div>
      </div>

      <div class="testimonial-card relative">
        <div class="quote-icon">“</div>
        <div class="testimonial-content">
          <p class="testimonial-text">
            "As a developer, I love how easy it is to integrate Doxa into my
            dApps. The documentation is excellent."
          </p>
          <div class="testimonial-author">
            <div class="author-avatar">👨‍💻</div>
            <div class="author-info">
              <h4 class="author-name">Alex Rodriguez</h4>
              <p class="author-role">Web3 Developer</p>
            </div>
          </div>
        </div>
      </div>

      <div class="testimonial-card relative">
        <div class="quote-icon">“</div>
        <div class="testimonial-content">
          <p class="testimonial-text">
            "The transparency and security of Doxa give me peace of mind. I can
            see exactly what backs my money."
          </p>
          <div class="testimonial-author">
            <div class="author-avatar">👩‍💼</div>
            <div class="author-info">
              <h4 class="author-name">Maria Garcia</h4>
              <p class="author-role">Financial Analyst</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .testimonial-card {
    @apply p-8 pt-12 rounded-2xl bg-primary-800/30 backdrop-blur-xl border border-primary-600/50 hover:border-primary-400 transition-all duration-500;
  }

  .quote-icon {
    @apply absolute top-4 left-4 text-6xl text-primary-500/30 font-serif;
  }

  .testimonial-text {
    @apply text-primary-200 mb-6;
  }

  .testimonial-author {
    @apply flex items-center gap-4;
  }

  .author-avatar {
    @apply w-12 h-12 bg-primary-500 rounded-full flex items-center justify-center text-primary-100 text-xl;
  }

  .author-name {
    @apply text-primary-100 font-semibold;
  }

  .author-role {
    @apply text-primary-400 text-sm;
  }
</style>
