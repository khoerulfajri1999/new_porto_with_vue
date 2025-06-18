<template>
  <section
    class="container px-10 sm:px-0 relative z-10 flex-1 flex flex-col lg:flex-row justify-between items-center mx-auto "
    ref="mainRef"
    id="home">
    
    <!-- Background Effects -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <!-- Animated Grid -->
      <div class="absolute inset-0 bg-[linear-gradient(rgba(6,182,212,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(6,182,212,0.1)_1px,transparent_1px)] bg-[size:50px_50px] animate-pulse"></div>
      
      <!-- Floating Elements -->
      <div class="absolute top-20 left-20 w-4 h-4 bg-cyan-400/30 rotate-45 animate-float"></div>
      <div class="absolute top-40 right-32 w-6 h-6 bg-blue-400/30 rounded-full animate-bounce"></div>
      <div class="absolute bottom-32 left-40 w-3 h-3 bg-purple-400/30 rotate-12 animate-ping"></div>
      
      <!-- Glowing Orbs -->
      <div class="absolute top-1/4 left-1/4 w-32 h-32 bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-full blur-xl animate-pulse"></div>
      <div class="absolute bottom-1/4 right-1/4 w-40 h-40 bg-gradient-to-r from-purple-500/20 to-pink-500/20 rounded-full blur-xl animate-pulse"></div>
    </div>

    <!-- Content Section -->
    <div class="flex-1 mt-30 w-full relative z-10">
      <!-- Status Indicator -->
      <div ref="statusRef" class="flex items-center gap-3 mb-6 opacity-0">
        <div class="flex items-center gap-2 px-4 py-2 bg-slate-900/50 backdrop-blur-sm border border-blue-500/30 rounded-full">
          <Cpu class="w-3 h-3 md:w-4 md:h-4 text-blue-400 animate-spin" />
          <span class="text-blue-400 text-[0.63rem] md:text-sm font-medium">I'M READY</span>
        </div>
      </div>

      <!-- Main Heading -->
      <h1
        ref="headingRef"
        class="text-center lg:text-start sm:text-5xl text-4xl md:text-6xl lg:text-7xl font-bold mb-8 leading-tight opacity-0">
        <div class="mb-4">
          <div class="flex flex-row justify-center lg:justify-start">
            <span class="text-white mr-4 block">I am a</span>
            <div class="flex items-center gap-4">
              <span ref="typedElement" class="text-transparent bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600 bg-clip-text font-black"></span>
              <div class="w-1 h-10 sm:h-13 md:h-16 lg:h-20 bg-gradient-to-b from-cyan-400 to-blue-600 animate-pulse"></div>
            </div>
          </div>
          <span class="text-transparent bg-gradient-to-r from-emerald-400 to-cyan-500 bg-clip-text font-black block mt-2">
            Developer
          </span>
        </div>
      </h1>

      <!-- Description with Glitch Effect -->
      <div
        ref="paragraphRef"
        class="relative mb-12 opacity-0">
        <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/10 to-transparent rounded-lg blur-sm"></div>
        <div class="relative bg-slate-900/30 backdrop-blur-sm border border-slate-700/50 rounded-xl p-6 w-full lg:w-[50vw]">
          <div class="flex items-center gap-2 mb-4">
            <Terminal class="w-4 h-4 md:w-5 md:h-5 text-cyan-400" />
            <span class="text-cyan-400 text-xs md:text-sm font-mono">PROFILE.EXE</span>
          </div>
          <p class="text-slate-300 text-sm md:text-lg leading-relaxed font-light">
            <span class="text-emerald-400 font-mono">&gt;</span> Experienced electrical engineering graduate with a strong foundation in fullstack development  gained through two years of intensive hands-on training in various coding bootcamps. Eager to contribute as a proactive <span class="text-cyan-400 font-semibold">Fullstack Developer</span> in a dynamic environment, combining technical expertise with strong interpersonal and problem-solving abilities.

          </p>
          <div class="mt-4 flex flex-wrap gap-2">
            <span v-for="tech in ['React.js', 'Vue.js', 'Next.js', 'Laravel', 'Node.js', 'Spring Boot', 'React Native']" 
                  :key="tech"
                  class="px-3 py-1 bg-slate-800/50 border border-cyan-500/30 rounded-full text-[0.65rem] md:text-xs text-cyan-400 font-mono">
              {{ tech }}
            </span>
          </div>
        </div>
      </div>

      <!-- Action Buttons -->
      <div ref="buttonGroupRef" class="flex flex-col sm:flex-row items-start sm:items-center gap-6 mb-8 opacity-0">
        <!-- Primary CTA -->
        <div class="relative group">
          <div class="absolute -inset-1 bg-gradient-to-r from-cyan-500 via-blue-500 to-purple-600 rounded-xl blur opacity-75 group-hover:opacity-100 transition duration-1000 group-hover:duration-200 animate-tilt"></div>
          <a href="#contact" class="relative cursor-pointer flex items-center gap-3 px-8 py-4 bg-slate-900 border border-cyan-500/50 rounded-xl text-white font-semibold hover:bg-slate-800 transition-all duration-300 group-hover:scale-105">
            <Zap class="w-5 h-5 text-cyan-400" />
            <span class="">INITIATE CONTACT</span>
            <div class="w-2 h-2 bg-cyan-400 rounded-full animate-pulse"></div>
          </a>
        </div>

        <!-- Secondary CTA -->
        <div class="relative group">
          <a 
          href="https://drive.google.com/file/d/15Lhy_BMwvkSW8jxzpT_L-K_v1hwRoooH/view?usp=drive_link"
          class="flex items-center cursor-pointer gap-3 px-8 py-4 bg-transparent border-2 border-slate-600 rounded-xl text-slate-300 font-semibold hover:border-emerald-500 hover:text-emerald-400 transition-all duration-300 group-hover:scale-105">
            <FileText class="w-5 h-5" />
            <span>ACCESS RESUME</span>
            <ExternalLink class="w-4 h-4 opacity-50 group-hover:opacity-100" />
          </a>
        </div>
      </div>

      <!-- Social Links -->
      <div ref="socialRef" class="flex items-center gap-6 opacity-0">
        <span class="text-slate-500 text-sm font-mono">CONNECT_TO:</span>
        <div class="flex gap-4">
          <button
            v-for="social in socialLinks"
            :key="social.name"
            @click="$emit('open-social', social.name)"
            class="group relative p-3 bg-slate-900/50 backdrop-blur-sm border border-slate-700 rounded-xl hover:border-cyan-500/50 transition-all duration-300 hover:scale-110">
            <component :is="social.icon" class="w-5 h-5 text-slate-400 group-hover:text-cyan-400 transition-colors duration-300" />
            <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 to-blue-500/20 rounded-xl opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
          </button>
        </div>
      </div>
    </div>

    <!-- Avatar Section -->
    <div class="flex-shrink-0 mt-12 lg:mt-0 lg:mr-12">
      <div ref="imageGroupRef" class="relative opacity-0">
        <!-- Holographic Ring -->
        <div class="absolute inset-0 rounded-full border-2 border-cyan-400/30 animate-spin-slow"></div>
        <div class="absolute inset-2 rounded-full border border-blue-400/20 animate-pulse"></div>
        
        <!-- Main Avatar Container -->
        <div class="relative w-64 h-64 sm:w-80 sm:h-80 lg:w-96 lg:h-96 rounded-full overflow-hidden bg-gradient-to-br from-slate-900 via-slate-800 to-slate-900 border-4 border-transparent bg-clip-padding">
          <!-- Gradient Border -->
          <div class="absolute inset-0 rounded-full bg-gradient-to-r from-cyan-500 via-blue-500 to-purple-600 p-1">
            <div class="w-full h-full rounded-full bg-slate-900 overflow-hidden">
              <img
                src="../assets/avatar3.png?height=400&width=400"
                alt="Khoerul Fajri - Robot Developer"
                class="w-full h-120 object-cover filter contrast-110 brightness-90 hover:brightness-100 transition-all duration-500 hover:scale-105" />
            </div>
          </div>
          
          <!-- Scanning Line Effect -->
          <div class="absolute inset-0 rounded-full overflow-hidden">
            <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-scan"></div>
          </div>
          
          <!-- Corner Brackets -->
          <div class="absolute top-4 left-4 w-8 h-8 border-l-2 border-t-2 border-cyan-400"></div>
          <div class="absolute top-4 right-4 w-8 h-8 border-r-2 border-t-2 border-cyan-400"></div>
          <div class="absolute bottom-4 left-4 w-8 h-8 border-l-2 border-b-2 border-cyan-400"></div>
          <div class="absolute bottom-4 right-4 w-8 h-8 border-r-2 border-b-2 border-cyan-400"></div>
        </div>

        <!-- Status Indicators -->
        <div class="absolute -bottom-4 left-1/2 transform -translate-x-1/2 flex gap-2">
          <div class="w-3 h-3 bg-emerald-400 rounded-full animate-pulse"></div>
          <div class="w-3 h-3 bg-blue-400 rounded-full animate-pulse" style="animation-delay: 0.5s"></div>
          <div class="w-3 h-3 bg-purple-400 rounded-full animate-pulse" style="animation-delay: 1s"></div>
        </div>

        <!-- Floating Data Points -->
        <div class="absolute -top-8 -left-8 px-3 py-1 bg-slate-900/80 backdrop-blur-sm border border-cyan-500/30 rounded-lg text-xs text-cyan-400 font-mono animate-float">
          CPU: 98%
        </div>
        <div class="absolute -top-4 -right-12 px-3 py-1 bg-slate-900/80 backdrop-blur-sm border border-emerald-500/30 rounded-lg text-xs text-emerald-400 font-mono animate-float" style="animation-delay: 1s">
          NEURAL: ACTIVE
        </div>
        <div class="absolute -bottom-8 -right-8 px-3 py-1 bg-slate-900/80 backdrop-blur-sm border border-purple-500/30 rounded-lg text-xs text-purple-400 font-mono animate-float" style="animation-delay: 2s">
          STATUS: READY
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import Typed from "typed.js";
import { 
  Linkedin, Github, MessageCircle, Cpu, Terminal, 
  Zap, FileText, ExternalLink 
} from "lucide-vue-next";

gsap.registerPlugin(ScrollTrigger);

const mainRef = ref(null);
const headingRef = ref(null);
const paragraphRef = ref(null);
const buttonGroupRef = ref(null);
const imageGroupRef = ref(null);
const statusRef = ref(null);
const socialRef = ref(null);
const typedElement = ref(null);

const socialLinks = [
  { name: 'linkedin', icon: Linkedin },
  { name: 'github', icon: Github },
  { name: 'whatsapp', icon: MessageCircle }
];

onMounted(() => {
  const animate = () => {
    // Status indicators
    gsap.fromTo(statusRef.value, 
      {opacity: 0, y: -20},
      {opacity: 1, y: 0, duration: 0.8, ease: "power2.out"}
    );

    // Main heading with stagger
    gsap.fromTo(headingRef.value, 
      {opacity: 0, y: 50, scale: 0.9},
      {opacity: 1, y: 0, scale: 1, duration: 1.2, ease: "back.out(1.7)", delay: 0.2}
    );

    // Description with slide effect
    gsap.fromTo(paragraphRef.value, 
      {opacity: 0, x: -100, rotationY: -15},
      {opacity: 1, x: 0, rotationY: 0, duration: 1, ease: "power3.out", delay: 0.5}
    );

    // Button group with bounce
    gsap.fromTo(buttonGroupRef.value, 
      {opacity: 0, y: 30, scale: 0.8},
      {opacity: 1, y: 0, scale: 1, duration: 0.8, ease: "back.out(1.7)", delay: 0.7}
    );

    // Social links
    gsap.fromTo(socialRef.value, 
      {opacity: 0, x: -50},
      {opacity: 1, x: 0, duration: 0.8, ease: "power2.out", delay: 0.9}
    );

    // Avatar with complex animation
    gsap.fromTo(imageGroupRef.value, 
      {opacity: 0, y: 100, scale: 0.5, rotation: -20},
      {opacity: 1, y: 0, scale: 1, rotation: 0, duration: 1.5, ease: "back.out(1.7)", delay: 0.8}
    );
  };

  ScrollTrigger.create({ 
    trigger: mainRef.value,
    start: "top 80%", 
    onEnter: animate,
    onEnterBack: animate,
  });

  // Enhanced Typed.js configuration
  new Typed(typedElement.value, {
    strings: [
      'Frontend', 
      'Backend', 
      'Mobile',
      'Fullstack'
    ],
    backSpeed: 30,
    typeSpeed: 60,
    loop: true,
    showCursor: false,
    smartBackspace: true,
  });
});
</script>

<style scoped>
/* Enhanced Animations */
@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-15px) rotate(5deg); }
}

@keyframes scan {
  0% { transform: translateY(-100%); opacity: 0; }
  50% { opacity: 1; }
  100% { transform: translateY(400%); opacity: 0; }
}

@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes tilt {
  0%, 50%, 100% { transform: rotate(0deg); }
  25% { transform: rotate(1deg); }
  75% { transform: rotate(-1deg); }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-scan {
  animation: scan 3s linear infinite;
}

.animate-spin-slow {
  animation: spin-slow 20s linear infinite;
}

.animate-tilt {
  animation: tilt 10s infinite linear;
}

/* Glitch Effect */
.glitch {
  position: relative;
}

.glitch::before,
.glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.glitch::before {
  animation: glitch-1 0.5s infinite;
  color: #00ffff;
  z-index: -1;
}

.glitch::after {
  animation: glitch-2 0.5s infinite;
  color: #ff00ff;
  z-index: -2;
}

@keyframes glitch-1 {
  0%, 100% { transform: translate(0); }
  20% { transform: translate(-2px, 2px); }
  40% { transform: translate(-2px, -2px); }
  60% { transform: translate(2px, 2px); }
  80% { transform: translate(2px, -2px); }
}

@keyframes glitch-2 {
  0%, 100% { transform: translate(0); }
  20% { transform: translate(2px, 2px); }
  40% { transform: translate(2px, -2px); }
  60% { transform: translate(-2px, 2px); }
  80% { transform: translate(-2px, -2px); }
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #1e293b;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #06b6d4, #3b82f6);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #0891b2, #2563eb);
}
</style>