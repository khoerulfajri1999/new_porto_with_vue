<template>
  <footer
    ref="footerRef"
    class="relative z-10 bg-neutral-800 text-white pt-12 pb-6 opacity-0 translate-y-10"
  >
    <div
      class="max-w-full mx-14 px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-5 gap-8"
    >
      <div class="col-span-1 md:col-span-2">
        <h2 class="text-2xl font-bold mb-4">stevara.id</h2>
        <p class="text-gray-400 text-sm">
          A trusted digital solution for your events and business.
        </p>
      </div>
      <div>
        <h3 class="text-xl font-semibold mb-4">Navigation</h3>
        <ul class="space-y-2">
          <li><a href="#home" class="hover:text-gray-300">Home</a></li>
          <li><a href="#services" class="hover:text-gray-300">Services</a></li>
          <li><a href="#about" class="hover:text-gray-300">About</a></li>
          <li><a href="#home" class="hover:text-gray-300">Contact</a></li>
        </ul>
      </div>
      <div>
        <h3 class="text-xl font-semibold mb-4">Contact</h3>
        <ul class="space-y-2 text-gray-400 text-sm">
          <li>
            <i class="fas fa-map-marker-alt mr-2"></i>Purwokerto, Central Java,
            Indonesia
          </li>
          <li><i class="fas fa-phone mr-2"></i>+62 812-3456-7890</li>
          <li><i class="fas fa-envelope mr-2"></i>info@stevara.id</li>
        </ul>
      </div>
      <div class="flex flex-col">
        <h3 class="text-xl font-semibold">Follow Us</h3>
        <div class="flex flex-col space-y-4 px-3 py-4 w-fit">
          <button
            class="hover:bg-white/20 rounded-full p-2 transition-colors text-white"
            @click="$emit('open-social', 'facebook')"
          >
            <Facebook class="w-6 h-6" />
          </button>
          <button
            class="hover:bg-white/20 rounded-full p-2 transition-colors text-white"
            @click="$emit('open-social', 'instagram')"
          >
            <Instagram class="w-6 h-6" />
          </button>
          <button
            class="hover:bg-white/20 rounded-full p-2 transition-colors text-white"
            @click="$emit('open-social', 'twitter')"
          >
            <Twitter class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>
    <div class="mt-12 text-center text-sm text-gray-500">
      <p>Powered by</p>
      <p class="font-semibold text-white">
        stevara <span class="font-normal">.id</span>
      </p>
    </div>
  </footer>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { Facebook, Instagram, Twitter } from "lucide-vue-next";

gsap.registerPlugin(ScrollTrigger);

const footerRef = ref(null);

onMounted(() => {
  const footer = footerRef.value;
  gsap.fromTo(
    footer,
    { opacity: 0, y: 40 },
    {
      opacity: 1,
      y: 0,
      duration: 1,
      ease: "power2.out",
      scrollTrigger: {
        trigger: footer,
        start: "top 90%",
        toggleActions: "play none none none",
      },
    }
  );
});
</script>

<style scoped>
button svg {
  transition: transform 0.2s ease;
}
button:hover svg {
  transform: scale(1.1);
}
</style>
