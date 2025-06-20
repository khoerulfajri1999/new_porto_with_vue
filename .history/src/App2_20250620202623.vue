<template>
  <section class="relative py-20 bg-gradient-to-tl from-[#030415] via-[#1E0B38] to-[#030415] overflow-hidden min-h-screen">
    <!-- Animated Background Grid -->
    <div class="absolute inset-0 bg-[linear-gradient(rgba(120,119,198,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(120,119,198,0.1)_1px,transparent_1px)] bg-[size:50px_50px] animate-grid-move"></div>

    <!-- Floating Circuit Elements -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div ref="circuit1" class="absolute top-20 left-10 w-32 h-32 opacity-30 animate-spin-slow">
        <svg viewBox="0 0 100 100" class="w-full h-full text-cyan-400">
          <circle cx="20" cy="20" r="3" fill="currentColor" />
          <circle cx="80" cy="20" r="3" fill="currentColor" />
          <circle cx="50" cy="50" r="5" fill="currentColor" />
          <circle cx="20" cy="80" r="3" fill="currentColor" />
          <circle cx="80" cy="80" r="3" fill="currentColor" />
          <path d="M20 20 L50 50 L80 20 M20 80 L50 50 L80 80" stroke="currentColor" stroke-width="1" fill="none" />
        </svg>
      </div>
      
      <div ref="circuit2" class="absolute top-40 right-20 w-24 h-24 opacity-40 animate-spin-reverse">
        <svg viewBox="0 0 100 100" class="w-full h-full text-green-400">
          <rect x="10" y="10" width="80" height="80" fill="none" stroke="currentColor" stroke-width="2" />
          <circle cx="30" cy="30" r="4" fill="currentColor" />
          <circle cx="70" cy="30" r="4" fill="currentColor" />
          <circle cx="50" cy="70" r="6" fill="currentColor" />
          <path d="M30 30 L70 30 L50 70 Z" stroke="currentColor" stroke-width="1" fill="none" />
        </svg>
      </div>
    </div>

    <!-- Glowing Orbs -->
    <div class="absolute top-1/4 left-1/6 w-4 h-4 bg-cyan-400 rounded-full blur-sm opacity-60 animate-pulse-glow"></div>
    <div class="absolute top-3/4 right-1/4 w-6 h-6 bg-green-400 rounded-full blur-sm opacity-40 animate-pulse-glow-delayed"></div>
    <div class="absolute bottom-1/3 left-3/4 w-3 h-3 bg-blue-400 rounded-full blur-sm opacity-70 animate-pulse-glow-delayed-2"></div>

    <div class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16" :class="{ 'animate-fade-in-up': isVisible }">
        <!-- Robot Head Icon -->
        <div ref="robotHead" class="mx-auto mb-8 w-24 h-24 relative animate-robot-head-entrance">
          <div class="w-full h-full bg-gradient-to-br from-cyan-400 to-blue-500 rounded-lg relative overflow-hidden shadow-2xl">
            <div class="absolute inset-2 bg-gray-900 rounded-md flex items-center justify-center">
              <div class="flex space-x-3">
                <div ref="robotEye1" class="w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50 animate-robot-blink"></div>
                <div ref="robotEye2" class="w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50 animate-robot-blink-delayed"></div>
              </div>
              <div class="absolute bottom-2 left-1/2 transform -translate-x-1/2 w-4 h-1 bg-cyan-400 rounded-full opacity-60"></div>
            </div>
            <div class="absolute -top-2 left-1/2 transform -translate-x-1/2 w-1 h-4 bg-cyan-400 rounded-full animate-antenna-pulse"></div>
            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50 animate-antenna-pulse"></div>
          </div>
        </div>

        <h2 class="text-5xl sm:text-6xl font-bold mb-6 animate-title-entrance">
          <span class="bg-gradient-to-r from-cyan-400 via-blue-400 to-green-400 bg-clip-text text-transparent">
            SEND MESSAGE
          </span>
        </h2>

        <p class="text-xl text-gray-300 mb-4 animate-subtitle-entrance">
          <span class="text-cyan-400 font-mono">[SYSTEM READY]</span> Let's work together!
        </p>

        <div class="flex items-center justify-center space-x-2 animate-status-entrance">
          <div class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></div>
          <span class="text-green-400 font-mono text-sm">CONNECTION_ACTIVE</span>
        </div>
      </div>

      <!-- Main Content Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <!-- Left Side - Robot Illustration -->
        <div ref="robotContainer" class="relative animate-robot-entrance">
          <div class="w-80 h-96 mx-auto relative">
            <!-- Robot Torso -->
            <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-48 h-64 bg-gradient-to-b from-gray-700 to-gray-800 rounded-t-3xl border-2 border-cyan-400/30 shadow-2xl">
              <!-- Chest Panel -->
              <div class="absolute top-8 left-1/2 transform -translate-x-1/2 w-32 h-20 bg-gray-900 rounded-lg border border-cyan-400/50">
                <!-- Status Lights -->
                <div class="flex justify-center space-x-2 mt-3">
                  <div class="w-2 h-2 bg-green-400 rounded-full animate-status-light-1"></div>
                  <div class="w-2 h-2 bg-blue-400 rounded-full animate-status-light-2"></div>
                  <div class="w-2 h-2 bg-cyan-400 rounded-full animate-status-light-3"></div>
                </div>
                <!-- Display Screen -->
                <div class="mt-2 mx-2 h-8 bg-black rounded border border-cyan-400/30 flex items-center justify-center">
                  <span ref="robotDisplay" class="text-cyan-400 font-mono text-xs transition-all duration-300" :class="{ 'animate-pulse': isSending }">
                    {{ robotDisplayText }}
                  </span>
                </div>
              </div>
              
              <!-- Arms -->
              <div class="absolute top-16 -left-8 w-6 h-32 bg-gradient-to-b from-gray-600 to-gray-700 rounded-full border border-cyan-400/30 animate-arm-left"></div>
              <div class="absolute top-16 -right-8 w-6 h-32 bg-gradient-to-b from-gray-600 to-gray-700 rounded-full border border-cyan-400/30 animate-arm-right"></div>
              
              <!-- Hands -->
              <div class="absolute top-44 -left-10 w-8 h-8 bg-gray-600 rounded-full border border-cyan-400/30"></div>
              <div class="absolute top-44 -right-10 w-8 h-8 bg-gray-600 rounded-full border border-cyan-400/30"></div>
            </div>

            <!-- Robot Head -->
            <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-32 h-32 bg-gradient-to-br from-gray-600 to-gray-800 rounded-2xl border-2 border-cyan-400/50 shadow-2xl animate-main-head-entrance">
              <!-- Face Screen -->
              <div class="absolute inset-4 bg-black rounded-lg border border-cyan-400/30 flex flex-col items-center justify-center">
                <!-- Main Eyes -->
                <div class="flex space-x-4 mb-2">
                  <div ref="mainEye1" class="w-4 h-4 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50" :class="{ 'animate-robot-thinking': isSending }"></div>
                  <div ref="mainEye2" class="w-4 h-4 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50" :class="{ 'animate-robot-thinking': isSending }"></div>
                </div>
                <!-- Expression Line -->
                <div class="w-8 h-0.5 bg-cyan-400 rounded-full"></div>
              </div>
              
              <!-- Head Antenna -->
              <div class="absolute -top-4 left-1/2 transform -translate-x-1/2 w-2 h-6 bg-cyan-400 rounded-full"></div>
              <div class="absolute -top-6 left-1/2 transform -translate-x-1/2 w-3 h-3 bg-cyan-400 rounded-full shadow-lg shadow-cyan-400/50 animate-antenna-light"></div>
            </div>

            <!-- Floating Data Particles -->
            <div class="absolute top-20 -left-12 w-1 h-1 bg-cyan-400 rounded-full opacity-60 animate-data-particle-1"></div>
            <div class="absolute top-32 -right-8 w-1 h-1 bg-green-400 rounded-full opacity-60 animate-data-particle-2"></div>
            <div class="absolute top-48 left-2 w-1 h-1 bg-blue-400 rounded-full opacity-60 animate-data-particle-3"></div>

            <!-- Holographic Effect -->
            <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-64 h-4 bg-gradient-to-r from-transparent via-cyan-400/20 to-transparent rounded-full blur-sm animate-holographic-ring"></div>
          </div>
        </div>

        <!-- Right Side - Message Form -->
        <div class="animate-form-entrance">
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
            <div class="absolute left-0 w-full h-0.5 bg-gradient-to-r from-transparent via-cyan-400 to-transparent opacity-60 animate-scan-line"></div>

            <form @submit.prevent="sendEmail" class="space-y-6">
              <!-- Name Input -->
              <div class="animate-field-entrance">
                <label class="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                  <span class="text-gray-500">[01]</span> NAME
                </label>
                <div class="relative">
                  <input
                    v-model="formData.name"
                    type="text"
                    required
                    class="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 font-mono focus:scale-[1.02] focus:shadow-[0_0_15px_rgba(0,255,255,0.3)]"
                    placeholder="Enter your name..."
                  >
                  <div class="absolute right-3 top-1/2 transform -translate-y-1/2 w-2 h-2 bg-cyan-400 rounded-full opacity-60"></div>
                </div>
              </div>

              <!-- Email Input -->
              <div class="animate-field-entrance-delayed">
                <label class="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                  <span class="text-gray-500">[02]</span> EMAIL
                </label>
                <div class="relative">
                  <input
                    v-model="formData.email"
                    type="email"
                    required
                    class="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 font-mono focus:scale-[1.02] focus:shadow-[0_0_15px_rgba(0,255,255,0.3)]"
                    placeholder="Enter your email..."
                  >
                  <div class="absolute right-3 top-1/2 transform -translate-y-1/2 w-2 h-2 bg-green-400 rounded-full opacity-60"></div>
                </div>
              </div>

              <!-- Message Input -->
              <div class="animate-field-entrance-delayed-2">
                <label class="block text-cyan-400 text-sm font-mono mb-2 uppercase tracking-wider">
                  <span class="text-gray-500">[03]</span> MESSAGE
                </label>
                <div class="relative">
                  <textarea
                    v-model="formData.message"
                    required
                    rows="5"
                    class="w-full px-4 py-3 bg-black/50 border border-cyan-400/30 rounded-lg text-white placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-cyan-400 focus:border-transparent transition-all duration-300 resize-none font-mono focus:scale-[1.02] focus:shadow-[0_0_15px_rgba(0,255,255,0.3)]"
                    placeholder="Enter your message..."
                  ></textarea>
                  <div class="absolute right-3 bottom-3 w-2 h-2 bg-blue-400 rounded-full opacity-60"></div>
                </div>
              </div>

              <!-- Submit Button -->
              <div class="animate-button-entrance">
                <button
                  type="submit"
                  :disabled="isSending"
                  class="w-full bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 disabled:opacity-50 text-white font-bold py-4 px-8 rounded-lg text-lg transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-cyan-400/25 font-mono uppercase tracking-wider relative overflow-hidden"
                  :class="{ 'animate-button-sending': isSending }"
                >
                  <span v-if="!isSending" class="flex items-center justify-center">
                    SEND MESSAGE
                  </span>
                  <span v-else class="flex items-center justify-center">
                    <div class="w-5 h-5 mr-2 border-2 border-white border-t-transparent rounded-full animate-spin"></div>
                    TRANSMITTING...
                  </span>
                  
                  <!-- Button Glow Effect -->
                  <div class="absolute inset-0 bg-gradient-to-r from-cyan-400/20 to-blue-400/20 rounded-lg" :class="{ 'animate-button-glow': success === true }"></div>
                </button>
              </div>

              <!-- Success/Error Messages -->
              <div v-if="success === true" class="text-green-400 text-center font-mono text-sm bg-green-400/10 border border-green-400/30 rounded-lg p-3 animate-message-success">
                [SUCCESS] Message sent successfully!
              </div>
              <div v-if="success === false" class="text-red-400 text-center font-mono text-sm bg-red-400/10 border border-red-400/30 rounded-lg p-3 animate-message-error">
                [ERROR] Failed to send message. Please try again.
              </div>
            </form>

            <!-- Status Bar -->
            <div class="mt-6 flex items-center justify-between text-xs font-mono animate-status-bar-entrance">
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
</template>

<script setup>
import { ref, reactive, computed, onMounted } from 'vue'
import emailjs from '@emailjs/browser'

// Reactive data
const isVisible = ref(false)
const isSending = ref(false)
const success = ref(null)

// Form data
const formData = reactive({
  name: '',
  email: '',
  message: ''
})

// Computed properties
const robotDisplayText = computed(() => {
  if (isSending.value) return 'TRANSMITTING...'
  if (success.value === true) return 'MESSAGE_SENT!'
  if (success.value === false) return 'TRANSMISSION_FAILED'
  return 'READY_TO_RECEIVE'
})

// Methods
const sendEmail = async (e) => {
  e.preventDefault()
  isSending.value = true
  success.value = null

  try {
    // Mengambil nilai dari environment variables
    const serviceID = import.meta.env.VITE_SERVICE_ID
    const templateID = import.meta.env.VITE_TEMPLATE_ID
    const publicKey = import.meta.env.VITE_PUBLIC_KEY

    const templateParams = {
      from_name: formData.name,
      from_email: formData.email,
      to_email: 'khoerulfajri1999@gmail.com',
      message: formData.message,
      reply_to: formData.email,
    }

    const response = await emailjs.send(serviceID, templateID, templateParams, publicKey)
    
    console.log('SUCCESS!', response.status, response.text)
    success.value = true
    
    // Reset form
    formData.name = ''
    formData.email = ''
    formData.message = ''
    
  } catch (err) {
    console.log('FAILED...', err)
    success.value = false
  } finally {
    isSending.value = false
    
    // Reset success/error message after 5 seconds
    setTimeout(() => {
      success.value = null
    }, 5000)
  }
}

// Lifecycle
onMounted(() => {
  isVisible.value = true
})
</script>

<style scoped>
/* Custom Animations */
@keyframes grid-move {
  0% { background-position: 0px 0px; }
  100% { background-position: 50px 50px; }
}

@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes spin-reverse {
  from { transform: rotate(360deg); }
  to { transform: rotate(0deg); }
}

@keyframes pulse-glow {
  0%, 100% { transform: scale(1); opacity: 0.6; }
  50% { transform: scale(1.5); opacity: 0.8; }
}

@keyframes pulse-glow-delayed {
  0%, 100% { transform: scale(1); opacity: 0.4; }
  50% { transform: scale(1.5); opacity: 0.7; }
}

@keyframes pulse-glow-delayed-2 {
  0%, 100% { transform: scale(1); opacity: 0.7; }
  50% { transform: scale(1.5); opacity: 0.9; }
}

@keyframes robot-blink {
  0%, 90%, 100% { transform: scaleY(1); }
  95% { transform: scaleY(0.1); }
}

@keyframes robot-blink-delayed {
  0%, 90%, 100% { transform: scaleY(1); }
  92% { transform: scaleY(0.1); }
}

@keyframes robot-thinking {
  0%, 100% { transform: scaleY(1); }
  25% { transform: scaleY(0.3); }
  50% { transform: scaleY(1); }
  75% { transform: scaleY(0.3); }
}

@keyframes antenna-pulse {
  0%, 100% { transform: scale(1); opacity: 0.8; }
  50% { transform: scale(1.2); opacity: 1; }
}

@keyframes antenna-light {
  0%, 100% { transform: scale(1); opacity: 0.8; }
  50% { transform: scale(1.2); opacity: 1; }
}

@keyframes status-light-1 {
  0%, 100% { transform: scale(1); opacity: 0.7; }
  33% { transform: scale(1.3); opacity: 1; }
}

@keyframes status-light-2 {
  0%, 100% { transform: scale(1); opacity: 0.7; }
  66% { transform: scale(1.3); opacity: 1; }
}

@keyframes status-light-3 {
  0%, 100% { transform: scale(1); opacity: 0.7; }
  100% { transform: scale(1.3); opacity: 1; }
}

@keyframes arm-left {
  0%, 100% { transform: rotate(0deg); }
  50% { transform: rotate(5deg); }
}

@keyframes arm-right {
  0%, 100% { transform: rotate(0deg); }
  50% { transform: rotate(-5deg); }
}

@keyframes data-particle-1 {
  0%, 100% { transform: translateY(0); opacity: 0.6; }
  50% { transform: translateY(-20px); opacity: 1; }
}

@keyframes data-particle-2 {
  0%, 100% { transform: translateY(0); opacity: 0.6; }
  50% { transform: translateY(-20px); opacity: 1; }
}

@keyframes data-particle-3 {
  0%, 100% { transform: translateY(0); opacity: 0.6; }
  50% { transform: translateY(-20px); opacity: 1; }
}

@keyframes holographic-ring {
  0%, 100% { transform: scaleX(1); opacity: 0.2; }
  50% { transform: scaleX(1.2); opacity: 0.4; }
}

@keyframes scan-line {
  0% { top: 0%; }
  100% { top: 100%; }
}

@keyframes fade-in-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes robot-head-entrance {
  from { transform: scale(0) rotate(180deg); opacity: 0; }
  to { transform: scale(1) rotate(0deg); opacity: 1; }
}

@keyframes title-entrance {
  from { opacity: 0; transform: translateY(50px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes subtitle-entrance {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes status-entrance {
  from { opacity: 0; transform: scale(0); }
  to { opacity: 1; transform: scale(1); }
}

@keyframes robot-entrance {
  from { opacity: 0; transform: translateX(-100px); }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes main-head-entrance {
  from { opacity: 0; transform: translateY(-50px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes form-entrance {
  from { opacity: 0; transform: translateX(100px); }
  to { opacity: 1; transform: translateX(0); }
}

@keyframes field-entrance {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes field-entrance-delayed {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes field-entrance-delayed-2 {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes button-entrance {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes status-bar-entrance {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes button-glow {
  0% { opacity: 0; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.2); }
  100% { opacity: 0; transform: scale(1); }
}

@keyframes message-success {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes message-error {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Animation Classes */
.animate-grid-move {
  animation: grid-move 20s linear infinite;
}

.animate-spin-slow {
  animation: spin-slow 8s linear infinite;
}

.animate-spin-reverse {
  animation: spin-reverse 6s linear infinite;
}

.animate-pulse-glow {
  animation: pulse-glow 2s ease-in-out infinite;
}

.animate-pulse-glow-delayed {
  animation: pulse-glow-delayed 2s ease-in-out infinite 0.3s;
}

.animate-pulse-glow-delayed-2 {
  animation: pulse-glow-delayed-2 2s ease-in-out infinite 0.6s;
}

.animate-robot-blink {
  animation: robot-blink 3s ease-in-out infinite;
}

.animate-robot-blink-delayed {
  animation: robot-blink-delayed 3s ease-in-out infinite;
}

.animate-robot-thinking {
  animation: robot-thinking 1s ease-in-out infinite;
}

.animate-antenna-pulse {
  animation: antenna-pulse 1.5s ease-in-out infinite;
}

.animate-antenna-light {
  animation: antenna-light 1.5s ease-in-out infinite;
}

.animate-status-light-1 {
  animation: status-light-1 1.5s ease-in-out infinite;
}

.animate-status-light-2 {
  animation: status-light-2 1.5s ease-in-out infinite 0.2s;
}

.animate-status-light-3 {
  animation: status-light-3 1.5s ease-in-out infinite 0.4s;
}

.animate-arm-left {
  animation: arm-left 4s ease-in-out infinite;
}

.animate-arm-right {
  animation: arm-right 4s ease-in-out infinite;
}

.animate-data-particle-1 {
  animation: data-particle-1 3s ease-in-out infinite;
}

.animate-data-particle-2 {
  animation: data-particle-2 3s ease-in-out infinite 0.5s;
}

.animate-data-particle-3 {
  animation: data-particle-3 3s ease-in-out infinite 1s;
}

.animate-holographic-ring {
  animation: holographic-ring 2s ease-in-out infinite;
}

.animate-scan-line {
  animation: scan-line 3s ease-in-out infinite;
}

.animate-fade-in-up {
  animation: fade-in-up 1s ease-out;
}

.animate-robot-head-entrance {
  animation: robot-head-entrance 1s ease-out;
}

.animate-title-entrance {
  animation: title-entrance 0.8s ease-out 0.2s both;
}

.animate-subtitle-entrance {
  animation: subtitle-entrance 0.6s ease-out 0.4s both;
}

.animate-status-entrance {
  animation: status-entrance 0.6s ease-out 0.6s both;
}

.animate-robot-entrance {
  animation: robot-entrance 1.2s ease-out 0.8s both;
}

.animate-main-head-entrance {
  animation: main-head-entrance 0.8s ease-out 1.4s both;
}

.animate-form-entrance {
  animation: form-entrance 1.2s ease-out 1s both;
}

.animate-field-entrance {
  animation: field-entrance 0.6s ease-out 1.2s both;
}

.animate-field-entrance-delayed {
  animation: field-entrance-delayed 0.6s ease-out 1.3s both;
}

.animate-field-entrance-delayed-2 {
  animation: field-entrance-delayed-2 0.6s ease-out 1.4s both;
}

.animate-button-entrance {
  animation: button-entrance 0.6s ease-out 1.5s both;
}

.animate-status-bar-entrance {
  animation: status-bar-entrance 0.6s ease-out 1.6s both;
}

.animate-button-glow {
  animation: button-glow 0.5s ease-out;
}

.animate-message-success {
  animation: message-success 0.5s ease-out;
}

.animate-message-error {
  animation: message-error 0.5s ease-out;
}

/* Hover Effects */
input:focus, textarea:focus {
  box-shadow: 0 0 15px rgba(0, 255, 255, 0.3);
  transform: scale(1.02);
}

button:hover {
  box-shadow: 0 10px 30px rgba(0, 255, 255, 0.3);
}

/* Responsive */
@media (max-width: 768px) {
  .robot-container {
    transform: scale(0.8);
  }
}
</style>
