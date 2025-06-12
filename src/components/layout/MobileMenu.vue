<template>
  <transition name="slide">
    <div
      v-if="isMenuOpen"
      class="fixed inset-0 z-50 bg-black/10 transition-all duration-300 backdrop-blur-sm flex justify-end"
      @click.self="$emit('toggle-menu')"
    >
      <!-- Slide Panel -->
      <div
        class="w-3/4 sm:w-1/2 md:w-1/3 h-full bg-black/90 backdrop-blur-sm text-white p-6 shadow-lg relative flex flex-col justify-between"
      >
        <!-- Close Button -->
        <button
          class="absolute top-4 right-4 p-2 text-gray-500 hover:text-white"
          @click="$emit('toggle-menu')"
        >
          <X class="w-6 h-6" />
        </button>

        <!-- Navigation Links -->
        <nav class="mt-16 space-y-6 text-xl font-semibold">
          <a
            href="#home"
            @click="$emit('toggle-menu')"
            class="block hover:text-blue-500 transition"
            >Home</a
          >
          <a
            href="#services"
            @click="$emit('toggle-menu')"
            class="block hover:text-blue-500 transition"
            >Services</a
          >
          <a
            href="#about"
            @click="$emit('toggle-menu')"
            class="block hover:text-blue-500 transition"
            >About</a
          >
          <a
            href="#home"
            @click="$emit('toggle-menu')"
            class="block hover:text-blue-500 transition"
            >Contact</a
          >
        </nav>

        <!-- Social Media Section -->
        <div class="flex items-center justify-between border-t border-white/20">
          <div class="text-md text-gray-400 mt-40">
            <p>Powered by</p>
            <p class="font-semibold text-white">
              stevara <span class="font-normal">.id</span>
            </p>
          </div>
          <div
            class="mt-10 flex flex-col items-end space-y-4 px-3 bg-white/20 backdrop-blur-sm rounded-t-full py-3 self-end"
          >
            <button
              class="hover:bg-white/30 rounded-full transition-colors text-white p-2"
              @click="$emit('open-social', 'facebook')"
            >
              <Facebook class="w-5 h-5 md:w-6 md:h-6 lg:w-7 lg:h-7" />
            </button>
            <button
              class="hover:bg-white/30 rounded-full transition-colors text-white p-2"
              @click="$emit('open-social', 'instagram')"
            >
              <Instagram class="w-5 h-5 md:w-6 md:h-6 lg:w-7 lg:h-7" />
            </button>
            <button
              class="hover:bg-white/30 rounded-full transition-colors text-white p-2"
              @click="$emit('open-social', 'twitter')"
            >
              <Twitter class="w-5 h-5 md:w-6 md:h-6 lg:w-7 lg:h-7" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { X, Facebook, Instagram, Twitter } from "lucide-vue-next";

defineProps({ isMenuOpen: Boolean });
</script>

<style scoped>
.slide-enter-from {
  transform: translateX(100%);
}
.slide-enter-to {
  transform: translateX(0%);
}
.slide-leave-from {
  transform: translateX(0%);
}
.slide-leave-to {
  transform: translateX(100%);
}
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.4s ease;
}
</style>
