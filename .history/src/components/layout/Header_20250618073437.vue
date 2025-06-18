<template>
  <div class="container mx-auto">
    <div
      ref="headerRef"
      class="container px-10 sm:px-0 fixed top-0 z-50 w-full transition-all duration-300 flex mt-2"
    >
      <div class="flex flex-col items-center justify-between w-full max-w-full">
        <div
          ref="borderRef"
          class="flex transition-all duration-300 ease-in-out items-center justify-between w-full origin-left scale-y-0 relative"
          :class="{
            'bg-slate-900/80 backdrop-blur-md border border-cyan-500/30 rounded-full shadow-2xl shadow-cyan-500/20':
              isScrollingUp ||
              (isScrolledDown && (isHoveringLogo || hasHoveredLogo)),
            'bg-transparent':
              !isScrollingUp &&
              (!isScrolledDown || (!isHoveringLogo && !hasHoveredLogo)),
          }"
        >
          <!-- Animated background circuit pattern -->
          <div 
            class="absolute inset-0 rounded-full opacity-10 overflow-hidden"
            :class="{
              'opacity-10': isScrollingUp || (isScrolledDown && (isHoveringLogo || hasHoveredLogo)),
              'opacity-0': !isScrollingUp && (!isScrolledDown || (!isHoveringLogo && !hasHoveredLogo))
            }"
          >
            <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 via-blue-500/20 to-purple-600/20 animate-pulse"></div>
          </div>

          <!-- Glowing border effect -->
          <div 
            class="absolute inset-0 rounded-full border border-cyan-400/50 opacity-0 transition-opacity duration-300"
            :class="{
              'opacity-100 animate-pulse': isScrollingUp || (isScrolledDown && (isHoveringLogo || hasHoveredLogo))
            }"
          ></div>

          <div
            class="flex items-center space-x-4 transition-all duration-500 ease-in-out relative z-10"
            :class="{
              'bg-slate-900/90 backdrop-blur-sm rounded-full text-white shadow-lg border border-cyan-500/20':
                isScrolledDown || isScrollingUp,
            }"
            @mouseenter="onLogoHover(true)"
            @mouseleave="onLogoHover(false)"
          >
            <!-- Logo besar dengan efek robot -->
            <div
              class="flex items-center space-x-4 transition-opacity duration-300 cursor-pointer relative"
              :class="{
                'opacity-0 hidden': isScrolledDown || isScrollingUp,
                'opacity-100 flex': !isScrolledDown && !isScrollingUp,
              }"
            >
              <a
                href="#"
                title="Get quote now"
                class="relative inline-flex items-center justify-center py-4 text-xl sm:text-3xl lg:text-5xl font-bold text-transparent bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600 bg-clip-text transition-all duration-200 rounded-xl hover:scale-105 group"
              >
                <!-- Glowing text effect -->
                <span class="relative">
                  KHOERUL FAJRI
                  <div class="absolute inset-0 bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600 opacity-0 group-hover:opacity-20 blur-xl transition-opacity duration-300"></div>
                </span>
                
                <!-- Robot accent elements -->
                <div class="absolute -top-2 -right-2 w-3 h-3 bg-cyan-400 rounded-full animate-ping opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <div class="absolute -bottom-2 -left-2 w-2 h-2 bg-purple-400 rounded-full animate-pulse opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
              </a>
            </div>

            <!-- Logo kecil dengan efek futuristik -->
            <div class="relative">
              <span
                class="relative inline-flex items-center justify-center py-4 px-4 text-6xl font-bold text-transparent bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600 bg-clip-text transition-all duration-200 rounded-xl hover:scale-105 group"
                :class="{
                  'scale-75 opacity-100': isScrolledDown || isScrollingUp,
                  'scale-100 opacity-0': !isScrolledDown && !isScrollingUp,
                }"
              >KF</span>
              <!-- Glowing ring around logo -->
              <div 
                class="absolute inset-0 rounded-full border-2 border-cyan-400/30 opacity-0 transition-all duration-300"
                :class="{
                  'opacity-100 scale-110 animate-pulse': (isScrolledDown || isScrollingUp) && isHoveringLogo
                }"
              ></div>
            </div>
          </div>

          <!-- Navigation & Hamburger Wrapper dengan tema robot -->
          <div
            class="relative transition-all duration-500 ease-in-out ml-4"
            :class="{
              'rounded-full shadow-lg bg-slate-900/80 backdrop-blur-sm border border-cyan-500/20':
                isScrollingUp || isHoveringLogo || hasHoveredLogo,
              'bg-transparent':
                !isScrollingUp && !isHoveringLogo && !hasHoveredLogo,
            }"
          >
            <!-- Circuit pattern background -->
            <div class="absolute inset-0 rounded-full overflow-hidden opacity-10">
              <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/10 via-blue-500/10 to-purple-600/10"></div>
            </div>

            <div
              class="flex items-center justify-between gap-6 px-6 py-3 transition-opacity duration-500 relative z-10"
              :class="{
                'opacity-0': isScrolledDown && !isScrollingUp && !isHoveringLogo,
                'opacity-100':
                  !isScrolledDown ||
                  isScrollingUp ||
                  isHoveringLogo ||
                  hasHoveredLogo,
              }"
            >
              <!-- Nav links dengan efek futuristik -->
              <nav class="hidden lg:flex space-x-8 text-white font-semibold">
                <a
                  href="#home"
                  class="relative group px-3 py-2 transition-all duration-300 hover:text-cyan-400"
                >
                  <span class="relative z-10">Home</span>
                  <!-- Hover background effect -->
                  <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-lg opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                  <!-- Glowing underline -->
                  <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <!-- Side accent lines -->
                  <div class="absolute left-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                  <div class="absolute right-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                </a>
                
                <a
                  href="#about"
                  class="relative group px-3 py-2 transition-all duration-300 hover:text-cyan-400"
                >
                  <span class="relative z-10">About</span>
                  <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-lg opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                  <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute left-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                  <div class="absolute right-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                </a>
                
                <a
                  href="#project"
                  class="relative group px-3 py-2 transition-all duration-300 hover:text-cyan-400"
                >
                  <span class="relative z-10">Project</span>
                  <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-lg opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                  <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute left-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                  <div class="absolute right-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                </a>
                
                <a
                  href="#contact"
                  class="relative group px-3 py-2 transition-all duration-300 hover:text-cyan-400"
                >
                  <span class="relative z-10">Contact</span>
                  <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-lg opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                  <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-0 h-0.5 bg-gradient-to-r from-cyan-400 to-blue-500 group-hover:w-full transition-all duration-300"></div>
                  <div class="absolute left-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                  <div class="absolute right-0 top-1/2 transform -translate-y-1/2 w-0.5 h-0 bg-cyan-400 group-hover:h-full transition-all duration-300 delay-100"></div>
                </a>
              </nav>

              <!-- Hamburger dengan efek robot -->
              <button
                class="lg:p-3 hover:bg-cyan-500/20 rounded-full transition-all duration-300 lg:hidden relative group border border-cyan-500/30"
                @click="$emit('toggle-menu')"
              >
                <Menu class="w-5 h-5 sm:w-6 h-6 text-cyan-400 group-hover:text-white transition-colors duration-300" />
                <!-- Glowing effect on hover -->
                <div class="absolute inset-0 bg-cyan-400/20 rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <!-- Corner accents -->
                <div class="absolute top-0 left-0 w-2 h-2 border-t-2 border-l-2 border-cyan-400 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <div class="absolute top-0 right-0 w-2 h-2 border-t-2 border-r-2 border-cyan-400 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <div class="absolute bottom-0 left-0 w-2 h-2 border-b-2 border-l-2 border-cyan-400 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                <div class="absolute bottom-0 right-0 w-2 h-2 border-b-2 border-r-2 border-cyan-400 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
              </button>
            </div>
          </div>
        </div>

        <!-- Text below border dengan efek futuristik -->
        <div
          class="hidden lg:flex border-t border-t-cyan-500/50 md:flex justify-end w-full pt-2 pb-2 text-sm transition-all duration-500 ease-in-out relative"
          :class="{
            'opacity-0 hidden': isScrolledDown || isScrollingUp,
            'opacity-100 flex': !isScrolledDown && !isScrollingUp,
          }"
        >
          <!-- Animated border line -->
          <div class="absolute top-0 left-0 h-0.5 bg-gradient-to-r from-transparent via-cyan-400 to-transparent w-full animate-pulse"></div>
          
          <!-- Status indicator -->
          <div class="flex items-center gap-2 text-cyan-400 font-medium">
            <div class="w-2 h-2 bg-emerald-400 rounded-full animate-pulse"></div>
            <span>System Online</span>
          </div>
        </div>
      </div>
    </div>
  </div>
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

  // Enhanced border animation with robot theme
  gsap.fromTo(
    borderRef.value,
    { 
      scaleY: 0, 
      transformOrigin: "top center",
      filter: "brightness(0)"
    },
    {
      scaleY: 1,
      filter: "brightness(1)",
      duration: 1.2,
      ease: "power3.out",
    }
  );

  // Add glowing effect animation
  gsap.to(borderRef.value, {
    boxShadow: "0 0 30px rgba(6, 182, 212, 0.3)",
    duration: 2,
    ease: "power2.inOut",
    yoyo: true,
    repeat: -1
  });

  // Animate location text with robot effect
  if (locationRef.value) {
    gsap.from(locationRef.value, {
      y: 30,
      opacity: 0,
      duration: 1,
      delay: 0.8,
      ease: "back.out(1.7)",
    });
  }
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
/* Enhanced robot-themed styles */
header {
  transition: transform 0.3s ease, opacity 0.3s ease;
}

/* Futuristic glow effects */
.group:hover {
  filter: drop-shadow(0 0 10px rgba(6, 182, 212, 0.5));
}

/* Custom scrollbar for robot theme */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #1e293b;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #06b6d4, #3b82f6);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #0891b2, #2563eb);
}

/* Animated background patterns */
@keyframes circuitPulse {
  0%, 100% { opacity: 0.1; }
  50% { opacity: 0.3; }
}

.animate-circuit {
  animation: circuitPulse 3s ease-in-out infinite;
}

/* Enhanced hover effects for navigation */
nav a {
  position: relative;
  overflow: hidden;
}

nav a::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(6, 182, 212, 0.2), transparent);
  transition: left 0.5s;
}

nav a:hover::before {
  left: 100%;
}

/* Glowing text effect */
.text-glow {
  text-shadow: 0 0 10px rgba(6, 182, 212, 0.5);
}

/* Robot-themed focus styles */
button:focus-visible {
  outline: 2px solid rgba(6, 182, 212, 0.5);
  outline-offset: 2px;
}

/* Enhanced backdrop blur */
.backdrop-blur-md {
  backdrop-filter: blur(12px);
}
</style>