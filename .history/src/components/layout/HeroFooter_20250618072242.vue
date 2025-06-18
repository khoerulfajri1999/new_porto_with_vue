<template>
  <div class="min-h-screen bg-gradient-to-br from-[#030415] via-[#1E0B38] to-[#030415] flex items-center justify-center p-8">
    <!-- Background Effects -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute inset-0 bg-[linear-gradient(rgba(6,182,212,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(6,182,212,0.1)_1px,transparent_1px)] bg-[size:50px_50px] animate-pulse"></div>
      
      <!-- Floating particles -->
      <div class="absolute top-20 left-20 w-2 h-2 bg-cyan-400/30 rounded-full animate-ping"></div>
      <div class="absolute top-40 right-32 w-1 h-1 bg-blue-400/40 rounded-full animate-pulse"></div>
      <div class="absolute bottom-32 left-40 w-1.5 h-1.5 bg-purple-400/30 rounded-full animate-bounce"></div>
    </div>

    <div class="relative z-10 max-w-6xl mx-auto">
      <!-- Title -->
      <div class="text-center mb-16">
        <h1 class="text-6xl font-bold bg-gradient-to-r from-cyan-400 via-blue-400 to-purple-400 bg-clip-text text-transparent mb-4">
          Robot Chevrons
        </h1>
        <p class="text-slate-300 text-lg">Futuristic directional indicators with advanced visual effects</p>
      </div>

      <!-- Chevron Showcase Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-16">
        
        <!-- Basic Animated Chevron -->
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 text-center hover:border-cyan-400/50 transition-all duration-300">
          <h3 class="text-cyan-400 font-semibold mb-6">Basic Animated</h3>
          <div class="flex justify-center">
            <div 
              class="chevron-basic"
              @click="handleChevronClick('basic')"
            >
              <ChevronDown class="w-12 h-12 text-cyan-400" />
            </div>
          </div>
        </div>

        <!-- Holographic Chevron -->
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 text-center hover:border-emerald-400/50 transition-all duration-300">
          <h3 class="text-emerald-400 font-semibold mb-6">Holographic</h3>
          <div class="flex justify-center">
            <div 
              class="chevron-holographic"
              @click="handleChevronClick('holographic')"
            >
              <ChevronRight class="w-12 h-12 text-emerald-400" />
            </div>
          </div>
        </div>

        <!-- Scanning Chevron -->
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 text-center hover:border-purple-400/50 transition-all duration-300">
          <h3 class="text-purple-400 font-semibold mb-6">Scanning</h3>
          <div class="flex justify-center">
            <div 
              class="chevron-scanning"
              @click="handleChevronClick('scanning')"
            >
              <ChevronUp class="w-12 h-12 text-purple-400" />
            </div>
          </div>
        </div>

        <!-- Glitch Chevron -->
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 text-center hover:border-pink-400/50 transition-all duration-300">
          <h3 class="text-pink-400 font-semibold mb-6">Glitch Effect</h3>
          <div class="flex justify-center">
            <div 
              class="chevron-glitch"
              @click="handleChevronClick('glitch')"
            >
              <ChevronLeft class="w-12 h-12 text-pink-400" />
            </div>
          </div>
        </div>

        <!-- Particle Chevron -->
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 text-center hover:border-yellow-400/50 transition-all duration-300">
          <h3 class="text-yellow-400 font-semibold mb-6">Particle Trail</h3>
          <div class="flex justify-center">
            <div 
              class="chevron-particle"
              @click="handleChevronClick('particle')"
            >
              <ChevronDown class="w-12 h-12 text-yellow-400" />
            </div>
          </div>
        </div>

        <!-- Matrix Chevron -->
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 text-center hover:border-green-400/50 transition-all duration-300">
          <h3 class="text-green-400 font-semibold mb-6">Matrix Style</h3>
          <div class="flex justify-center">
            <div 
              class="chevron-matrix"
              @click="handleChevronClick('matrix')"
            >
              <ChevronRight class="w-12 h-12 text-green-400" />
            </div>
          </div>
        </div>
      </div>

      <!-- Large Interactive Chevrons -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
        
        <!-- Mega Chevron 1 -->
        <div class="relative group">
          <div class="bg-slate-900/30 backdrop-blur-sm border border-slate-700/30 rounded-3xl p-12 text-center hover:border-cyan-400/50 transition-all duration-500">
            <h3 class="text-2xl font-bold text-cyan-400 mb-8">Quantum Chevron</h3>
            <div class="relative flex justify-center">
              <!-- Main Chevron -->
              <div 
                class="mega-chevron-quantum cursor-pointer"
                @click="handleMegaChevronClick('quantum')"
              >
                <ChevronDown class="w-24 h-24 text-cyan-400" />
                
                <!-- Orbital rings -->
                <div class="absolute inset-0 rounded-full border-2 border-cyan-400/30 animate-spin-slow"></div>
                <div class="absolute inset-2 rounded-full border border-blue-400/20 animate-spin-reverse"></div>
                
                <!-- Energy particles -->
                <div class="absolute -top-2 -left-2 w-2 h-2 bg-cyan-400 rounded-full animate-ping"></div>
                <div class="absolute -top-2 -right-2 w-1 h-1 bg-blue-400 rounded-full animate-pulse"></div>
                <div class="absolute -bottom-2 -left-2 w-1.5 h-1.5 bg-purple-400 rounded-full animate-bounce"></div>
                <div class="absolute -bottom-2 -right-2 w-1 h-1 bg-cyan-300 rounded-full animate-ping"></div>
              </div>
            </div>
            
            <!-- Status indicators -->
            <div class="flex justify-center gap-2 mt-8">
              <div class="w-2 h-2 bg-emerald-400 rounded-full animate-pulse"></div>
              <div class="w-2 h-2 bg-blue-400 rounded-full animate-pulse" style="animation-delay: 0.5s"></div>
              <div class="w-2 h-2 bg-purple-400 rounded-full animate-pulse" style="animation-delay: 1s"></div>
            </div>
          </div>
        </div>

        <!-- Mega Chevron 2 -->
        <div class="relative group">
          <div class="bg-slate-900/30 backdrop-blur-sm border border-slate-700/30 rounded-3xl p-12 text-center hover:border-emerald-400/50 transition-all duration-500">
            <h3 class="text-2xl font-bold text-emerald-400 mb-8">Neural Chevron</h3>
            <div class="relative flex justify-center">
              <!-- Main Chevron -->
              <div 
                class="mega-chevron-neural cursor-pointer"
                @click="handleMegaChevronClick('neural')"
              >
                <ChevronUp class="w-24 h-24 text-emerald-400" />
                
                <!-- Neural network lines -->
                <div class="absolute inset-0">
                  <div class="absolute top-0 left-1/2 w-px h-6 bg-gradient-to-b from-emerald-400 to-transparent animate-pulse"></div>
                  <div class="absolute bottom-0 left-1/2 w-px h-6 bg-gradient-to-t from-emerald-400 to-transparent animate-pulse"></div>
                  <div class="absolute left-0 top-1/2 w-6 h-px bg-gradient-to-r from-emerald-400 to-transparent animate-pulse"></div>
                  <div class="absolute right-0 top-1/2 w-6 h-px bg-gradient-to-l from-emerald-400 to-transparent animate-pulse"></div>
                </div>
                
                <!-- Corner brackets -->
                <div class="absolute -top-4 -left-4 w-6 h-6 border-l-2 border-t-2 border-emerald-400/50"></div>
                <div class="absolute -top-4 -right-4 w-6 h-6 border-r-2 border-t-2 border-emerald-400/50"></div>
                <div class="absolute -bottom-4 -left-4 w-6 h-6 border-l-2 border-b-2 border-emerald-400/50"></div>
                <div class="absolute -bottom-4 -right-4 w-6 h-6 border-r-2 border-b-2 border-emerald-400/50"></div>
              </div>
            </div>
            
            <!-- Data stream -->
            <div class="flex justify-center gap-1 mt-8">
              <div class="w-1 h-4 bg-emerald-400/60 animate-pulse"></div>
              <div class="w-1 h-6 bg-emerald-400/80 animate-pulse" style="animation-delay: 0.2s"></div>
              <div class="w-1 h-3 bg-emerald-400/40 animate-pulse" style="animation-delay: 0.4s"></div>
              <div class="w-1 h-5 bg-emerald-400/70 animate-pulse" style="animation-delay: 0.6s"></div>
              <div class="w-1 h-2 bg-emerald-400/30 animate-pulse" style="animation-delay: 0.8s"></div>
            </div>
          </div>
        </div>
      </div>

      <!-- Interactive Controls -->
      <div class="mt-16 text-center">
        <div class="bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl p-8 max-w-2xl mx-auto">
          <h3 class="text-xl font-bold text-white mb-6">Chevron Controls</h3>
          
          <!-- Direction Controls -->
          <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
            <button
              v-for="direction in directions"
              :key="direction.name"
              @click="setActiveDirection(direction.name)"
              :class="`p-4 rounded-xl border transition-all duration-300 ${
                activeDirection === direction.name 
                  ? 'border-cyan-400 bg-cyan-400/10 text-cyan-400' 
                  : 'border-slate-600 text-slate-400 hover:border-slate-500'
              }`"
            >
              <component :is="direction.icon" class="w-6 h-6 mx-auto mb-2" />
              <div class="text-sm font-medium">{{ direction.label }}</div>
            </button>
          </div>

          <!-- Size Controls -->
          <div class="flex justify-center gap-4">
            <button
              v-for="size in sizes"
              :key="size.name"
              @click="setActiveSize(size.name)"
              :class="`px-6 py-2 rounded-lg border transition-all duration-300 ${
                activeSize === size.name 
                  ? 'border-emerald-400 bg-emerald-400/10 text-emerald-400' 
                  : 'border-slate-600 text-slate-400 hover:border-slate-500'
              }`"
            >
              {{ size.label }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ChevronDown, ChevronUp, ChevronLeft, ChevronRight } from 'lucide-vue-next'

// State
const activeDirection = ref('down')
const activeSize = ref('medium')

// Configuration
const directions = [
  { name: 'up', label: 'Up', icon: ChevronUp },
  { name: 'down', label: 'Down', icon: ChevronDown },
  { name: 'left', label: 'Left', icon: ChevronLeft },
  { name: 'right', label: 'Right', icon: ChevronRight }
]

const sizes = [
  { name: 'small', label: 'Small' },
  { name: 'medium', label: 'Medium' },
  { name: 'large', label: 'Large' },
  { name: 'xl', label: 'Extra Large' }
]

// Methods
const handleChevronClick = (type) => {
  console.log(`${type} chevron activated!`)
  // Add haptic feedback simulation
  if (navigator.vibrate) {
    navigator.vibrate(50)
  }
}

const handleMegaChevronClick = (type) => {
  console.log(`Mega ${type} chevron activated!`)
  // Add stronger haptic feedback
  if (navigator.vibrate) {
    navigator.vibrate([100, 50, 100])
  }
}

const setActiveDirection = (direction) => {
  activeDirection.value = direction
  console.log(`Direction set to: ${direction}`)
}

const setActiveSize = (size) => {
  activeSize.value = size
  console.log(`Size set to: ${size}`)
}
</script>

<style scoped>
/* Basic Animated Chevron */
.chevron-basic {
  position: relative;
  padding: 1rem;
  border-radius: 50%;
  background: rgba(6, 182, 212, 0.1);
  border: 2px solid rgba(6, 182, 212, 0.3);
  cursor: pointer;
  transition: all 0.3s ease;
}

.chevron-basic:hover {
  transform: scale(1.1);
  background: rgba(6, 182, 212, 0.2);
  border-color: rgba(6, 182, 212, 0.6);
  box-shadow: 0 0 30px rgba(6, 182, 212, 0.4);
}

.chevron-basic:active {
  transform: scale(0.95);
}

/* Holographic Chevron */
.chevron-holographic {
  position: relative;
  padding: 1rem;
  border-radius: 50%;
  background: linear-gradient(45deg, rgba(16, 185, 129, 0.1), rgba(6, 182, 212, 0.1));
  border: 2px solid transparent;
  background-clip: padding-box;
  cursor: pointer;
  transition: all 0.3s ease;
}

.chevron-holographic::before {
  content: '';
  position: absolute;
  inset: -2px;
  border-radius: 50%;
  background: linear-gradient(45deg, #10b981, #06b6d4, #8b5cf6);
  z-index: -1;
  animation: rotate 3s linear infinite;
}

.chevron-holographic:hover {
  transform: scale(1.1) rotateY(15deg);
  box-shadow: 0 0 40px rgba(16, 185, 129, 0.5);
}

/* Scanning Chevron */
.chevron-scanning {
  position: relative;
  padding: 1rem;
  border-radius: 50%;
  background: rgba(139, 92, 246, 0.1);
  border: 2px solid rgba(139, 92, 246, 0.3);
  cursor: pointer;
  overflow: hidden;
}

.chevron-scanning::after {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(45deg, transparent, rgba(139, 92, 246, 0.3), transparent);
  animation: scan 2s linear infinite;
}

.chevron-scanning:hover {
  transform: scale(1.1);
  box-shadow: 0 0 35px rgba(139, 92, 246, 0.6);
}

/* Glitch Chevron */
.chevron-glitch {
  position: relative;
  padding: 1rem;
  border-radius: 50%;
  background: rgba(236, 72, 153, 0.1);
  border: 2px solid rgba(236, 72, 153, 0.3);
  cursor: pointer;
}

.chevron-glitch:hover {
  animation: glitch 0.3s ease-in-out;
  box-shadow: 0 0 30px rgba(236, 72, 153, 0.5);
}

/* Particle Chevron */
.chevron-particle {
  position: relative;
  padding: 1rem;
  border-radius: 50%;
  background: rgba(251, 191, 36, 0.1);
  border: 2px solid rgba(251, 191, 36, 0.3);
  cursor: pointer;
}

.chevron-particle::before,
.chevron-particle::after {
  content: '';
  position: absolute;
  width: 4px;
  height: 4px;
  background: #fbbf24;
  border-radius: 50%;
  animation: particle-float 2s ease-in-out infinite;
}

.chevron-particle::before {
  top: 10%;
  left: 20%;
  animation-delay: 0s;
}

.chevron-particle::after {
  bottom: 10%;
  right: 20%;
  animation-delay: 1s;
}

.chevron-particle:hover {
  transform: scale(1.1);
  box-shadow: 0 0 40px rgba(251, 191, 36, 0.4);
}

/* Matrix Chevron */
.chevron-matrix {
  position: relative;
  padding: 1rem;
  border-radius: 50%;
  background: rgba(34, 197, 94, 0.1);
  border: 2px solid rgba(34, 197, 94, 0.3);
  cursor: pointer;
  font-family: 'Courier New', monospace;
}

.chevron-matrix::before {
  content: '01010101';
  position: absolute;
  top: -20px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 8px;
  color: rgba(34, 197, 94, 0.6);
  animation: matrix-rain 2s linear infinite;
}

.chevron-matrix:hover {
  transform: scale(1.1);
  box-shadow: 0 0 35px rgba(34, 197, 94, 0.5);
}

/* Mega Chevrons */
.mega-chevron-quantum {
  position: relative;
  padding: 2rem;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(6, 182, 212, 0.2), rgba(6, 182, 212, 0.05));
  border: 3px solid rgba(6, 182, 212, 0.4);
  transition: all 0.5s ease;
}

.mega-chevron-quantum:hover {
  transform: scale(1.05) rotateZ(5deg);
  box-shadow: 
    0 0 50px rgba(6, 182, 212, 0.6),
    inset 0 0 30px rgba(6, 182, 212, 0.2);
}

.mega-chevron-neural {
  position: relative;
  padding: 2rem;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(16, 185, 129, 0.2), rgba(16, 185, 129, 0.05));
  border: 3px solid rgba(16, 185, 129, 0.4);
  transition: all 0.5s ease;
}

.mega-chevron-neural:hover {
  transform: scale(1.05) rotateZ(-5deg);
  box-shadow: 
    0 0 50px rgba(16, 185, 129, 0.6),
    inset 0 0 30px rgba(16, 185, 129, 0.2);
}

/* Animations */
@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes scan {
  0% { transform: translate(-50%, -50%) rotate(0deg); }
  100% { transform: translate(-50%, -50%) rotate(360deg); }
}

@keyframes glitch {
  0%, 100% { transform: translate(0); }
  10% { transform: translate(-2px, 2px); }
  20% { transform: translate(2px, -2px); }
  30% { transform: translate(-2px, -2px); }
  40% { transform: translate(2px, 2px); }
  50% { transform: translate(-2px, 2px); }
  60% { transform: translate(2px, -2px); }
  70% { transform: translate(-2px, -2px); }
  80% { transform: translate(2px, 2px); }
  90% { transform: translate(-2px, 2px); }
}

@keyframes particle-float {
  0%, 100% { 
    transform: translateY(0) scale(1); 
    opacity: 1; 
  }
  50% { 
    transform: translateY(-20px) scale(1.2); 
    opacity: 0.7; 
  }
}

@keyframes matrix-rain {
  0% { 
    transform: translateX(-50%) translateY(0); 
    opacity: 1; 
  }
  100% { 
    transform: translateX(-50%) translateY(100px); 
    opacity: 0; 
  }
}

@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes spin-reverse {
  from { transform: rotate(360deg); }
  to { transform: rotate(0deg); }
}

.animate-spin-slow {
  animation: spin-slow 8s linear infinite;
}

.animate-spin-reverse {
  animation: spin-reverse 6s linear infinite;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .mega-chevron-quantum,
  .mega-chevron-neural {
    padding: 1.5rem;
  }
  
  .mega-chevron-quantum svg,
  .mega-chevron-neural svg {
    width: 4rem;
    height: 4rem;
  }
}
</style>