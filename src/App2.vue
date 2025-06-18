<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { ChevronDown, ChevronUp, ChevronLeft, ChevronRight } from "lucide-vue-next";

const chevronBtn = ref(null);
const chevronIcon = ref(null);
const rippleEffect = ref(null);
const glowRing = ref(null);

// State untuk direction chevron
const direction = ref('down'); // 'down', 'up', 'left', 'right'
const isAnimating = ref(false);

const chevronIcons = {
  down: ChevronDown,
  up: ChevronUp,
  left: ChevronLeft,
  right: ChevronRight
};

const directions = ['down', 'up', 'left', 'right'];

const handleClick = () => {
  if (isAnimating.value) return;
  
  isAnimating.value = true;
  
  // Ripple effect
  gsap.fromTo(rippleEffect.value,
    { scale: 0, opacity: 0.8 },
    { 
      scale: 4, 
      opacity: 0, 
      duration: 0.6,
      ease: "power2.out"
    }
  );

  // Icon rotation and scale animation
  gsap.timeline()
    .to(chevronIcon.value, {
      scale: 0,
      rotation: 180,
      duration: 0.3,
      ease: "back.in(2)"
    })
    .call(() => {
      // Change direction
      const currentIndex = directions.indexOf(direction.value);
      direction.value = directions[(currentIndex + 1) % directions.length];
    })
    .to(chevronIcon.value, {
      scale: 1,
      rotation: 360,
      duration: 0.4,
      ease: "back.out(2)"
    })
    .call(() => {
      isAnimating.value = false;
    });

  // Button pulse animation
  gsap.timeline()
    .to(chevronBtn.value, {
      scale: 0.95,
      duration: 0.1,
      ease: "power2.out"
    })
    .to(chevronBtn.value, {
      scale: 1.05,
      duration: 0.2,
      ease: "back.out(3)"
    })
    .to(chevronBtn.value, {
      scale: 1,
      duration: 0.2,
      ease: "power2.out"
    });

  // Glow ring animation
  gsap.fromTo(glowRing.value,
    { scale: 1, opacity: 0 },
    { 
      scale: 1.5, 
      opacity: 1, 
      duration: 0.3,
      ease: "power2.out",
      yoyo: true,
      repeat: 1
    }
  );
};

const handleMouseEnter = () => {
  if (isAnimating.value) return;
  
  gsap.to(chevronIcon.value, {
    scale: 1.2,
    rotation: 15,
    duration: 0.3,
    ease: "power2.out"
  });
  
  gsap.to(glowRing.value, {
    scale: 1.1,
    opacity: 0.3,
    duration: 0.3,
    ease: "power2.out"
  });
};

const handleMouseLeave = () => {
  if (isAnimating.value) return;
  
  gsap.to(chevronIcon.value, {
    scale: 1,
    rotation: 0,
    duration: 0.3,
    ease: "power2.out"
  });
  
  gsap.to(glowRing.value, {
    scale: 1,
    opacity: 0,
    duration: 0.3,
    ease: "power2.out"
  });
};

onMounted(() => {
  // Initial animation
  gsap.fromTo(chevronBtn.value,
    { scale: 0, rotation: -180, opacity: 0 },
    { 
      scale: 1, 
      rotation: 0, 
      opacity: 1, 
      duration: 0.8,
      ease: "back.out(1.7)"
    }
  );
  
  // Floating animation
  gsap.to(chevronBtn.value, {
    y: -5,
    duration: 2,
    ease: "power2.inOut",
    yoyo: true,
    repeat: -1
  });
});
</script>

<template>
  <div class="flex items-center justify-center h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900">
    <!-- Chevron Button -->
    <button
      ref="chevronBtn"
      @click="handleClick"
      @mouseenter="handleMouseEnter"
      @mouseleave="handleMouseLeave"
      class="relative group focus:outline-none"
    >
      <!-- Main Button -->
      <div class="relative w-20 h-20 bg-gradient-to-r from-cyan-500 via-blue-500 to-purple-600 rounded-full p-1 shadow-2xl hover:shadow-cyan-500/25 transition-all duration-300">
        <div class="w-full h-full bg-slate-900 rounded-full flex items-center justify-center relative overflow-hidden">
          
          <!-- Animated Background -->
          <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 via-blue-500/20 to-purple-600/20 rounded-full animate-pulse"></div>
          
          <!-- Chevron Icon -->
          <div ref="chevronIcon" class="relative z-10">
            <component 
              :is="chevronIcons[direction]" 
              class="w-8 h-8 text-cyan-400 transition-colors duration-300" 
            />
          </div>
          
          <!-- Ripple Effect -->
          <div 
            ref="rippleEffect"
            class="absolute inset-0 bg-cyan-400/30 rounded-full pointer-events-none"
          ></div>
        </div>
        
        <!-- Glow Ring -->
        <div 
          ref="glowRing"
          class="absolute inset-0 rounded-full border-2 border-cyan-400/50 opacity-0 pointer-events-none"
        ></div>
      </div>
      
      <!-- Outer Glow Ring -->
      <div class="absolute inset-0 rounded-full border border-cyan-400/20 scale-125 opacity-0 group-hover:opacity-100 group-hover:scale-150 transition-all duration-500 pointer-events-none"></div>
      
      <!-- Particles -->
      <div class="absolute -top-2 -left-2 w-2 h-2 bg-cyan-400 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-ping transition-opacity duration-300"></div>
      <div class="absolute -top-2 -right-2 w-1.5 h-1.5 bg-blue-400 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-pulse transition-opacity duration-300"></div>
      <div class="absolute -bottom-2 -left-2 w-1 h-1 bg-purple-400 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-bounce transition-opacity duration-300"></div>
      <div class="absolute -bottom-2 -right-2 w-2 h-2 bg-cyan-300 rounded-full opacity-0 group-hover:opacity-100 group-hover:animate-ping transition-opacity duration-300"></div>
      
      <!-- Energy Lines -->
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-32 h-32 opacity-0 group-hover:opacity-30 transition-opacity duration-500 pointer-events-none">
        <div class="absolute top-0 left-1/2 w-0.5 h-8 bg-gradient-to-t from-cyan-400 to-transparent transform -translate-x-1/2 animate-pulse"></div>
        <div class="absolute bottom-0 left-1/2 w-0.5 h-8 bg-gradient-to-b from-cyan-400 to-transparent transform -translate-x-1/2 animate-pulse"></div>
        <div class="absolute left-0 top-1/2 h-0.5 w-8 bg-gradient-to-l from-cyan-400 to-transparent transform -translate-y-1/2 animate-pulse"></div>
        <div class="absolute right-0 top-1/2 h-0.5 w-8 bg-gradient-to-r from-cyan-400 to-transparent transform -translate-y-1/2 animate-pulse"></div>
      </div>
    </button>
  </div>
</template>

<style scoped>
/* Custom animations */
@keyframes energyPulse {
  0%, 100% { 
    transform: scale(1) rotate(0deg);
    opacity: 0.5;
  }
  50% { 
    transform: scale(1.1) rotate(180deg);
    opacity: 1;
  }
}

@keyframes particleFloat {
  0%, 100% { 
    transform: translateY(0px) rotate(0deg);
    opacity: 0.3;
  }
  50% { 
    transform: translateY(-10px) rotate(180deg);
    opacity: 1;
  }
}

.animate-energy-pulse {
  animation: energyPulse 2s ease-in-out infinite;
}

.animate-particle-float {
  animation: particleFloat 3s ease-in-out infinite;
}

/* Hover glow effect */
button:hover .bg-gradient-to-r {
  filter: drop-shadow(0 0 20px rgba(6, 182, 212, 0.5));
}

/* Focus styles */
button:focus-visible {
  outline: 2px solid rgba(6, 182, 212, 0.5);
  outline-offset: 4px;
}
</style>