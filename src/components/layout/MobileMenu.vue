<template>
  <transition name="slide">
    <div
      v-if="isMenuOpen"
      class="fixed inset-0 z-50 bg-black/20 transition-all duration-500 backdrop-blur-md flex justify-end"
      @click.self="$emit('toggle-menu')"
    >
      <!-- Slide Panel -->
      <div
        class="w-3/4 sm:w-1/2 md:w-1/3 h-full bg-gradient-to-b from-gray-900 via-black to-gray-900 backdrop-blur-lg text-white p-6 shadow-2xl relative flex flex-col justify-between border-l border-cyan-400/30 overflow-hidden"
      >
        <!-- Animated Background Grid -->
        <div class="absolute inset-0 opacity-10">
          <div class="w-full h-full" style="background-image: linear-gradient(rgba(0,255,255,0.2) 1px, transparent 1px), linear-gradient(90deg, rgba(0,255,255,0.2) 1px, transparent 1px); background-size: 30px 30px; animation: grid-move 20s linear infinite;"></div>
        </div>

        <!-- Circuit Pattern -->
        <div class="absolute top-10 right-10 w-16 h-16 opacity-20">
          <svg viewBox="0 0 100 100" class="w-full h-full text-cyan-400 animate-spin" style="animation-duration: 15s;">
            <circle cx="50" cy="50" r="20" fill="none" stroke="currentColor" stroke-width="2"/>
            <circle cx="50" cy="50" r="5" fill="currentColor"/>
            <circle cx="30" cy="50" r="3" fill="currentColor"/>
            <circle cx="70" cy="50" r="3" fill="currentColor"/>
            <circle cx="50" cy="30" r="3" fill="currentColor"/>
            <circle cx="50" cy="70" r="3" fill="currentColor"/>
            <path d="M30 50 L70 50 M50 30 L50 70" stroke="currentColor" stroke-width="1"/>
          </svg>
        </div>

        <!-- Data Stream Lines -->
        <div class="absolute left-0 top-0 w-px h-full bg-gradient-to-b from-transparent via-cyan-400/30 to-transparent animate-pulse"></div>
        <div class="absolute right-0 top-0 w-px h-full bg-gradient-to-b from-transparent via-blue-400/30 to-transparent animate-pulse" style="animation-delay: 1s;"></div>

        <!-- Close Button -->
        <button
          class="absolute top-4 right-4 p-3 text-gray-400 hover:text-cyan-400 bg-gray-800/50 hover:bg-gray-700/70 rounded-full border border-cyan-400/30 hover:border-cyan-400/60 transition-all duration-300 hover:scale-110 z-10 group"
          @click="$emit('toggle-menu')"
        >
          <X class="w-6 h-6 group-hover:rotate-90 transition-transform duration-300" />
          <!-- Glowing effect -->
          <div class="absolute inset-0 rounded-full bg-cyan-400/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
        </button>

        <!-- Header Section -->
        <div class="relative z-10 mt-8">
          <div class="flex items-center space-x-3 mb-8">
            <div class="w-8 h-8 bg-gradient-to-br from-cyan-500 to-blue-500 rounded border border-cyan-400/50 flex items-center justify-center">
              <div class="w-2 h-2 bg-cyan-400 rounded-full animate-pulse"></div>
            </div>
            <div>
              <h2 class="text-cyan-400 font-mono text-sm uppercase tracking-wider">
                [MENU] NAVIGATION_SYSTEM
              </h2>
              <div class="flex items-center space-x-2 mt-1">
                <div class="w-1 h-1 bg-green-400 rounded-full animate-pulse"></div>
                <span class="text-green-400 font-mono text-xs">ONLINE</span>
              </div>
            </div>
          </div>

          <!-- Scanning Line Effect -->
          <div class="absolute left-0 w-full h-0.5 bg-gradient-to-r from-transparent via-cyan-400 to-transparent opacity-60 animate-scan"></div>
        </div>

        <!-- Navigation Links -->
        <nav class="relative z-10 space-y-4 flex-1">
          <a
            href="#home"
            @click="$emit('toggle-menu')"
            class="group flex items-center space-x-4 p-4 rounded-lg bg-gray-800/30 hover:bg-gray-700/50 border border-gray-700/50 hover:border-cyan-400/50 transition-all duration-300 hover:scale-105"
          >
            <div class="w-8 h-8 bg-gray-700 group-hover:bg-cyan-500 rounded border border-cyan-400/30 flex items-center justify-center transition-all duration-300">
              <svg class="w-4 h-4 text-cyan-400 group-hover:text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path>
              </svg>
            </div>
            <div class="flex-1">
              <span class="text-white group-hover:text-cyan-400 font-mono text-lg transition-colors duration-300">HOME</span>
            </div>
            <div class="w-2 h-2 bg-cyan-400 rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
          </a>

          <a
            href="#about"
            @click="$emit('toggle-menu')"
            class="group flex items-center space-x-4 p-4 rounded-lg bg-gray-800/30 hover:bg-gray-700/50 border border-gray-700/50 hover:border-cyan-400/50 transition-all duration-300 hover:scale-105"
          >
            <div class="w-8 h-8 bg-gray-700 group-hover:bg-blue-500 rounded border border-blue-400/30 flex items-center justify-center transition-all duration-300">
              <svg class="w-4 h-4 text-blue-400 group-hover:text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path>
              </svg>
            </div>
            <div class="flex-1">
              <span class="text-white group-hover:text-blue-400 font-mono text-lg transition-colors duration-300">ABOUT</span>
            </div>
            <div class="w-2 h-2 bg-blue-400 rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
          </a>

          <a
            href="#project"
            @click="$emit('toggle-menu')"
            class="group flex items-center space-x-4 p-4 rounded-lg bg-gray-800/30 hover:bg-gray-700/50 border border-gray-700/50 hover:border-cyan-400/50 transition-all duration-300 hover:scale-105"
          >
            <div class="w-8 h-8 bg-gray-700 group-hover:bg-green-500 rounded border border-green-400/30 flex items-center justify-center transition-all duration-300">
              <svg class="w-4 h-4 text-green-400 group-hover:text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"></path>
              </svg>
            </div>
            <div class="flex-1">
              <span class="text-white group-hover:text-green-400 font-mono text-lg transition-colors duration-300">PROJECT</span>
            </div>
            <div class="w-2 h-2 bg-green-400 rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
          </a>

          <a
            href="#contact"
            @click="$emit('toggle-menu')"
            class="group flex items-center space-x-4 p-4 rounded-lg bg-gray-800/30 hover:bg-gray-700/50 border border-gray-700/50 hover:border-cyan-400/50 transition-all duration-300 hover:scale-105"
          >
            <div class="w-8 h-8 bg-gray-700 group-hover:bg-purple-500 rounded border border-purple-400/30 flex items-center justify-center transition-all duration-300">
              <svg class="w-4 h-4 text-purple-400 group-hover:text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
              </svg>
            </div>
            <div class="flex-1">
              <span class="text-white group-hover:text-purple-400 font-mono text-lg transition-colors duration-300">CONTACT</span>
            </div>
            <div class="w-2 h-2 bg-purple-400 rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
          </a>
        </nav>

        <!-- Bottom Section -->
        <div class="relative z-10 border-t border-gray-700/50 pt-6">
          <div class="flex items-end justify-between">
            <!-- Brand Info -->
            <div class="flex-1">
              <div class="flex items-center space-x-2 mb-2">
                <div class="w-2 h-2 bg-cyan-400 rounded-full animate-pulse"></div>
                <span class="text-cyan-400 font-mono text-xs uppercase tracking-wider">Powered by</span>
              </div>
              <div class="text-white font-mono">
                <span class="text-xl font-bold bg-gradient-to-r from-cyan-400 to-blue-400 bg-clip-text text-transparent">
                  khoerul_fajri
                </span>
              </div>
              <div class="flex items-center space-x-2 mt-1">
                <div class="w-1 h-1 bg-green-400 rounded-full animate-pulse"></div>
                <span class="text-green-400 font-mono text-xs">v1.0.0</span>
              </div>
            </div>

            <!-- Social Media Section -->
            <div class="bg-gray-800/50 backdrop-blur-sm rounded-t-2xl border border-cyan-400/30 border-b-0 p-4 relative overflow-hidden">
              <!-- Glowing effect -->
              <div class="absolute inset-0 bg-gradient-to-t from-cyan-400/10 to-transparent"></div>
              
              <div class="relative z-10 flex flex-col items-center space-y-3">
                <div class="text-cyan-400 font-mono text-xs uppercase tracking-wider mb-2">
                  [SOCIAL] NETWORKS
                </div>
                
                <a
                  href="https://www.linkedin.com/in/khoerul-fajri-93698a229/"
                  class="group w-10 h-10 bg-gray-700/50 hover:bg-blue-600 rounded-full border border-blue-400/30 hover:border-blue-400/60 transition-all duration-300 hover:scale-110 flex items-center justify-center relative overflow-hidden"
                >
                  <Linkedin class="w-5 h-5 text-blue-400 group-hover:text-white transition-colors duration-300 relative z-10" />
                  <div class="absolute inset-0 bg-blue-400/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                </a>
                
                <a
                  href="https://github.com/khoerulfajri1999/"
                  class="group w-10 h-10 bg-gray-700/50 hover:bg-pink-600 rounded-full border border-pink-400/30 hover:border-pink-400/60 transition-all duration-300 hover:scale-110 flex items-center justify-center relative overflow-hidden"
                >
                  <Github class="w-5 h-5 text-pink-400 group-hover:text-white transition-colors duration-300 relative z-10" />
                  <div class="absolute inset-0 bg-pink-400/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                </a>
                
                <a
                  href="https://wa.me/62882003233343"
                  class="group w-10 h-10 bg-gray-700/50 hover:bg-cyan-600 rounded-full border border-cyan-400/30 hover:border-cyan-400/60 transition-all duration-300 hover:scale-110 flex items-center justify-center relative overflow-hidden"
                >
                  <MessageCircle class="w-5 h-5 text-cyan-400 group-hover:text-white transition-colors duration-300 relative z-10" />
                  <div class="absolute inset-0 bg-cyan-400/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- Floating Data Particles -->
        <div class="absolute inset-0 overflow-hidden pointer-events-none">
          <div class="absolute top-1/4 left-1/6 w-1 h-1 bg-cyan-400 rounded-full opacity-40 animate-ping"></div>
          <div class="absolute top-1/2 right-1/4 w-1 h-1 bg-blue-400 rounded-full opacity-30 animate-pulse"></div>
          <div class="absolute bottom-1/3 left-1/3 w-1 h-1 bg-green-400 rounded-full opacity-50 animate-bounce"></div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { X, Facebook, Instagram, Twitter, Linkedin, Github, MessageCircle } from "lucide-vue-next";

defineProps({ isMenuOpen: Boolean });
</script>

<style scoped>
/* Slide Animation */
.slide-enter-from {
  transform: translateX(100%);
  opacity: 0;
}
.slide-enter-to {
  transform: translateX(0%);
  opacity: 1;
}
.slide-leave-from {
  transform: translateX(0%);
  opacity: 1;
}
.slide-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
.slide-enter-active,
.slide-leave-active {
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Grid Animation */
@keyframes grid-move {
  0% { background-position: 0 0; }
  100% { background-position: 30px 30px; }
}

/* Scanning Line Animation */
@keyframes scan {
  0% { transform: translateX(-100%) scaleX(0); opacity: 0; }
  50% { opacity: 1; scaleX: 1; }
  100% { transform: translateX(200%) scaleX(0); opacity: 0; }
}

.animate-scan {
  animation: scan 3s linear infinite;
}

/* Hover Effects */
.nav-link:hover {
  transform: translateX(5px);
}

/* Glitch Effect for Brand */
.brand-glitch {
  position: relative;
}

.brand-glitch::before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  color: #00ffff;
  z-index: -1;
  animation: glitch-1 0.3s infinite;
}

@keyframes glitch-1 {
  0%, 100% { transform: translate(0); }
  20% { transform: translate(-1px, 1px); }
  40% { transform: translate(-1px, -1px); }
  60% { transform: translate(1px, 1px); }
  80% { transform: translate(1px, -1px); }
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 4px;
}

::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.2);
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #00ffff, #0080ff);
  border-radius: 2px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #00cccc, #0066cc);
}

/* Responsive adjustments */
@media (max-width: 640px) {
  .slide-panel {
    width: 85%;
  }
}

/* Backdrop blur fallback */
@supports not (backdrop-filter: blur(10px)) {
  .backdrop-blur-lg {
    background-color: rgba(0, 0, 0, 0.9);
  }
  
  .backdrop-blur-sm {
    background-color: rgba(0, 0, 0, 0.8);
  }
}
</style>