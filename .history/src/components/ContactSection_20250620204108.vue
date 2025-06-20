<template>
  <div :class="{ 'dark': isDark }" class="min-h-screen transition-colors duration-500">
    <!-- Robot Send Message Section -->
    <section ref="robotMessageSection" id="contact" class="relative py-20 bg-gradient-to-tl from-[#030415] via-[#1E0B38] to-[#030415] overflow-hidden">
      <!-- Animated Background Grid -->
      <div class="absolute inset-0 bg-[linear-gradient(rgba(120,119,198,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(120,119,198,0.1)_1px,transparent_1px)] bg-[size:50px_50px] animate-pulse"></div>
    

      <!-- Floating Circuit Elements -->
      <div class="absolute inset-0 overflow-hidden pointer-events-none">
        <div ref="circuit1" class="absolute top-20 left-10 w-32 h-32 opacity-30">
          <svg viewBox="0 0 100 100" class="w-full h-full text-cyan-400">
            <circle cx="20" cy="20" r="3" fill="currentColor" />
            <circle cx="80" cy="20" r="3" fill="currentColor" />
            <circle cx="50" cy="50" r="5" fill="currentColor" />
            <circle cx="20" cy="80" r="3" fill="currentColor" />
            <circle cx="80" cy="80" r="3" fill="currentColor" />
            <path d="M20 20 L50 50 L80 20 M20 80 L50 50 L80 80" stroke="currentColor" stroke-width="1" fill="none" />
          </svg>
        </div>
        <div ref="circuit2" class="absolute top-40 right-20 w-24 h-24 opacity-40">
          <svg viewBox="0 0 100 100" class="w-full h-full text-green-400">
            <rect x="10" y="10" width="80" height="80" fill="none" stroke="currentColor" stroke-width="2" />
            <circle cx="30" cy="30" r="4" fill="currentColor" />
            <circle cx="70" cy="30" r="4" fill="currentColor" />
            <circle cx="50" cy="70" r="6" fill="currentColor" />
            <path d="M30 30 L70 30 L50 70 Z" stroke="currentColor" stroke-width="1" fill="none" />
          </svg>
        </div>
        <div ref="circuit3" class="absolute bottom-32 left-1/4 w-28 h-28 opacity-25">
          <svg viewBox="0 0 100 100" class="w-full h-full text-blue-400">
            <polygon points="50,10 90,50 50,90 10,50" fill="none" stroke="currentColor" stroke-width="2" />
            <circle cx="50" cy="50" r="8" fill="currentColor" />
            <circle cx="50" cy="25" r="3" fill="currentColor" />
            <circle cx="75" cy="50" r="3" fill="currentColor" />
            <circle cx="50" cy="75" r="3" fill="currentColor" />
            <circle cx="25" cy="50" r="3" fill="currentColor" />
          </svg>
        </div>
      </div>

      <!-- Glowing Orbs -->
      <div ref="glowOrb1" class="absolute top-1/4 left-1/6 w-4 h-4 bg-cyan-400 rounded-full blur-sm opacity-60"></div>
      <div ref="glowOrb2" class="absolute top-3/4 right-1/4 w-6 h-6 bg-green-400 rounded-full blur-sm opacity-40"></div>
      <div ref="glowOrb3" class="absolute bottom-1/3 left-3/4 w-3 h-3 bg-blue-400 rounded-full blur-sm opacity-70"></div>

      <div class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Section Header with Robot Theme -->
        <div class="text-center mb-16">
          <!-- Robot Head Icon -->
          <div ref="robotHead" class="mx-auto mb-8 w-24 h-24 relative">
            <div class="w-full h-full bg-gradient-to-br from-cyan-400 to-blue-500 rounded-lg relative overflow-hidden shadow-2xl">
              <!-- Robot Face -->
              <div class="absolute inset-2 bg-gray-900 rounded-md flex items-center justify-center">
                <!-- Eyes -->
                <div class="flex space-x-3">
                  <div ref="robotEye1" class="w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"></div>
                  <div ref="robotEye2" class="w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"></div>
                </div>
                <!-- Mouth -->
                <div ref="robotMouth" class="absolute bottom-2 left-1/2 transform -translate-x-1/2 w-4 h-1 bg-cyan-400 rounded-full opacity-60"></div>
              </div>
              <!-- Antenna -->
              <div ref="robotAntenna" class="absolute -top-2 left-1/2 transform -translate-x-1/2 w-1 h-4 bg-cyan-400 rounded-full"></div>
              <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"></div>
            </div>
          </div>

          <h2 ref="sectionTitle" class="text-5xl sm:text-6xl font-bold mb-6">
            <span class="bg-gradient-to-r from-cyan-400 via-blue-400 to-green-400 bg-clip-text text-transparent">
              SEND MESSAGE
            </span>
          </h2>
          <p ref="sectionSubtitle" class="text-xl text-gray-300 mb-4">
            <span class="text-cyan-400 font-mono">[SYSTEM READY]</span> Let's work
            together!
          </p>
          <div ref="statusIndicator" class="flex items-center justify-center space-x-2">
            <div class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></div>
            <span class="text-green-400 font-mono text-sm">CONNECTION_ACTIVE</span>
          </div>
        </div>

        <!-- Robot Message Interface -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
          <!-- Left Side - Robot Illustration -->
          <div ref="robotContainer" class="relative">
            <div class="relative">
              <!-- Main Robot Body -->
              <div ref="robotBody" class="w-80 h-96 mx-auto relative">
                <!-- Robot Torso -->
                <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-48 h-64 bg-gradient-to-b from-gray-700 to-gray-800 rounded-t-3xl border-2 border-cyan-400/30 shadow-2xl">
                  <!-- Chest Panel -->
                  <div class="absolute top-8 left-1/2 transform -translate-x-1/2 w-32 h-20 bg-gray-900 rounded-lg border border-cyan-400/50">
                    <!-- Status Lights -->
                    <div class="flex justify-center space-x-2 mt-3">
                      <div ref="statusLight1" class="w-2 h-2 bg-green-400 rounded-full"></div>
                      <div ref="statusLight2" class="w-2 h-2 bg-blue-400 rounded-full"></div>
                      <div ref="statusLight3" class="w-2 h-2 bg-cyan-400 rounded-full"></div>
                    </div>
                    <!-- Display Screen -->
                    <div class="mt-2 mx-2 h-8 bg-black rounded border border-cyan-400/30 flex items-center justify-center">
                      <span ref="robotDisplay" class="text-cyan-400 font-mono text-xs">READY_TO_RECEIVE</span>
                    </div>
                  </div>
                  
                  <!-- Arms -->
                  <div ref="robotArmLeft" class="absolute top-16 -left-8 w-6 h-32 bg-gradient-to-b from-gray-600 to-gray-700 rounded-full border border-cyan-400/30"></div>
                  <div ref="robotArmRight" class="absolute top-16 -right-8 w-6 h-32 bg-gradient-to-b from-gray-600 to-gray-700 rounded-full border border-cyan-400/30"></div>
                  
                  <!-- Hands -->
                  <div class="absolute top-44 -left-10 w-8 h-8 bg-gray-600 rounded-full border border-cyan-400/30"></div>
                  <div class="absolute top-44 -right-10 w-8 h-8 bg-gray-600 rounded-full border border-cyan-400/30"></div>
                </div>

                <!-- Robot Head -->
                <div ref="robotMainHead" class="absolute top-0 left-1/2 transform -translate-x-1/2 w-32 h-32 bg-gradient-to-br from-gray-600 to-gray-800 rounded-2xl border-2 border-cyan-400/50 shadow-2xl">
                  <!-- Face Screen -->
                  <div class="absolute inset-4 bg-black rounded-lg border border-cyan-400/30 flex flex-col items-center justify-center">
                    <!-- Main Eyes -->
                    <div class="flex space-x-4 mb-2">
                      <div ref="mainEye1" class="w-4 h-4 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"></div>
                      <div ref="mainEye2" class="w-4 h-4 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"></div>
                    </div>
                    <!-- Expression Line -->
                    <div ref="expressionLine" class="w-8 h-0.5 bg-cyan-400 rounded-full"></div>
                  </div>
                  
                  <!-- Head Antenna -->
                  <div class="absolute -top-4 left-1/2 transform -translate-x-1/2 w-2 h-6 bg-cyan-400 rounded-full"></div>
                  <div ref="antennaLight" class="absolute -top-6 left-1/2 transform -translate-x-1/2 w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50"></div>
                </div>

                <!-- Floating Data Particles -->
                <div ref="dataParticle1" class="absolute top-20 -left-12 w-1 h-1 bg-cyan-400 rounded-full opacity-60"></div>
                <div ref="dataParticle2" class="absolute top-32 -right-8 w-1 h-1 bg-green-400 rounded-full opacity-60"></div>
                <div ref="dataParticle3" class="absolute top-48 left-2 w-1 h-1 bg-blue-400 rounded-full opacity-60"></div>
              </div>

              <!-- Holographic Effect -->
              <div ref="holographicRing" class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-64 h-4 bg-gradient-to-r from-transparent via-cyan-400/20 to-transparent rounded-full blur-sm"></div>
            </div>
          </div>

          <!-- Right Side - Message Form -->
          <div ref="messageForm">
            <div class="bg-gray-900/80 backdrop-blur-md rounded-2xl p-8 border border-cyan-400/30 shadow-2xl relative overflow-hidden">
              <!-- Form Header -->
              <div class="flex items-center justify-between mb-6">
                <div class="flex items-center space-x-3">
                  <div class="w-3 h-3 bg-green-400 rounded-full animate-pulse"></div>
                  <span class="text-cyan-400 font-mono text-sm">COMMUNICATION_INTERFACE</span>
                </div>
                <div class="text-gray-400 font-mono text-xs">v1.0.0</div>
              </div>

              <!-- Scanning Line Effect -->
              <div ref="scanLine" class="absolute left-0 w-full h-0.5 bg-gradient-to-r from-transparent via-cyan-400 to-transparent opacity-60"></div>

              <form @submit.prevent="submitMessage" class="space-y-6 ">
                <!-- Name Input -->
                <div ref="nameField">
                  <label class="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                    <span class="text-gray-500">[01]</span> NAME
                  </label>
                  <div class="relative">
                    <input
                      v-model="messageForm.name"
                      type="text"
                      required
                      class="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 font-mono"
                      placeholder="Enter your name..."
                    >
                    <div class="absolute right-3 top-1/2 transform -translate-y-1/2 w-2 h-2 bg-cyan-400 rounded-full opacity-60"></div>
                  </div>
                </div>

                <!-- Email Input -->
                <div ref="emailField">
                  <label class="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                    <span class="text-gray-500">[02]</span> EMAIL
                  </label>
                  <div class="relative">
                    <input
                      v-model="messageForm.email"
                      type="email"
                      required
                      class="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 font-mono"
                      placeholder="Enter your email..."
                    >
                    <div class="absolute right-3 top-1/2 transform -translate-y-1/2 w-2 h-2 bg-green-400 rounded-full opacity-60"></div>
                  </div>
                </div>

                <!-- Message Input -->
                <div ref="messageField">
                  <label class="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                    <span class="text-gray-500">[03]</span> MESSAGE
                  </label>
                  <div class="relative">
                    <textarea
                      v-model="messageForm.message"
                      required
                      rows="5"
                      class="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 resize-none font-mono"
                      placeholder="Enter your message..."
                    ></textarea>
                    <div class="absolute right-3 bottom-3 w-2 h-2 bg-blue-400 rounded-full opacity-60"></div>
                  </div>
                </div>

                <!-- Submit Button -->
                <div ref="submitButton">
                  <button
                    type="submit"
                    :disabled="isTransmitting"
                    class="w-full bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 disabled:opacity-50 text-white font-bold py-4 px-8 rounded-lg text-lg transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-cyan-400/25 font-mono uppercase tracking-wider relative overflow-hidden"
                  >
                    <span v-if="!isTransmitting" class="flex items-center justify-center">
                      SEND MESSAGE
                    </span>
                    <span v-else class="flex items-center justify-center">
                      <div class="w-5 h-5 mr-2 border-2 border-white border-t-transparent rounded-full animate-spin"></div>
                      TRANSMITTING...
                    </span>
                    
                    <!-- Button Glow Effect -->
                    <div ref="buttonGlow" class="absolute inset-0 bg-gradient-to-r from-cyan-400/20 to-blue-400/20 rounded-lg"></div>
                  </button>
                </div>
              </form>

              <!-- Status Bar -->
              <div ref="statusBar" class="mt-6 flex items-center justify-between text-xs font-mono">
                <div class="flex items-center space-x-2">
                  <div class="w-1 h-1 bg-green-400 rounded-full animate-pulse"></div>
                  <span class="text-green-400">SYSTEM_ONLINE</span>
                </div>
                <div class="text-gray-500">ENCRYPTION: AES-256</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import emailjs from '@emailjs/browser'

// Register GSAP plugins
gsap.registerPlugin(ScrollTrigger)

// Reactive data
const isDark = ref(true)
const isTransmitting = ref(false)
const success = ref(null)

// Form data
const messageForm = ref({
  name: '',
  email: '',
  message: ''
})

// Template refs
const robotMessageSection = ref(null)
const gridPattern = ref(null)
const circuit1 = ref(null)
const circuit2 = ref(null)
const circuit3 = ref(null)
const glowOrb1 = ref(null)
const glowOrb2 = ref(null)
const glowOrb3 = ref(null)
const robotHead = ref(null)
const robotEye1 = ref(null)
const robotEye2 = ref(null)
const robotMouth = ref(null)
const robotAntenna = ref(null)
const sectionTitle = ref(null)
const sectionSubtitle = ref(null)
const statusIndicator = ref(null)
const robotContainer = ref(null)
const robotBody = ref(null)
const robotMainHead = ref(null)
const robotArmLeft = ref(null)
const robotArmRight = ref(null)
const mainEye1 = ref(null)
const mainEye2 = ref(null)
const expressionLine = ref(null)
const antennaLight = ref(null)
const statusLight1 = ref(null)
const statusLight2 = ref(null)
const statusLight3 = ref(null)
const robotDisplay = ref(null)
const dataParticle1 = ref(null)
const dataParticle2 = ref(null)
const dataParticle3 = ref(null)
const holographicRing = ref(null)
const scanLine = ref(null)
const nameField = ref(null)
const emailField = ref(null)
const messageField = ref(null)
const submitButton = ref(null)
const statusBar = ref(null)
const buttonGlow = ref(null)

// Methods
const submitMessage = async () => {
  isTransmitting.value = true
  
  // Animate robot response
  gsap.to(robotDisplay.value, {
    duration: 0.5,
    scale: 1.1,
    ease: "power2.out"
  })
  
  // Change robot expression
  gsap.to([mainEye1.value, mainEye2.value], {
    duration: 0.3,
    scaleY: 0.3,
    repeat: 3,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  // Simulate transmission
  await new Promise(resolve => setTimeout(resolve, 3000))
  
  // Reset form
  messageForm.value = {
    name: '',
    email: '',
    message: ''
  }
  
  isTransmitting.value = false
  
  // Success animation
  gsap.to(buttonGlow.value, {
    duration: 0.5,
    opacity: 1,
    scale: 1.2,
    ease: "power2.out",
    onComplete: () => {
      gsap.to(buttonGlow.value, {
        duration: 0.5,
        opacity: 0,
        scale: 1,
        ease: "power2.in"
      })
    }
  })
  
  alert('Message transmitted successfully!')
}

// GSAP Animations
const initRobotAnimations = () => {
  // Create main timeline
  const mainTl = gsap.timeline()
  
  // Background animations
  gsap.to(gridPattern.value, {
    duration: 20,
    backgroundPosition: "100px 100px",
    repeat: -1,
    ease: "none"
  })
  
  // Circuit animations
  gsap.to(circuit1.value, {
    duration: 8,
    rotation: 360,
    repeat: -1,
    ease: "none"
  })
  
  gsap.to(circuit2.value, {
    duration: 6,
    rotation: -360,
    repeat: -1,
    ease: "none"
  })
  
  gsap.to(circuit3.value, {
    duration: 10,
    rotation: 360,
    repeat: -1,
    ease: "none"
  })
  
  // Glowing orbs
  gsap.to([glowOrb1.value, glowOrb2.value, glowOrb3.value], {
    duration: 2,
    scale: 1.5,
    opacity: 0.8,
    repeat: -1,
    yoyo: true,
    stagger: 0.3,
    ease: "power2.inOut"
  })
  
  // Robot eye blinking
  gsap.to([robotEye1.value, robotEye2.value, mainEye1.value, mainEye2.value], {
    duration: 0.1,
    scaleY: 0.1,
    repeat: -1,
    repeatDelay: 3,
    ease: "power2.inOut"
  })
  
  // Robot antenna pulsing
  gsap.to([robotAntenna.value, antennaLight.value], {
    duration: 1.5,
    scale: 1.2,
    opacity: 0.8,
    repeat: -1,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  // Status lights sequence
  gsap.to([statusLight1.value, statusLight2.value, statusLight3.value], {
    duration: 0.5,
    scale: 1.3,
    repeat: -1,
    stagger: 0.2,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  // Robot arms subtle movement
  gsap.to(robotArmLeft.value, {
    duration: 4,
    rotation: 5,
    repeat: -1,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  gsap.to(robotArmRight.value, {
    duration: 4,
    rotation: -5,
    repeat: -1,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  // Data particles floating
  gsap.to([dataParticle1.value, dataParticle2.value, dataParticle3.value], {
    duration: 3,
    y: -20,
    opacity: 1,
    repeat: -1,
    stagger: 0.5,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  // Holographic ring pulsing
  gsap.to(holographicRing.value, {
    duration: 2,
    scaleX: 1.2,
    opacity: 0.4,
    repeat: -1,
    yoyo: true,
    ease: "power2.inOut"
  })
  
  // Scanning line animation
  gsap.to(scanLine.value, {
    duration: 3,
    top: "100%",
    repeat: -1,
    ease: "power2.inOut"
  })
}

const initScrollTriggerAnimations = () => {
  // Main entrance animation - will retrigger every time
  ScrollTrigger.create({
    trigger: robotMessageSection.value,
    start: "top 80%",
    end: "bottom 20%",
    toggleActions: "play none none reverse",
    animation: gsap.timeline()
      .from(sectionTitle.value, {
        duration: 1,
        y: 100,
        opacity: 0,
        ease: "power3.out"
      })
      .from(sectionSubtitle.value, {
        duration: 0.8,
        y: 50,
        opacity: 0,
        ease: "power3.out"
      }, "-=0.6")
      .from(statusIndicator.value, {
        duration: 0.6,
        scale: 0,
        opacity: 0,
        ease: "back.out(1.7)"
      }, "-=0.4")
      .from(robotContainer.value, {
        duration: 1.2,
        x: -100,
        opacity: 0,
        ease: "power3.out"
      }, "-=0.8")
      .from(messageForm.value, {
        duration: 1.2,
        x: 100,
        opacity: 0,
        ease: "power3.out"
      }, "-=1")
      .from([nameField.value, emailField.value, messageField.value, submitButton.value, statusBar.value], {
        duration: 0.6,
        y: 30,
        opacity: 0,
        stagger: 0.1,
        ease: "power3.out"
      }, "-=0.6")
  })
  
  // Robot head entrance animation
  ScrollTrigger.create({
    trigger: robotHead.value,
    start: "top 90%",
    toggleActions: "play none none reverse",
    animation: gsap.timeline()
      .from(robotHead.value, {
        duration: 1,
        scale: 0,
        rotation: 180,
        ease: "back.out(1.7)"
      })
      .from([robotEye1.value, robotEye2.value], {
        duration: 0.5,
        scale: 0,
        stagger: 0.1,
        ease: "back.out(1.7)"
      }, "-=0.5")
  })
  
  // Robot body parts animation
  ScrollTrigger.create({
    trigger: robotBody.value,
    start: "top 85%",
    toggleActions: "play none none reverse",
    animation: gsap.timeline()
      .from(robotMainHead.value, {
        duration: 0.8,
        y: -50,
        opacity: 0,
        ease: "bounce.out"
      })
      .from(robotBody.value, {
        duration: 1,
        scale: 0.8,
        opacity: 0,
        ease: "power3.out"
      }, "-=0.6")
      .from([robotArmLeft.value, robotArmRight.value], {
        duration: 0.6,
        scaleY: 0,
        stagger: 0.1,
        ease: "power3.out"
      }, "-=0.4")
  })
}

// Lifecycle hooks
onMounted(() => {
  // Initialize animations
  initRobotAnimations()
  initScrollTriggerAnimations()
})

onUnmounted(() => {
  // Clean up ScrollTrigger instances
  ScrollTrigger.getAll().forEach(trigger => trigger.kill())
})
</script>

<style scoped>
/* Custom robot-themed styles */
.robot-glow {
  box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
}

/* Holographic effect */
.holographic {
  background: linear-gradient(45deg, transparent 30%, rgba(0, 255, 255, 0.1) 50%, transparent 70%);
  background-size: 200% 200%;
  animation: holographic-shift 3s ease-in-out infinite;
}

@keyframes holographic-shift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}

/* Circuit pattern animation */
.circuit-flow {
  background-image: 
    radial-gradient(circle at 20% 20%, rgba(0, 255, 255, 0.3) 2px, transparent 2px),
    radial-gradient(circle at 80% 80%, rgba(0, 255, 255, 0.3) 2px, transparent 2px);
  background-size: 50px 50px;
  animation: circuit-pulse 4s ease-in-out infinite;
}

@keyframes circuit-pulse {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 0.7; }
}

/* Glitch effect for robot display */
.glitch {
  animation: glitch 2s infinite;
}

@keyframes glitch {
  0%, 90%, 100% { transform: translate(0); }
  10% { transform: translate(-1px, -1px); }
  20% { transform: translate(1px, 1px); }
  30% { transform: translate(-1px, 1px); }
  40% { transform: translate(1px, -1px); }
  50% { transform: translate(-1px, -1px); }
  60% { transform: translate(1px, 1px); }
  70% { transform: translate(-1px, 1px); }
  80% { transform: translate(1px, -1px); }
}

/* Scanning line effect */
.scan-line {
  background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.8), transparent);
  height: 2px;
}

/* Form input focus effects */
input:focus, textarea:focus {
  box-shadow: 0 0 15px rgba(0, 255, 255, 0.3);
  transform: scale(1.02);
}

/* Button hover effects */
button:hover {
  box-shadow: 0 10px 30px rgba(0, 255, 255, 0.3);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .robot-container {
    transform: scale(0.8);
  }
}

/* Custom scrollbar for robot theme */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.3);
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #00ffff, #0080ff);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #00cccc, #0066cc);
}
</style>