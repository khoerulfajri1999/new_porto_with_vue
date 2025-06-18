<template>
  <div class="flex items-center justify-center relative ">
    
    <!-- Background Effects -->
    <div class="absolute inset-0">
      <div class="absolute inset-0 bg-[linear-gradient(rgba(6,182,212,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(6,182,212,0.1)_1px,transparent_1px)] bg-[size:50px_50px] animate-pulse"></div>
      
      <!-- Floating particles -->
      <div class="absolute top-20 left-20 w-2 h-2 bg-cyan-400/20 rounded-full animate-ping"></div>
      <div class="absolute top-40 right-32 w-1 h-1 bg-blue-400/30 rounded-full animate-pulse"></div>
      <div class="absolute bottom-32 left-40 w-1.5 h-1.5 bg-purple-400/20 rounded-full animate-bounce"></div>
      <div class="absolute bottom-20 right-20 w-1 h-1 bg-emerald-400/25 rounded-full animate-ping"></div>
    </div>

    <!-- Main Chevron Button -->
    <div class="relative">
      <!-- Hover Detection Area -->
      <div 
        class="relative w-30 h-30 flex items-center justify-center cursor-pointer group animate-float"
        @click="handleClick"
        @mouseenter="handleHover"
      >
        <!-- Outer Glow Ring -->
        <div class="absolute w-35 h-35 border-2 border-transparent rounded-full bg-gradient-to-r from-cyan-500 via-blue-500 via-purple-500 to-cyan-500 bg-[length:400%_400%] opacity-0 scale-75 transition-all duration-500 group-hover:opacity-60 group-hover:scale-100 group-hover:shadow-[0_0_50px_rgba(6,182,212,0.4)] animate-gradient-shift"></div>
        
        <!-- Middle Ring -->
        <div class="absolute w-25 h-25 border border-cyan-400/30 rounded-full transition-all duration-700 group-hover:rotate-180 group-hover:border-cyan-400/80 group-hover:shadow-[0_0_30px_rgba(6,182,212,0.3)]"></div>
        
        <!-- Inner Ring -->
        <div class="absolute w-20 h-20 border border-purple-400/20 rounded-full animate-pulse-ring group-hover:border-purple-400/60 group-hover:animate-pulse-ring-fast"></div>
        
        <!-- Main Button -->
        <div class="relative w-[70px] h-[70px] bg-slate-900/80 border-2 border-cyan-400/40 rounded-full flex items-center justify-center backdrop-blur-md transition-all duration-300 overflow-hidden z-10 group-hover:bg-cyan-400/10 group-hover:border-cyan-400/80 group-hover:shadow-[0_0_40px_rgba(6,182,212,0.4),inset_0_0_20px_rgba(6,182,212,0.1)] group-hover:scale-105 group-active:scale-95">
          
          <!-- Background Gradient -->
          <div class="absolute inset-0 bg-radial-gradient from-cyan-400/10 to-transparent rounded-full opacity-0 transition-opacity duration-300 group-hover:opacity-100"></div>
          
          <!-- Scanning Line -->
          <div class="absolute top-0 left-0 w-full h-0.5 bg-gradient-to-r from-transparent via-cyan-400 to-transparent rounded-full opacity-0 -translate-y-full animate-scan-line group-hover:opacity-100"></div>
          
          <!-- Chevron Icon -->
          <ChevronDown class="w-8 h-8 text-cyan-400 transition-all duration-300 z-10 drop-shadow-[0_0_10px_rgba(6,182,212,0.5)] group-hover:text-white group-hover:translate-y-1 group-hover:scale-110 group-hover:drop-shadow-[0_0_20px_rgba(6,182,212,0.8)]" />
          
          <!-- Corner Brackets -->
          <div class="absolute top-2 left-2 w-3 h-3 border-l-2 border-t-2 border-cyan-400/40 opacity-0 transition-all duration-300 group-hover:opacity-100 group-hover:border-cyan-400/80"></div>
          <div class="absolute top-2 right-2 w-3 h-3 border-r-2 border-t-2 border-cyan-400/40 opacity-0 transition-all duration-300 group-hover:opacity-100 group-hover:border-cyan-400/80"></div>
          <div class="absolute bottom-2 left-2 w-3 h-3 border-l-2 border-b-2 border-cyan-400/40 opacity-0 transition-all duration-300 group-hover:opacity-100 group-hover:border-cyan-400/80"></div>
          <div class="absolute bottom-2 right-2 w-3 h-3 border-r-2 border-b-2 border-cyan-400/40 opacity-0 transition-all duration-300 group-hover:opacity-100 group-hover:border-cyan-400/80"></div>
          
          <!-- Energy Particles -->
          <div class="absolute top-4 left-4 w-1 h-1 bg-cyan-400 rounded-full opacity-0 transition-all duration-300 animate-particle-float-1 group-hover:opacity-100 group-hover:shadow-[0_0_10px_#06b6d4]"></div>
          <div class="absolute top-4 right-4 w-1 h-1 bg-cyan-400 rounded-full opacity-0 transition-all duration-300 animate-particle-float-2 group-hover:opacity-100 group-hover:shadow-[0_0_10px_#06b6d4]"></div>
          <div class="absolute bottom-4 left-4 w-1 h-1 bg-cyan-400 rounded-full opacity-0 transition-all duration-300 animate-particle-float-3 group-hover:opacity-100 group-hover:shadow-[0_0_10px_#06b6d4]"></div>
          <div class="absolute bottom-4 right-4 w-1 h-1 bg-cyan-400 rounded-full opacity-0 transition-all duration-300 animate-particle-float-4 group-hover:opacity-100 group-hover:shadow-[0_0_10px_#06b6d4]"></div>
        </div>
        
        <!-- Ripple Effect -->
        <div 
          ref="rippleRef" 
          class="absolute w-full h-full border-2 border-cyan-400/60 rounded-full opacity-0 scale-0 pointer-events-none"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ChevronDown } from 'lucide-vue-next'

const rippleRef = ref(null)

const handleClick = () => {
  console.log('Chevron button clicked!')
  
  // Trigger ripple effect
  if (rippleRef.value) {
    rippleRef.value.classList.remove('animate-ripple')
    void rippleRef.value.offsetWidth // Force reflow
    rippleRef.value.classList.add('animate-ripple')
  }
  
  // Haptic feedback
  if (navigator.vibrate) {
    navigator.vibrate([50, 30, 50])
  }
}

const handleHover = () => {
  console.log('Chevron button hovered!')
}
</script>

<style scoped>
/* Custom animations that can't be replicated with Tailwind */
@keyframes float {
  0%, 100% { 
    transform: translateY(0px) rotate(0deg); 
  }
  50% { 
    transform: translateY(-15px) rotate(1deg); 
  }
}

@keyframes gradient-shift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

@keyframes pulse-ring {
  0%, 100% { 
    transform: scale(1); 
    opacity: 1; 
  }
  50% { 
    transform: scale(1.05); 
    opacity: 0.7; 
  }
}

@keyframes pulse-ring-fast {
  0%, 100% { 
    transform: scale(1); 
    opacity: 1; 
  }
  50% { 
    transform: scale(1.05); 
    opacity: 0.7; 
  }
}

@keyframes scan-line {
  0% { 
    transform: translateY(-100%) scaleX(0); 
    opacity: 0; 
  }
  50% { 
    transform: translateY(3400%) scaleX(1); 
    opacity: 1; 
  }
  100% { 
    transform: translateY(3500%) scaleX(0); 
    opacity: 0; 
  }
}

@keyframes particle-float-1 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(-5px, -5px) scale(1.2); }
}

@keyframes particle-float-2 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(5px, -5px) scale(1.2); }
}

@keyframes particle-float-3 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(-5px, 5px) scale(1.2); }
}

@keyframes particle-float-4 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(5px, 5px) scale(1.2); }
}

@keyframes ripple {
  0% {
    transform: scale(0);
    opacity: 1;
  }
  100% {
    transform: scale(2);
    opacity: 0;
  }
}

/* Apply animations */
.animate-float {
  animation: float 4s ease-in-out infinite;
}

.animate-gradient-shift {
  animation: gradient-shift 3s ease infinite;
}

.animate-pulse-ring {
  animation: pulse-ring 2s ease-in-out infinite;
}

.animate-pulse-ring-fast {
  animation: pulse-ring-fast 1s ease-in-out infinite;
}

.animate-scan-line {
  animation: scan-line 2s linear infinite;
}

.animate-particle-float-1 {
  animation: particle-float-1 3s ease-in-out infinite;
}

.animate-particle-float-2 {
  animation: particle-float-2 3s ease-in-out infinite 0.5s;
}

.animate-particle-float-3 {
  animation: particle-float-3 3s ease-in-out infinite 1s;
}

.animate-particle-float-4 {
  animation: particle-float-4 3s ease-in-out infinite 1.5s;
}

.animate-ripple {
  animation: ripple 0.6s ease-out;
}

/* Custom utilities */
.bg-radial-gradient {
  background: radial-gradient(circle at center, var(--tw-gradient-stops));
}
</style>
