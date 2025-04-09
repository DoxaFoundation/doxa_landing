<script lang="ts">
  import { onMount } from "svelte";

  export let gsap: any;
  export let ScrollTrigger: any;

  let email = "";
  let submitting = false;
  let submitStatus: { success?: boolean; message?: string } | null = null;
  let emailError: string | null = null;

  function validateEmail(email: string): boolean {
    const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    return emailRegex.test(email);
  }

  function handleEmailChange() {
    emailError = null;
    if (email && !validateEmail(email)) {
      emailError = "Please enter a valid email address";
    }
  }

  async function handleEmailSubmit(e: Event) {
    e.preventDefault();

    if (!email) {
      emailError = "Email is required";
      return;
    }

    if (!validateEmail(email)) {
      emailError = "Please enter a valid email address";
      return;
    }

    submitting = true;
    submitStatus = null;

    try {
      // For now, just show a success message
      // TODO: Implement actual email collection in IC canister
      submitStatus = {
        success: true,
        message: "Thanks for signing up! We'll keep you updated.",
      };
      email = "";
      emailError = null;
    } catch (error) {
      submitStatus = {
        success: false,
        message: "Something went wrong. Please try again later.",
      };
    } finally {
      submitting = false;
    }
  }

  onMount(() => {
    initAnimations();
  });

  function initAnimations() {
    // Newsletter Section Animation with Background
    const newsletterSection = document.querySelector(".newsletter-content");
    if (newsletterSection) {
      gsap.from(newsletterSection, {
        scrollTrigger: {
          trigger: newsletterSection,
          start: "top 75%",
          toggleActions: "play none none reverse",
        },
        duration: 1.2,
        y: 100,
        opacity: 0,
        ease: "power3.out",
      });
    }

    // Form elements animation
    gsap.from(".newsletter-form", {
      scrollTrigger: {
        trigger: ".newsletter-form",
        start: "top 80%",
      },
      duration: 1,
      y: 30,
      opacity: 0,
      delay: 0.3,
      ease: "power3.out",
    });

    // Background gradient animation
    gsap.to(".newsletter-bg", {
      duration: 3,
      backgroundPosition: "200% 50%",
      repeat: -1,
      ease: "none",
    });
  }
</script>

<section class="py-32 relative overflow-hidden">
  <div class="newsletter-bg absolute inset-0 bg-primary-800 opacity-90"></div>

  <div class="relative container mx-auto px-6 max-w-4xl">
    <div class="newsletter-content text-center">
      <h2 class="text-3xl font-bold mb-4 text-primary-100">
        Be Early. Be First.
      </h2>
      <p class="text-xl mb-8 text-primary-300">
        Don't just watch the future happen — help build it.
      </p>
      <p class="text-lg mb-8 text-primary-400">
        Join thousands already signed up for early access, launch updates,
        staking rewards, and more.
      </p>

      <form
        class="newsletter-form max-w-md mx-auto"
        on:submit={handleEmailSubmit}
      >
        <div class="flex flex-col gap-4">
          <div class="relative">
            <input
              type="email"
              placeholder="Enter your email"
              bind:value={email}
              on:input={handleEmailChange}
              class="w-full px-6 py-4 rounded-full bg-primary-700/50 backdrop-blur-xl border border-primary-600/50 text-primary-100 placeholder-primary-400 focus:outline-none focus:border-primary-400 transition-colors {emailError
                ? 'border-red-500'
                : ''}"
            />
            <button
              type="submit"
              disabled={submitting || !!emailError}
              class="absolute right-2 top-2 px-6 py-2 bg-primary-500 hover:bg-primary-400 text-primary-100 rounded-full transition-all duration-300 transform hover:scale-105 disabled:opacity-50 disabled:cursor-not-allowed"
            >
              {submitting ? "Subscribing..." : "Join the Early List"}
            </button>
          </div>

          {#if emailError}
            <div class="text-red-400 text-sm">{emailError}</div>
          {/if}

          {#if submitStatus}
            <div
              class="text-primary-100 bg-primary-700/50 backdrop-blur-xl border border-primary-600/50 px-6 py-3 rounded-full"
            >
              {submitStatus.message}
            </div>
          {/if}
        </div>
      </form>
    </div>
  </div>
</section>

<style>
  .newsletter-bg {
    /* Removed animation properties */
    /* background-size: 200% 200%; */
    /* animation: gradientMove 15s linear infinite; */
  }

  /* Removed gradientMove keyframes */
  /* @keyframes gradientMove { ... } */

  input::placeholder {
    /* Use primary color */
    color: theme("colors.primary.400 / 70%");
  }

  input:focus {
    /* Use primary color for shadow */
    box-shadow: 0 0 0 2px theme("colors.primary.400 / 40%");
  }

  .newsletter-form {
    transform: translateY(0);
    transition: transform 0.3s ease;
  }

  .newsletter-form:hover {
    transform: translateY(-5px);
  }
</style>
