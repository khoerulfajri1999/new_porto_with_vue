<template>
  <footer
    ref="footerRef"
    class="mx-14 relative z-10 flex items-end justify-between px-6 lg:px-8 flex-shrink-0 opacity-0 translate-y-10"
  >
    <div class="text-md pb-10 text-gray-400">
      <p>Powered by</p>
      <p class="font-semibold text-white">
        stevara <span class="font-normal">.id</span>
      </p>
    </div>

    <div
      class="flex flex-col space-y-5 px-3 bg-white/40 backdrop-blur-sm rounded-t-full py-3"
    >
      <button
        class="hover:bg-white/20 rounded-full transition-colors text-white"
        @click="$emit('open-social', 'facebook')"
      >
        <Facebook class="w-5 h-5 md:w-6 md:h-6 lg:w-7 lg:h-7" />
      </button>
      <button
        class="hover:bg-white/20 rounded-full transition-colors text-white"
        @click="$emit('open-social', 'instagram')"
      >
        <Instagram class="w-5 h-5 md:w-6 md:h-6 lg:w-7 lg:h-7" />
      </button>
      <button
        class="hover:bg-white/20 rounded-full transition-colors text-white"
        @click="$emit('open-social', 'twitter')"
      >
        <Twitter class="w-5 h-5 md:w-6 md:h-6 lg:w-7 lg:h-7" />
      </button>
    </div>
  </footer>
</template>

<script>
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { Facebook, Instagram, Twitter } from 'lucide-vue-next';

gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'AnimatedFooter',
  components: {
    Facebook,
    Instagram,
    Twitter,
  },
  mounted() {
    const footer = this.$refs.footerRef;

    gsap.fromTo(
      footer,
      { opacity: 1, y: 40 },
      {
        opacity: 1,
        y: 0,
        duration: 1,
        ease: 'power2.out',
        scrollTrigger: {
          trigger: footer,
          start: 'top 90%',
          toggleActions: 'play none none none',
        },
      }
    );
  },
};
</script>
