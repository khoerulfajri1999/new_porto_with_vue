<template>
  <div
    class="h-screen bg-black/60 text-white relative overflow-hidden flex flex-col"
  >
    <!-- Background Image -->
    <div class="absolute inset-0 z-0">
      <img
        src="./assets/bg-image.webp"
        alt="stevara.id-background"
        class="w-full h-full object-cover opacity-80"
      />
      <div class="absolute inset-0 bg-black/40"></div>
    </div>

    <!-- Header -->
    <header
      class="relative z-10 flex items-center justify-between px-6 py-4 lg:px-8 lg:py-6 flex-shrink-0"
    >
      <!-- Logo and Tagline -->
      <div class="flex items-center space-x-4">
        <div class="flex items-center space-x-4">
          <img
            class="w-80"
            src="./assets/Logo PT Dark.png"
            alt="stevara.id-logo"
          />
          <div class="h-12 border-r-2 border-white"></div>
        </div>
        <div class="hidden lg:block">
          <p class="text-sm text-gray-300 pl-2">Everything<br />you can be</p>
        </div>
      </div>

      <!-- Navigation -->
      <div class="flex items-center space-x-4">
        <button
          class="p-2 hover:bg-white/10 rounded-full transition-colors"
          @click="toggleMenu"
        >
          <Menu class="w-6 h-6" />
        </button>
      </div>
    </header>

    <!-- Main Content -->
    <main
      class="relative z-10 flex-1 flex flex-col justify-center px-6 lg:px-8"
    >
      <div class="max-w-2xl">
        <!-- Main Heading -->
        <h2
          class="text-4xl md:text-5xl lg:text-7xl font-bold mb-6 lg:mb-8 leading-tight"
        >
          Lets<br />
          <span class="text-white">Connect.</span>
        </h2>

        <!-- Description -->
        <div
          class="space-y-3 lg:space-y-4 mb-8 lg:mb-12 text-gray-300 text-base lg:text-lg xl:text-xl leading-relaxed"
        >
          <p>One message could be the start of something great.</p>
          <p>
            We are the experience of true self-expression<br />
            that goes beyond traditional limitations.
          </p>
        </div>

        <!-- CTA Section -->
        <div class="flex items-center space-x-6">
          <button
            class="bg-blue-500 hover:bg-blue-600 text-white px-6 lg:px-8 py-3 lg:py-4 rounded-full font-semibold text-base lg:text-lg transition-colors"
            @click="goToShop"
          >
            Contact Us
          </button>
          <div class="h-12 border-r-2 border-white"></div>
          <div class="text-gray-300">
            <p class="text-sm">Everything<br />you can be</p>
          </div>
        </div>
      </div>
    </main>

    <!-- Footer -->
    <footer
      class="relative z-10 flex items-end justify-between px-6 lg:px-8 flex-shrink-0"
    >
      <!-- Brand Info -->
      <div class="text-xs pb-10 text-gray-400">
        <p>Powered by</p>
        <p class="font-semibold text-white">
          stevara <span class="font-normal">.id</span>
        </p>
      </div>

      <!-- Social Media -->
      <div
        class="flex flex-col me-30 space-y-5 px-3 bg-white/40 backdrop-blur-sm rounded-t-full py-3"
      >
        <button
          class="hover:bg-white/20 rounded-full transition-colors text-white"
          @click="openSocial('facebook')"
        >
          <Facebook class="w-4 h-4" />
        </button>
        <button
          class="hover:bg-white/20 rounded-full transition-colors text-white"
          @click="openSocial('instagram')"
        >
          <Instagram class="w-4 h-4" />
        </button>
        <button
          class="hover:bg-white/20 rounded-full transition-colors text-white"
          @click="openSocial('twitter')"
        >
          <Twitter class="w-4 h-4" />
        </button>
      </div>
    </footer>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-16 left-1/2 transform -translate-x-1/2 z-10">
      <ChevronDown class="w-6 h-6 text-white animate-bounce" />
    </div>

    <!-- Mobile Menu Overlay -->
    <div
      v-if="isMenuOpen"
      class="fixed inset-0 bg-black/50 z-85 flex items-center justify-center"
      @click="toggleMenu"
    >
      <div class="text-center space-y-8">
        <button class="absolute top-6 right-6 p-2" @click="toggleMenu">
          <X class="w-8 h-8" />
        </button>
        <nav class="space-y-6 text-2xl">
          <a href="#" class="block hover:text-blue-400 transition-colors"
            >Products</a
          >
          <a href="#" class="block hover:text-blue-400 transition-colors"
            >About</a
          >
          <a href="#" class="block hover:text-blue-400 transition-colors"
            >Science</a
          >
          <a href="#" class="block hover:text-blue-400 transition-colors"
            >Contact</a
          >
        </nav>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import {
  ShoppingBag,
  Menu,
  Facebook,
  Instagram,
  Twitter,
  ChevronDown,
  X,
} from "lucide-vue-next";

// Reactive state
const cartCount = ref(0);
const isMenuOpen = ref(false);

// Methods
const toggleCart = () => {
  console.log("Cart clicked");
  // Add cart functionality here
};

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const goToShop = () => {
  console.log("Shop button clicked");
  // Add navigation to shop page
};

const openSocial = (platform) => {
  console.log(`Opening ${platform}`);
  // Add social media links
  const urls = {
    facebook: "https://facebook.com/stevara",
    instagram: "https://instagram.com/stevara",
    twitter: "https://twitter.com/stevara",
  };
  window.open(urls[platform], "_blank");
};
</script>

<style scoped>
/* Custom animations */
@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}

/* Smooth transitions */
* {
  transition: all 0.3s ease;
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 4px;
}

::-webkit-scrollbar-track {
  background: rgba(255, 255, 255, 0.1);
}

::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255, 0.3);
  border-radius: 2px;
}

::-webkit-scrollbar-thumb:hover {
  background: rgba(255, 255, 255, 0.5);
}
</style>
