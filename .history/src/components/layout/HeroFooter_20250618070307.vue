<template>
    <div :class="{ 'dark': isDark }" class="transition-colors duration-500">
      <!-- Robot Footer Section -->
      <footer ref="robotFooter" class="relative bg-black overflow-hidden">
        <!-- Animated Background Elements -->
        <div class="absolute inset-0">
          <!-- Grid Pattern -->
          <div ref="footerGrid" class="absolute inset-0 opacity-10" style="background-image: linear-gradient(rgba(0,255,255,0.3) 1px, transparent 1px), linear-gradient(90deg, rgba(0,255,255,0.3) 1px, transparent 1px); background-size: 40px 40px;"></div>
          
          <!-- Floating Circuit Elements -->
          <div ref="footerCircuit1" class="absolute top-10 left-20 w-16 h-16 opacity-20">
            <svg viewBox="0 0 100 100" class="w-full h-full text-cyan-400">
              <circle cx="50" cy="50" r="20" fill="none" stroke="currentColor" stroke-width="2"/>
              <circle cx="50" cy="50" r="5" fill="currentColor"/>
              <circle cx="30" cy="50" r="3" fill="currentColor"/>
              <circle cx="70" cy="50" r="3" fill="currentColor"/>
              <circle cx="50" cy="30" r="3" fill="currentColor"/>
              <circle cx="50" cy="70" r="3" fill="currentColor"/>
              <path d="M30 50 L70 50 M50 30 L50 70" stroke="currentColor" stroke-width="1"/>
            </svg>
          </div>
          
          <div ref="footerCircuit2" class="absolute bottom-20 right-32 w-20 h-20 opacity-15">
            <svg viewBox="0 0 100 100" class="w-full h-full text-green-400">
              <polygon points="50,10 90,30 90,70 50,90 10,70 10,30" fill="none" stroke="currentColor" stroke-width="2"/>
              <circle cx="50" cy="50" r="8" fill="currentColor"/>
              <circle cx="50" cy="25" r="2" fill="currentColor"/>
              <circle cx="75" cy="40" r="2" fill="currentColor"/>
              <circle cx="75" cy="60" r="2" fill="currentColor"/>
              <circle cx="50" cy="75" r="2" fill="currentColor"/>
              <circle cx="25" cy="60" r="2" fill="currentColor"/>
              <circle cx="25" cy="40" r="2" fill="currentColor"/>
            </svg>
          </div>
  
          <!-- Data Stream Lines -->
          <div ref="dataStream1" class="absolute top-0 left-1/4 w-px h-full bg-gradient-to-b from-transparent via-cyan-400/30 to-transparent"></div>
          <div ref="dataStream2" class="absolute top-0 right-1/3 w-px h-full bg-gradient-to-b from-transparent via-blue-400/30 to-transparent"></div>
          <div ref="dataStream3" class="absolute top-0 left-2/3 w-px h-full bg-gradient-to-b from-transparent via-green-400/30 to-transparent"></div>
        </div>
  
        <!-- Main Footer Content -->
        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
          <!-- Top Section -->
          <div class="grid grid-cols-1 lg:grid-cols-4 gap-12 mb-12">
            <!-- Brand Section with Robot -->
            <div ref="brandSection" class="lg:col-span-2 opacity-0">
              <div class="flex items-start space-x-6">
                <!-- Mini Robot Avatar -->
                <div ref="footerRobot" class="flex-shrink-0">
                  <div class="w-16 h-20 relative">
                    <!-- Robot Body -->
                    <div class="absolute bottom-0 w-12 h-12 bg-gradient-to-b from-gray-700 to-gray-800 rounded-lg border border-cyan-400/50 mx-auto left-1/2 transform -translate-x-1/2">
                      <!-- Chest Light -->
                      <div ref="chestLight" class="absolute top-2 left-1/2 transform -translate-x-1/2 w-2 h-2 bg-cyan-400 rounded-full"></div>
                      <!-- Arms -->
                      <div class="absolute top-2 -left-1 w-1 h-6 bg-gray-600 rounded-full"></div>
                      <div class="absolute top-2 -right-1 w-1 h-6 bg-gray-600 rounded-full"></div>
                    </div>
                    <!-- Robot Head -->
                    <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-8 h-8 bg-gradient-to-br from-gray-600 to-gray-800 rounded border border-cyan-400/50">
                      <!-- Eyes -->
                      <div class="flex justify-center space-x-1 mt-1">
                        <div ref="footerEye1" class="w-1 h-1 bg-cyan-400 rounded-full"></div>
                        <div ref="footerEye2" class="w-1 h-1 bg-cyan-400 rounded-full"></div>
                      </div>
                      <!-- Antenna -->
                      <div ref="footerAntenna" class="absolute -top-1 left-1/2 transform -translate-x-1/2 w-px h-2 bg-cyan-400"></div>
                      <div class="absolute -top-2 left-1/2 transform -translate-x-1/2 w-1 h-1 bg-cyan-400 rounded-full"></div>
                    </div>
                  </div>
                </div>
  
                <!-- Brand Info -->
                <div class="flex-1">
                  <h3 ref="brandTitle" class="text-3xl font-bold mb-4 opacity-0">
                    <span class="bg-gradient-to-r from-cyan-400 via-blue-400 to-green-400 bg-clip-text text-transparent font-mono">
                      CREATIVE_STUDIO
                    </span>
                  </h3>
                  <p ref="brandDescription" class="text-gray-400 mb-6 leading-relaxed opacity-0">
                    <span class="text-cyan-400 font-mono">[MISSION]</span> Transforming digital landscapes through innovative robotic intelligence and cutting-edge creative solutions.
                  </p>
                  
                  <!-- Status Indicators -->
                  <div ref="systemStatus" class="space-y-2 opacity-0">
                    <div class="flex items-center space-x-3">
                      <div class="flex items-center space-x-2">
                        <div ref="statusDot1" class="w-2 h-2 bg-green-400 rounded-full"></div>
                        <span class="text-green-400 font-mono text-sm">SYSTEM_ONLINE</span>
                      </div>
                    </div>
                    <div class="flex items-center space-x-3">
                      <div class="flex items-center space-x-2">
                        <div ref="statusDot2" class="w-2 h-2 bg-blue-400 rounded-full"></div>
                        <span class="text-blue-400 font-mono text-sm">AI_READY</span>
                      </div>
                    </div>
                    <div class="flex items-center space-x-3">
                      <div class="flex items-center space-x-2">
                        <div ref="statusDot3" class="w-2 h-2 bg-cyan-400 rounded-full"></div>
                        <span class="text-cyan-400 font-mono text-sm">CREATIVE_MODE</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
  
            <!-- Navigation Links -->
            <div ref="navSection" class="opacity-0">
              <h4 class="text-cyan-400 font-mono text-sm uppercase tracking-wider mb-6 flex items-center">
                <span class="text-gray-500 mr-2">[NAV]</span>
                SYSTEM_LINKS
              </h4>
              <ul class="space-y-3">
                <li><a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors duration-300 font-mono text-sm flex items-center group">
                  <span class="w-1 h-1 bg-cyan-400 rounded-full mr-3 opacity-0 group-hover:opacity-100 transition-opacity"></span>
                  HOME.exe
                </a></li>
                <li><a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors duration-300 font-mono text-sm flex items-center group">
                  <span class="w-1 h-1 bg-cyan-400 rounded-full mr-3 opacity-0 group-hover:opacity-100 transition-opacity"></span>
                  ABOUT.sys
                </a></li>
                <li><a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors duration-300 font-mono text-sm flex items-center group">
                  <span class="w-1 h-1 bg-cyan-400 rounded-full mr-3 opacity-0 group-hover:opacity-100 transition-opacity"></span>
                  SERVICES.dll
                </a></li>
                <li><a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors duration-300 font-mono text-sm flex items-center group">
                  <span class="w-1 h-1 bg-cyan-400 rounded-full mr-3 opacity-0 group-hover:opacity-100 transition-opacity"></span>
                  PORTFOLIO.db
                </a></li>
                <li><a href="#" class="text-gray-400 hover:text-cyan-400 transition-colors duration-300 font-mono text-sm flex items-center group">
                  <span class="w-1 h-1 bg-cyan-400 rounded-full mr-3 opacity-0 group-hover:opacity-100 transition-opacity"></span>
                  CONTACT.api
                </a></li>
              </ul>
            </div>
  
            <!-- Contact Info -->
            <div ref="contactSection" class="opacity-0">
              <h4 class="text-cyan-400 font-mono text-sm uppercase tracking-wider mb-6 flex items-center">
                <span class="text-gray-500 mr-2">[COM]</span>
                COMMUNICATION
              </h4>
              <div class="space-y-4">
                <div class="flex items-center space-x-3">
                  <div class="w-8 h-8 bg-gray-800 rounded border border-cyan-400/30 flex items-center justify-center">
                    <svg class="w-4 h-4 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                    </svg>
                  </div>
                  <div>
                    <p class="text-gray-400 font-mono text-sm">protocol@creative.studio</p>
                  </div>
                </div>
                
                <div class="flex items-center space-x-3">
                  <div class="w-8 h-8 bg-gray-800 rounded border border-cyan-400/30 flex items-center justify-center">
                    <svg class="w-4 h-4 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path>
                    </svg>
                  </div>
                  <div>
                    <p class="text-gray-400 font-mono text-sm">+1.800.ROBOT.AI</p>
                  </div>
                </div>
  
                <div class="flex items-center space-x-3">
                  <div class="w-8 h-8 bg-gray-800 rounded border border-cyan-400/30 flex items-center justify-center">
                    <svg class="w-4 h-4 text-cyan-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                    </svg>
                  </div>
                  <div>
                    <p class="text-gray-400 font-mono text-sm">Cyber District, Neo City</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
  
          <!-- Social Media Section -->
          <div ref="socialSection" class="border-t border-gray-800 pt-8 mb-8 opacity-0">
            <div class="flex flex-col md:flex-row justify-between items-center">
              <div class="mb-6 md:mb-0">
                <h4 class="text-cyan-400 font-mono text-sm uppercase tracking-wider mb-4 flex items-center">
                  <span class="text-gray-500 mr-2">[NET]</span>
                  SOCIAL_PROTOCOLS
                </h4>
                <div class="flex space-x-4">
                  <a href="#" ref="socialLink1" class="w-10 h-10 bg-gray-800 hover:bg-gray-700 border border-cyan-400/30 hover:border-cyan-400/60 rounded flex items-center justify-center transition-all duration-300 group">
                    <svg class="w-5 h-5 text-gray-400 group-hover:text-cyan-400" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.957-2.178-1.555-3.594-1.555-3.179 0-5.515 2.966-4.797 6.045-4.091-.205-7.719-2.165-10.148-5.144-1.29 2.213-.669 5.108 1.523 6.574-.806-.026-1.566-.247-2.229-.616-.054 2.281 1.581 4.415 3.949 4.89-.693.188-1.452.232-2.224.084.626 1.956 2.444 3.379 4.6 3.419-2.07 1.623-4.678 2.348-7.29 2.04 2.179 1.397 4.768 2.212 7.548 2.212 9.142 0 14.307-7.721 13.995-14.646.962-.695 1.797-1.562 2.457-2.549z"/>
                    </svg>
                  </a>
                  
                  <a href="#" ref="socialLink2" class="w-10 h-10 bg-gray-800 hover:bg-gray-700 border border-cyan-400/30 hover:border-cyan-400/60 rounded flex items-center justify-center transition-all duration-300 group">
                    <svg class="w-5 h-5 text-gray-400 group-hover:text-cyan-400" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                    </svg>
                  </a>
                  
                  <a href="#" ref="socialLink3" class="w-10 h-10 bg-gray-800 hover:bg-gray-700 border border-cyan-400/30 hover:border-cyan-400/60 rounded flex items-center justify-center transition-all duration-300 group">
                    <svg class="w-5 h-5 text-gray-400 group-hover:text-cyan-400" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12.017 0C5.396 0 .029 5.367.029 11.987c0 5.079 3.158 9.417 7.618 11.174-.105-.949-.199-2.403.041-3.439.219-.937 1.406-5.957 1.406-5.957s-.359-.72-.359-1.781c0-1.663.967-2.911 2.168-2.911 1.024 0 1.518.769 1.518 1.688 0 1.029-.653 2.567-.992 3.992-.285 1.193.6 2.165 1.775 2.165 2.128 0 3.768-2.245 3.768-5.487 0-2.861-2.063-4.869-5.008-4.869-3.41 0-5.409 2.562-5.409 5.199 0 1.033.394 2.143.889 2.741.099.12.112.225.085.345-.09.375-.293 1.199-.334 1.363-.053.225-.172.271-.402.165-1.495-.69-2.433-2.878-2.433-4.646 0-3.776 2.748-7.252 7.92-7.252 4.158 0 7.392 2.967 7.392 6.923 0 4.135-2.607 7.462-6.233 7.462-1.214 0-2.357-.629-2.75-1.378l-.748 2.853c-.271 1.043-1.002 2.35-1.492 3.146C9.57 23.812 10.763 24.009 12.017 24.009c6.624 0 11.99-5.367 11.99-11.988C24.007 5.367 18.641.001.012.001z"/>
                    </svg>
                  </a>
                  
                  <a href="#" ref="socialLink4" class="w-10 h-10 bg-gray-800 hover:bg-gray-700 border border-cyan-400/30 hover:border-cyan-400/60 rounded flex items-center justify-center transition-all duration-300 group">
                    <svg class="w-5 h-5 text-gray-400 group-hover:text-cyan-400" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12 0C5.374 0 0 5.373 0 12 0 17.302 3.438 21.8 8.207 23.387c.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
                    </svg>
                  </a>
                </div>
              </div>
  
              <!-- Newsletter Signup -->
              <div ref="newsletterSection" class="opacity-0">
                <h4 class="text-cyan-400 font-mono text-sm uppercase tracking-wider mb-4 flex items-center">
                  <span class="text-gray-500 mr-2">[SUB]</span>
                  DATA_FEED
                </h4>
                <form @submit.prevent="subscribeNewsletter" class="flex">
                  <input
                    v-model="newsletterEmail"
                    type="email"
                    placeholder="your@protocol.net"
                    class="flex-1 px-4 py-2 bg-gray-800 border border-cyan-400/30 rounded-l text-white placeholder-gray-500 focus:outline-none focus:ring-1 focus:ring-cyan-400 focus:border-cyan-400 font-mono text-sm"
                    required
                  >
                  <button
                    type="submit"
                    class="px-6 py-2 bg-gradient-to-r from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 text-white font-mono text-sm rounded-r transition-all duration-300 flex items-center"
                  >
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path>
                    </svg>
                  </button>
                </form>
              </div>
            </div>
          </div>
  
          <!-- Bottom Section -->
          <div ref="bottomSection" class="border-t border-gray-800 pt-8 opacity-0">
            <div class="flex flex-col md:flex-row justify-between items-center">
              <!-- Copyright -->
              <div class="mb-4 md:mb-0">
                <p class="text-gray-500 font-mono text-sm flex items-center">
                  <span class="text-cyan-400 mr-2">&copy;</span>
                  2024 CREATIVE_STUDIO.exe - All protocols reserved
                </p>
              </div>
  
              <!-- System Info -->
              <div class="flex items-center space-x-6 text-xs font-mono">
                <div class="flex items-center space-x-2">
                  <div ref="systemIndicator" class="w-2 h-2 bg-green-400 rounded-full"></div>
                  <span class="text-green-400">SYSTEM_v2.1.0</span>
                </div>
                <div class="text-gray-500">
                  UPTIME: <span ref="uptimeCounter" class="text-cyan-400">99.9%</span>
                </div>
                <div class="text-gray-500">
                  LOAD: <span class="text-blue-400">OPTIMAL</span>
                </div>
              </div>
            </div>
          </div>
        </div>
  
        <!-- Scroll to Top Robot -->
        <button
          ref="scrollToTop"
          @click="scrollToTop"
          class="fixed bottom-8 right-8 w-12 h-12 bg-gradient-to-br from-cyan-500 to-blue-500 hover:from-cyan-600 hover:to-blue-600 rounded-full shadow-lg hover:shadow-cyan-400/25 transition-all duration-300 transform hover:scale-110 opacity-0 z-50"
        >
          <div class="flex items-center justify-center">
            <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"></path>
            </svg>
          </div>
        </button>
      </footer>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue'
  import { gsap } from 'gsap'
  import { ScrollTrigger } from 'gsap/ScrollTrigger'
  
  // Register GSAP plugins
  gsap.registerPlugin(ScrollTrigger)
  
  // Reactive data
  const isDark = ref(true)
  const newsletterEmail = ref('')
  
  // Template refs
  const robotFooter = ref(null)
  const footerGrid = ref(null)
  const footerCircuit1 = ref(null)
  const footerCircuit2 = ref(null)
  const dataStream1 = ref(null)
  const dataStream2 = ref(null)
  const dataStream3 = ref(null)
  const brandSection = ref(null)
  const navSection = ref(null)
  const contactSection = ref(null)
  const socialSection = ref(null)
  const bottomSection = ref(null)
  const newsletterSection = ref(null)
  const footerRobot = ref(null)
  const footerEye1 = ref(null)
  const footerEye2 = ref(null)
  const footerAntenna = ref(null)
  const chestLight = ref(null)
  const brandTitle = ref(null)
  const brandDescription = ref(null)
  const systemStatus = ref(null)
  const statusDot1 = ref(null)
  const statusDot2 = ref(null)
  const statusDot3 = ref(null)
  const socialLink1 = ref(null)
  const socialLink2 = ref(null)
  const socialLink3 = ref(null)
  const socialLink4 = ref(null)
  const systemIndicator = ref(null)
  const uptimeCounter = ref(null)
  const scrollToTopBtn = ref(null)
  
  // Methods
  const subscribeNewsletter = () => {
    // Animate robot response
    gsap.to([footerEye1.value, footerEye2.value], {
      duration: 0.2,
      scaleY: 0.1,
      repeat: 5,
      yoyo: true,
      ease: "power2.inOut"
    })
    
    gsap.to(chestLight.value, {
      duration: 0.5,
      scale: 1.5,
      repeat: 3,
      yoyo: true,
      ease: "power2.inOut"
    })
    
    alert(`Subscription protocol initiated for: ${newsletterEmail.value}`)
    newsletterEmail.value = ''
  }
  
  const scrollToTop = () => {
    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    })
  }
  
  // GSAP Animations
  const initFooterAnimations = () => {
    // Background animations
    gsap.to(footerGrid.value, {
      duration: 30,
      backgroundPosition: "80px 80px",
      repeat: -1,
      ease: "none"
    })
    
    // Circuit animations
    gsap.to(footerCircuit1.value, {
      duration: 12,
      rotation: 360,
      repeat: -1,
      ease: "none"
    })
    
    gsap.to(footerCircuit2.value, {
      duration: 15,
      rotation: -360,
      repeat: -1,
      ease: "none"
    })
    
    // Data stream animations
    gsap.to([dataStream1.value, dataStream2.value, dataStream3.value], {
      duration: 3,
      backgroundPosition: "0 100px",
      repeat: -1,
      stagger: 0.5,
      ease: "none"
    })
    
    // Robot animations
    gsap.to([footerEye1.value, footerEye2.value], {
      duration: 0.1,
      scaleY: 0.1,
      repeat: -1,
      repeatDelay: 4,
      ease: "power2.inOut"
    })
    
    gsap.to(footerAntenna.value, {
      duration: 2,
      scaleY: 1.3,
      repeat: -1,
      yoyo: true,
      ease: "power2.inOut"
    })
    
    gsap.to(chestLight.value, {
      duration: 1.5,
      scale: 1.2,
      opacity: 0.7,
      repeat: -1,
      yoyo: true,
      ease: "power2.inOut"
    })
    
    // Status dots pulsing
    gsap.to([statusDot1.value, statusDot2.value, statusDot3.value], {
      duration: 1,
      scale: 1.3,
      repeat: -1,
      stagger: 0.3,
      yoyo: true,
      ease: "power2.inOut"
    })
    
    // System indicator
    gsap.to(systemIndicator.value, {
      duration: 2,
      scale: 1.2,
      repeat: -1,
      yoyo: true,
      ease: "power2.inOut"
    })
    
    // Social links hover effect
    [socialLink1.value, socialLink2.value, socialLink3.value, socialLink4.value].forEach(link => {
      if (link) {
        link.addEventListener('mouseenter', () => {
          gsap.to(link, {
            duration: 0.3,
            scale: 1.1,
            rotationY: 180,
            ease: "power2.out"
          })
        })
        
        link.addEventListener('mouseleave', () => {
          gsap.to(link, {
            duration: 0.3,
            scale: 1,
            rotationY: 0,
            ease: "power2.out"
          })
        })
      }
    })
  }
  
  const initScrollTriggerAnimations = () => {
    // Main footer entrance animation
    ScrollTrigger.create({
      trigger: robotFooter.value,
      start: "top 90%",
      end: "bottom 10%",
      toggleActions: "play none none reverse",
      animation: gsap.timeline()
        .from(brandSection.value, {
          duration: 1,
          x: -100,
          opacity: 0,
          ease: "power3.out"
        })
        .from(navSection.value, {
          duration: 0.8,
          y: 50,
          opacity: 0,
          ease: "power3.out"
        }, "-=0.6")
        .from(contactSection.value, {
          duration: 0.8,
          y: 50,
          opacity: 0,
          ease: "power3.out"
        }, "-=0.6")
        .from(socialSection.value, {
          duration: 0.8,
          y: 30,
          opacity: 0,
          ease: "power3.out"
        }, "-=0.4")
        .from(bottomSection.value, {
          duration: 0.6,
          y: 20,
          opacity: 0,
          ease: "power3.out"
        }, "-=0.2")
    })
    
    // Brand section detailed animation
    ScrollTrigger.create({
      trigger: brandSection.value,
      start: "top 85%",
      toggleActions: "play none none reverse",
      animation: gsap.timeline()
        .from(brandTitle.value, {
          duration: 0.8,
          y: 30,
          opacity: 0,
          ease: "power3.out"
        })
        .from(brandDescription.value, {
          duration: 0.6,
          y: 20,
          opacity: 0,
          ease: "power3.out"
        }, "-=0.4")
        .from(systemStatus.value, {
          duration: 0.6,
          y: 20,
          opacity: 0,
          ease: "power3.out"
        }, "-=0.2")
    })
    
    // Newsletter section animation
    ScrollTrigger.create({
      trigger: newsletterSection.value,
      start: "top 90%",
      toggleActions: "play none none reverse",
      animation: gsap.from(newsletterSection.value, {
        duration: 0.8,
        scale: 0.9,
        opacity: 0,
        ease: "back.out(1.7)"
      })
    })
    
    // Scroll to top button
    ScrollTrigger.create({
      trigger: "body",
      start: "top -100px",
      end: "bottom bottom",
      toggleActions: "play none none reverse",
      animation: gsap.to(scrollToTopBtn.value, {
        duration: 0.3,
        opacity: 1,
        scale: 1,
        ease: "power2.out"
      })
    })
  }
  
  // Lifecycle hooks
  onMounted(() => {
    // Initialize animations
    initFooterAnimations()
    initScrollTriggerAnimations()
  })
  
  onUnmounted(() => {
    // Clean up ScrollTrigger instances
    ScrollTrigger.getAll().forEach(trigger => trigger.kill())
  })
  </script>
  
  <style scoped>
  /* Robot-themed footer styles */
  .robot-footer-glow {
    box-shadow: 0 0 30px rgba(0, 255, 255, 0.1);
  }
  
  /* Data stream animation */
  .data-stream {
    background: linear-gradient(to bottom, transparent, rgba(0, 255, 255, 0.3), transparent);
    background-size: 100% 50px;
    animation: data-flow 3s linear infinite;
  }
  
  @keyframes data-flow {
    0% { background-position: 0 -50px; }
    100% { background-position: 0 100px; }
  }
  
  /* Circuit glow effect */
  .circuit-glow {
    filter: drop-shadow(0 0 5px rgba(0, 255, 255, 0.3));
  }
  
  /* Social link hover effects */
  .social-link:hover {
    transform: translateY(-2px) rotateY(180deg);
    box-shadow: 0 5px 15px rgba(0, 255, 255, 0.3);
  }
  
  /* Newsletter input focus */
  .newsletter-input:focus {
    box-shadow: 0 0 10px rgba(0, 255, 255, 0.3);
    transform: scale(1.02);
  }
  
  /* Scroll to top button */
  .scroll-to-top {
    backdrop-filter: blur(10px);
    border: 1px solid rgba(0, 255, 255, 0.2);
  }
  
  .scroll-to-top:hover {
    box-shadow: 0 0 20px rgba(0, 255, 255, 0.4);
  }
  
  /* Robot mini avatar animations */
  .robot-avatar {
    transition: all 0.3s ease;
  }
  
  .robot-avatar:hover {
    transform: scale(1.1) rotateY(10deg);
  }
  
  /* Status indicator animations */
  .status-dot {
    animation: pulse-glow 2s ease-in-out infinite;
  }
  
  @keyframes pulse-glow {
    0%, 100% {
      opacity: 0.6;
      transform: scale(1);
    }
    50% {
      opacity: 1;
      transform: scale(1.2);
    }
  }
  
  /* Link hover effects */
  .nav-link {
    position: relative;
    overflow: hidden;
  }
  
  .nav-link::before {
    content: '';
    position: absolute;
    left: -100%;
    top: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(0, 255, 255, 0.1), transparent);
    transition: left 0.5s ease;
  }
  
  .nav-link:hover::before {
    left: 100%;
  }
  
  /* Responsive adjustments */
  @media (max-width: 768px) {
    .robot-footer {
      padding: 3rem 1rem;
    }
    
    .footer-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
    
    .social-links {
      justify-content: center;
    }
    
    .newsletter-form {
      flex-direction: column;
      gap: 0.5rem;
    }
  }
  
  /* Custom scrollbar for footer */
  .footer-section::-webkit-scrollbar {
    width: 4px;
  }
  
  .footer-section::-webkit-scrollbar-track {
    background: rgba(0, 0, 0, 0.2);
  }
  
  .footer-section::-webkit-scrollbar-thumb {
    background: linear-gradient(to bottom, #00ffff, #0080ff);
    border-radius: 2px;
  }
  
  /* Glitch effect for system status */
  .system-status {
    animation: subtle-glitch 5s infinite;
  }
  
  @keyframes subtle-glitch {
    0%, 98%, 100% { transform: translate(0); }
    99% { transform: translate(1px, -1px); }
  }
  </style>