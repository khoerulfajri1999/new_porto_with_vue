<template>
  <div class="min-h-screen bg-gradient-to-br from-[#030415] via-[#1E0B38] to-[#030415] flex items-center justify-center relative overflow-hidden">
    
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
      <!-- Hover Detection Area (larger than button for better UX) -->
      <div 
        class="chevron-container group cursor-pointer"
        @click="handleClick"
        @mouseenter="handleHover"
      >
        <!-- Outer Glow Ring (appears on hover) -->
        <div class="outer-glow-ring"></div>
        
        <!-- Middle Ring (rotates on hover) -->
        <div class="middle-ring"></div>
        
        <!-- Inner Ring (pulses) -->
        <div class="inner-ring"></div>
        
        <!-- Main Button -->
        <div class="main-button">
          <!-- Background Gradient -->
          <div class="button-gradient"></div>
          
          <!-- Scanning Line -->
          <div class="scanning-line"></div>
          
          <!-- Chevron Icon -->
          <ChevronDown class="chevron-icon" />
          
          <!-- Corner Brackets -->
          <div class="corner-bracket top-left"></div>
          <div class="corner-bracket top-right"></div>
          <div class="corner-bracket bottom-left"></div>
          <div class="corner-bracket bottom-right"></div>
          
          <!-- Energy Particles -->
          <div class="energy-particle particle-1"></div>
          <div class="energy-particle particle-2"></div>
          <div class="energy-particle particle-3"></div>
          <div class="energy-particle particle-4"></div>
        </div>
        
        <!-- Ripple Effect (on click) -->
        <div class="ripple-effect" ref="rippleRef"></div>
        
        <!-- Status Indicator -->
        <div class="status-indicator">
          <div class="status-dot"></div>
          <span class="status-text">READY</span>
        </div>
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
/* Main Container */
.chevron-container {
  position: relative;
  width: 120px;
  height: 120px;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: float 4s ease-in-out infinite;
}

/* Floating Animation */
@keyframes float {
  0%, 100% { 
    transform: translateY(0px) rotate(0deg); 
  }
  50% { 
    transform: translateY(-15px) rotate(1deg); 
  }
}

/* Outer Glow Ring */
.outer-glow-ring {
  position: absolute;
  width: 140px;
  height: 140px;
  border: 2px solid transparent;
  border-radius: 50%;
  background: linear-gradient(45deg, #06b6d4, #3b82f6, #8b5cf6, #06b6d4);
  background-size: 400% 400%;
  opacity: 0;
  transform: scale(0.8);
  transition: all 0.5s ease;
  animation: gradient-shift 3s ease infinite;
}

.chevron-container:hover .outer-glow-ring {
  opacity: 0.6;
  transform: scale(1);
  box-shadow: 0 0 50px rgba(6, 182, 212, 0.4);
}

/* Middle Ring */
.middle-ring {
  position: absolute;
  width: 100px;
  height: 100px;
  border: 1px solid rgba(6, 182, 212, 0.3);
  border-radius: 50%;
  transform: rotate(0deg);
  transition: all 0.8s ease;
}

.chevron-container:hover .middle-ring {
  transform: rotate(180deg);
  border-color: rgba(6, 182, 212, 0.8);
  box-shadow: 0 0 30px rgba(6, 182, 212, 0.3);
}

/* Inner Ring */
.inner-ring {
  position: absolute;
  width: 80px;
  height: 80px;
  border: 1px solid rgba(139, 92, 246, 0.2);
  border-radius: 50%;
  animation: pulse-ring 2s ease-in-out infinite;
}

.chevron-container:hover .inner-ring {
  border-color: rgba(139, 92, 246, 0.6);
  animation-duration: 1s;
}

/* Main Button */
.main-button {
  position: relative;
  width: 70px;
  height: 70px;
  background: rgba(15, 23, 42, 0.8);
  border: 2px solid rgba(6, 182, 212, 0.4);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
  overflow: hidden;
  z-index: 10;
}

.chevron-container:hover .main-button {
  background: rgba(6, 182, 212, 0.1);
  border-color: rgba(6, 182, 212, 0.8);
  box-shadow: 
    0 0 40px rgba(6, 182, 212, 0.4),
    inset 0 0 20px rgba(6, 182, 212, 0.1);
  transform: scale(1.05);
}

.chevron-container:active .main-button {
  transform: scale(0.95);
}

/* Button Gradient Background */
.button-gradient {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at center, rgba(6, 182, 212, 0.1), transparent);
  border-radius: 50%;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.chevron-container:hover .button-gradient {
  opacity: 1;
}

/* Scanning Line */
.scanning-line {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #06b6d4, transparent);
  border-radius: 1px;
  opacity: 0;
  transform: translateY(-100%);
  animation: scan-line 2s linear infinite;
}

.chevron-container:hover .scanning-line {
  opacity: 1;
}

/* Chevron Icon */
.chevron-icon {
  width: 32px;
  height: 32px;
  color: #06b6d4;
  transition: all 0.3s ease;
  z-index: 2;
  filter: drop-shadow(0 0 10px rgba(6, 182, 212, 0.5));
}

.chevron-container:hover .chevron-icon {
  color: #ffffff;
  transform: translateY(3px) scale(1.1);
  filter: drop-shadow(0 0 20px rgba(6, 182, 212, 0.8));
}

/* Corner Brackets */
.corner-bracket {
  position: absolute;
  width: 12px;
  height: 12px;
  border: 2px solid rgba(6, 182, 212, 0.4);
  opacity: 0;
  transition: all 0.3s ease;
}

.corner-bracket.top-left {
  top: 8px;
  left: 8px;
  border-right: none;
  border-bottom: none;
}

.corner-bracket.top-right {
  top: 8px;
  right: 8px;
  border-left: none;
  border-bottom: none;
}

.corner-bracket.bottom-left {
  bottom: 8px;
  left: 8px;
  border-right: none;
  border-top: none;
}

.corner-bracket.bottom-right {
  bottom: 8px;
  right: 8px;
  border-left: none;
  border-top: none;
}

.chevron-container:hover .corner-bracket {
  opacity: 1;
  border-color: rgba(6, 182, 212, 0.8);
}

/* Energy Particles */
.energy-particle {
  position: absolute;
  width: 3px;
  height: 3px;
  background: #06b6d4;
  border-radius: 50%;
  opacity: 0;
  transition: all 0.3s ease;
}

.particle-1 {
  top: 15px;
  left: 15px;
  animation: particle-float-1 3s ease-in-out infinite;
}

.particle-2 {
  top: 15px;
  right: 15px;
  animation: particle-float-2 3s ease-in-out infinite 0.5s;
}

.particle-3 {
  bottom: 15px;
  left: 15px;
  animation: particle-float-3 3s ease-in-out infinite 1s;
}

.particle-4 {
  bottom: 15px;
  right: 15px;
  animation: particle-float-4 3s ease-in-out infinite 1.5s;
}

.chevron-container:hover .energy-particle {
  opacity: 1;
  box-shadow: 0 0 10px #06b6d4;
}

/* Ripple Effect */
.ripple-effect {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 2px solid rgba(6, 182, 212, 0.6);
  border-radius: 50%;
  opacity: 0;
  transform: scale(0);
  pointer-events: none;
}

.animate-ripple {
  animation: ripple 0.6s ease-out;
}

/* Status Indicator */
.status-indicator {
  position: absolute;
  bottom: -40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 6px 12px;
  background: rgba(15, 23, 42, 0.8);
  border: 1px solid rgba(6, 182, 212, 0.3);
  border-radius: 20px;
  backdrop-filter: blur(10px);
  opacity: 0;
  transition: all 0.3s ease;
}

.chevron-container:hover .status-indicator {
  opacity: 1;
  transform: translateX(-50%) translateY(-5px);
}

.status-dot {
  width: 6px;
  height: 6px;
  background: #10b981;
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
}

.status-text {
  font-size: 10px;
  color: #06b6d4;
  font-weight: 600;
  letter-spacing: 1px;
}

/* Animations */
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

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

/* Responsive */
@media (max-width: 768px) {
  .chevron-container {
    width: 100px;
    height: 100px;
  }
  
  .main-button {
    width: 60px;
    height: 60px;
  }
  
  .chevron-icon {
    width: 28px;
    height: 28px;
  }
}
</style>