<template>
  <section
    class="container px-10 sm:px-0 relative z-10 flex-1 flex flex-col justify-center mx-auto"
    ref="mainRef"
    id="home"
  >
    <div class="max-w-2xl mt-10 md:mt-16 lg:mt-28">
      <h2
        ref="headingRef"
        class="text-4xl md:text-5xl lg:text-8xl font-bold mb-6 lg:mb-8 leading-tight opacity-0"
      >
        Lets<br />
        <span class="text-white">Connect.</span>
      </h2>

      <div
        ref="paragraphRef"
        class="space-y-3 lg:space-y-4 mb-8 lg:mb-12 text-gray-300 text-base lg:text-lg xl:text-2xl leading-relaxed opacity-0"
      >
        <p>One message could be the start of something great.</p>
        <p>
          We are the experience of true self-expression<br />
          that goes beyond traditional limitations.
        </p>
      </div>

      <div ref="buttonGroupRef" class="flex items-center space-x-6 opacity-0">
        <div class="relative inline-flex group">
          <div
            class="absolute transitiona-all duration-1000 opacity-70 -inset-px bg-gradient-to-r from-blue-300 via-purple-300 to-yellow-200 rounded-xl blur-lg group-hover:opacity-100 group-hover:-inset-1 group-hover:duration-200 animate-tilt"
          ></div>
          <a
            href="#"
            title="Get quote now"
            class="relative inline-flex items-center justify-center px-8 py-4 text-lg font-bold text-white transition-all duration-200 bg-neutral-800 font-pj rounded-xl focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-900"
            role="button"
            >Contact Us
          </a>
        </div>
        <div class="h-12 border-r-2 border-white"></div>
        <div class="text-gray-300">
          <p class="text-sm">Everything<br />you can be</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "HeroConnectSection",
  mounted() {
    const animate = () => {
      gsap.fromTo(
        this.$refs.headingRef,
        { opacity: 0, y: 40 },
        { opacity: 1, y: 0, duration: 1, ease: "power2.out" }
      );

      gsap.fromTo(
        this.$refs.paragraphRef,
        { opacity: 0, y: 40 },
        { opacity: 1, y: 0, duration: 1, ease: "power2.out", delay: 0.3 }
      );

      gsap.fromTo(
        this.$refs.buttonGroupRef,
        { opacity: 0, x: -50 },
        { opacity: 1, x: 0, duration: 1, ease: "power2.out", delay: 0.5 }
      );
    };

    ScrollTrigger.create({
      trigger: this.$refs.mainRef,
      start: "top 80%",
      onEnter: animate,
      onEnterBack: animate,
      // Optional:
      // markers: true,
    });
  },
};
</script>
