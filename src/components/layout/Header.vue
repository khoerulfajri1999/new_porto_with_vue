<template>
  <header
    ref="headerRef"
    class="container mx-auto fixed top-0 z-50 w-full transition-all duration-300 flex mt-2"
  >
    <div
      class="flex flex-col items-center justify-between w-full max-w-full"
    >
      <div
        ref="borderRef"
        class="flex transition-all duration-300 ease-in-out items-center justify-between w-full origin-left scale-y-0"
        :class="{
          'bg-neutral-800 rounded-full':
            isScrollingUp ||
            (isScrolledDown && (isHoveringLogo || hasHoveredLogo)),
          'bg-transparent':
            !isScrollingUp &&
            (!isScrolledDown || (!isHoveringLogo && !hasHoveredLogo)),
        }"
      >
        <div
          class="flex items-center space-x-4 transition-all duration-500 ease-in-out"
          :class="{
            'bg-neutral-800 rounded-full text-white shadow-lg':
              isScrolledDown || isScrollingUp,
          }"
          @mouseenter="onLogoHover(true)"
          @mouseleave="onLogoHover(false)"
        >
          <!-- Logo besar -->
          <div
            class="flex items-center space-x-4 transition-opacity duration-300 cursor-pointer"
            :class="{
              'opacity-0 hidden': isScrolledDown || isScrollingUp,
              'opacity-100 flex': !isScrolledDown && !isScrollingUp,
            }"
          >
            <img
              src="../../assets/Logo PT Dark.png"
              alt="logo-default"
              class="w-40 md:w-60 lg:w-80 transition-opacity duration-300"
            />
            <div
              class="hidden sm:flex items-center space-x-2 text-gray-300 text-sm leading-tight"
            >
              <div class="h-12 border-r-2 border-current"></div>
              <div class="pl-2">Everything<br />you can be</div>
            </div>
          </div>

          <!-- Logo kecil -->
          <img
            src="../../assets/Logo PT.png"
            alt="logo-scroll"
            class="p-3 transition-discrete ease-in-out w-20 lg:w-30 cursor-pointer"
            :class="{
              'scale-75 opacity-100': isScrolledDown || isScrollingUp,
              'scale-100 opacity-0': !isScrolledDown && !isScrollingUp,
            }"
          />
        </div>

        <!-- Navigation & Hamburger Wrapper -->
        <div
          class="relative transition-all duration-500 ease-in-out ml-4"
          :class="{
            'rounded-full shadow-lg':
              isScrollingUp || isHoveringLogo || hasHoveredLogo,
            'bg-transparent':
              !isScrollingUp && !isHoveringLogo && !hasHoveredLogo,
          }"
        >
          <div
            class="flex items-center justify-between gap-6 px-4 py-2 transition-opacity duration-500"
            :class="{
              'opacity-0': isScrolledDown && !isScrollingUp && !isHoveringLogo,
              'opacity-100':
                !isScrolledDown ||
                isScrollingUp ||
                isHoveringLogo ||
                hasHoveredLogo,
            }"
          >
            <!-- Nav links -->
            <nav class="hidden lg:flex space-x-8 text-white font-medium">
              <a href="#home" class="hover:text-gray-300 transition-colors"
                >Home</a
              >
              <a href="#services" class="hover:text-gray-300 transition-colors"
                >Services</a
              >
              <a href="#about" class="hover:text-gray-300 transition-colors"
                >About</a
              >
              <a href="#home" class="hover:text-gray-300 transition-colors"
                >Contact</a
              >
            </nav>

            <!-- Hamburger -->
            <button
              class="lg:p-2 hover:bg-white/10 rounded-full transition-colors lg:hidden"
              @click="$emit('toggle-menu')"
            >
              <Menu class="w-6 h-6 text-white" />
            </button>
          </div>
        </div>
      </div>

      <!-- Text below border -->
      <div
        class="hidden lg:flex border-t border-t-yellow-300 md:flex justify-end w-full pt-0 pb-2 text-sm transition-all duration-500 ease-in-out"
        :class="{
          'opacity-0 hidden': isScrolledDown || isScrollingUp,
          'opacity-100 flex': !isScrolledDown && !isScrollingUp,
        }"
      >
        <div
          ref="locationRef"
          class="bg-yellow-300 text-black px-4 py-1 rounded-b shadow-sm inline-flex"
        >
          Purwokerto, Central Java, Indonesia
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from "vue";
import { Menu } from "lucide-vue-next";
import { gsap } from "gsap";

const isScrolledDown = ref(false);
const isScrollingUp = ref(false);
const isHoveringLogo = ref(false);
const hasHoveredLogo = ref(false);

const headerRef = ref(null);
const borderRef = ref(null);
const locationRef = ref(null);

let lastScrollY = 0;

const handleScroll = () => {
  const currentY = window.scrollY;
  isScrollingUp.value = currentY < lastScrollY && currentY > 80;
  isScrolledDown.value = currentY > 80;

  if (isScrolledDown.value) {
    hasHoveredLogo.value = false;
  }

  lastScrollY = currentY;
};

const onLogoHover = (hovering) => {
  isHoveringLogo.value = hovering;
  if (hovering) hasHoveredLogo.value = true;
};

onMounted(async () => {
  window.addEventListener("scroll", handleScroll);
  await nextTick();

  // Animate border from top to bottom
  gsap.fromTo(
    borderRef.value,
    { scaleY: 0, transformOrigin: "top center" },
    {
      scaleY: 1,
      duration: 1,
      ease: "power2.out",
    }
  );

  // Animate location text from bottom up
  gsap.from(locationRef.value, {
    y: 30,
    opacity: 0,
    duration: 1,
    delay: 0.5,
    ease: "power2.out",
  });
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
header {
  transition: transform 0.3s ease, opacity 0.3s ease;
}
</style>
