<template>
  <div
    class="fixed inset-0 bg-black/60 backdrop-blur-sm flex items-center justify-center z-50"
  >
    <!-- Subtle Background Pattern -->
    <div class="absolute inset-0 opacity-5">
      <div
        class="absolute inset-0"
        style="
          background-image: radial-gradient(
              circle at 25% 25%,
              #fbbf24 1px,
              transparent 1px
            ),
            radial-gradient(circle at 75% 75%, #fbbf24 1px, transparent 1px);
          background-size: 40px 40px;
        "
      ></div>
    </div>

    <!-- Main Content Card -->
    <div
      class="relative bg-white/10 backdrop-blur-md border border-white/20 rounded-2xl shadow-2xl p-8 max-w-lg mx-4"
    >
      <!-- Construction Icon -->
      <div class="mb-6 flex justify-center">
        <div class="relative">
          <div
            class="w-16 h-16 bg-yellow-300/90 rounded-full flex items-center justify-center animate-bounce shadow-lg"
          >
            <svg
              class="w-8 h-8 text-slate-900"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M21,8H20V6A2,2 0 0,0 18,4H16V2H14V4H10V2H8V4H6A2,2 0 0,0 4,6V8H3A1,1 0 0,0 2,9V11A1,1 0 0,0 3,12H4V18A2,2 0 0,0 6,20H18A2,2 0 0,0 20,18V12H21A1,1 0 0,0 22,11V9A1,1 0 0,0 21,8M18,18H6V6H18V18Z"
              />
            </svg>
          </div>
          <!-- Small rotating gear -->
          <div
            class="absolute -top-1 -right-1 w-6 h-6 bg-amber-400/90 rounded-full flex items-center justify-center animate-spin shadow-md"
          >
            <svg
              class="w-3 h-3 text-black"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M12,15.5A3.5,3.5 0 0,1 8.5,12A3.5,3.5 0 0,1 12,8.5A3.5,3.5 0 0,1 15.5,12A3.5,3.5 0 0,1 12,15.5M19.43,12.97C19.47,12.65 19.5,12.33 19.5,12C19.5,11.67 19.47,11.34 19.43,11.03L21.54,9.37C21.73,9.22 21.78,8.95 21.66,8.73L19.66,5.27C19.54,5.05 19.27,4.96 19.05,5.05L16.56,6.05C16.04,5.66 15.5,5.32 14.87,5.07L14.5,2.42C14.46,2.18 14.25,2 14,2H10C9.75,2 9.54,2.18 9.5,2.42L9.13,5.07C8.5,5.32 7.96,5.66 7.44,6.05L4.95,5.05C4.73,4.96 4.46,5.05 4.34,5.27L2.34,8.73C2.22,8.95 2.27,9.22 2.46,9.37L4.57,11.03C4.53,11.34 4.5,11.67 4.5,12C4.5,12.33 4.53,12.65 4.57,12.97L2.46,14.63C2.27,14.78 2.22,15.05 2.34,15.27L4.34,18.73C4.46,18.95 4.73,19.03 4.95,18.95L7.44,17.94C7.96,18.34 8.5,18.68 9.13,18.93L9.5,21.58C9.54,21.82 9.75,22 10,22H14C14.25,22 14.46,21.82 14.5,21.58L14.87,18.93C15.5,18.68 16.04,18.34 16.56,17.94L19.05,18.95C19.27,19.03 19.54,18.95 19.66,18.73L21.66,15.27C21.78,15.05 21.73,14.78 21.54,14.63L19.43,12.97Z"
              />
            </svg>
          </div>
        </div>
      </div>

      <!-- Main Title -->
      <h1
        class="text-3xl md:text-4xl font-bold text-center mb-4 tracking-tight"
      >
        <span
          class="bg-gradient-to-r from-white via-neutral-300 to-neutral-500 bg-clip-text text-transparent"
        >
          Under Construction
        </span>
      </h1>

      <!-- Subtitle -->
      <p class="text-center text-white/90 mb-6 leading-relaxed">
        Website sedang dalam tahap pengembangan.
        <br />
        Mohon bersabar, akan segera hadir!
      </p>

      <!-- Compact Progress Bar -->
      <div class="mb-6">
        <div class="flex justify-between text-xs text-white/70 mb-2">
          <span>Progress</span>
          <span>{{ Math.floor(progress) }}%</span>
        </div>
        <div class="w-full bg-white/20 rounded-full h-2 overflow-hidden">
          <div
            class="h-full bg-gradient-to-r from-white to-neutral-500 rounded-full transition-all duration-300 ease-out shadow-sm"
            :style="{ width: progress + '%' }"
          ></div>
        </div>
      </div>

      <!-- Simple Status Message -->
      <div class="text-center bg-white/5 rounded-lg p-4 border border-white/10">
        <p class="text-white/80 text-sm">🚧 Sedang dalam pengembangan</p>
        <p class="text-white/60 text-xs mt-1">
          Terima kasih atas kesabaran Anda
        </p>
      </div>
    </div>

    <!-- Subtle Floating Elements -->
    <div
      class="absolute top-1/4 left-1/4 w-2 h-2 bg-yellow-400/60 rounded-full animate-ping"
    ></div>
    <div
      class="absolute bottom-1/3 right-1/4 w-3 h-3 bg-orange-400/40 rounded-full animate-pulse"
    ></div>
    <div
      class="absolute top-1/2 right-1/6 w-1 h-1 bg-red-400/50 rounded-full animate-bounce"
    ></div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const progress = ref(0);
let progressInterval = null;

// Animate progress bar slowly
onMounted(() => {
  progressInterval = setInterval(() => {
    if (progress.value < 75) {
      progress.value += Math.random() * 1;
    } else if (progress.value < 90) {
      progress.value += Math.random() * 0.3;
    }
  }, 300);
});

onUnmounted(() => {
  if (progressInterval) {
    clearInterval(progressInterval);
  }
});
</script>

<style scoped>
/* Ensure smooth backdrop blur */
.backdrop-blur-sm {
  backdrop-filter: blur(4px);
}

.backdrop-blur-md {
  backdrop-filter: blur(8px);
}

/* Subtle glow effect */
.shadow-2xl {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25),
    0 0 0 1px rgba(255, 255, 255, 0.1);
}
</style>
