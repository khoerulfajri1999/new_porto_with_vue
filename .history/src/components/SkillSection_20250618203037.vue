<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { 
  // Tech Stack Icons
  Code2, Server, Terminal, Layers, Globe,
  FileCode, Palette, Zap, Monitor, GitBranch,
  Cloud, Braces, Settings, Container, Cpu,
  Database, Smartphone, Shield, Key, Wifi,
  // Soft Skills Icons
  Users, MessageCircle, Target, Clock, Lightbulb
} from "lucide-vue-next";

// Register GSAP plugins
gsap.registerPlugin(ScrollTrigger);

// Refs for animations
const mainContainer = ref(null);
const titleRef = ref(null);
const descriptionRef = ref(null);
const legendRef = ref(null);
const counterRef = ref(null);
const particlesRef = ref(null);

// State untuk tombol kiri (20 buttons)
const isVisibleLeft = ref(false);
const circleBtnLeft = ref(null);
const circleButtonsLeft = ref([]);

// State untuk tombol kanan (5 buttons)
const isVisibleRight = ref(false);
const circleBtnRight = ref(null);
const circleButtonsRight = ref([]);

// Data untuk tombol kiri (20 tech stack buttons)
const buttonIconsLeft = [
  Code2, Server, Terminal, Layers, Globe,
  FileCode, Palette, Zap, Monitor, GitBranch,
  Cloud, Braces, Settings, Container, Cpu,
  Database, Smartphone, Database, Database, Shield
];

const buttonLabelsLeft = [
  'React JS', 'Node JS', 'Express JS', 'Vue JS', 'Next JS',
  'Laravel', 'Bootstrap', 'Tailwind CSS', 'Material UI', 'GitHub',
  'Firebase', 'REST API', 'Spring Boot', 'Docker', 'Microservice',
  'Redis', 'React Native', 'MySQL', 'PostgreSQL', 'JWT'
];

// Data untuk tombol kanan (5 soft skills buttons)
const buttonIconsRight = [Users, MessageCircle, Target, Clock, Lightbulb];
const buttonLabelsRight = ['Team Work', 'Communication', 'Problem Solving', 'Time Management', 'Creative Thinking'];

// Functions untuk tombol kiri
const toggleButtonsLeft = () => {
  if (isVisibleLeft.value) {
    hideButtonsLeft();
  } else {
    showButtonsLeft();
  }
};

const getResponsiveRadiusButtonLeft = () => {
  if (window.matchMedia("(min-width: 1024px)").matches) {
    return 230; // lg
  } else if (window.matchMedia("(min-width: 768px)").matches) {
    return 150; // md
  } else {
    return 120; // sm
  }
};

const showButtonsLeft = () => {
  isVisibleLeft.value = true;
  if (circleButtonsLeft.value.length === 0) return; 

  circleButtonsLeft.value.forEach((el, i) => {
    if (el) {
      const angle = (i * 2 * Math.PI) / 20;
      const radius = getResponsiveRadiusButtonLeft();
      
      gsap.fromTo(
        el,
        { x: 0, y: 0, opacity: 0, scale: 0, rotation: -180 },
        {
          x: Math.cos(angle) * radius,
          y: Math.sin(angle) * radius,
          opacity: 1,
          scale: 1,
          rotation: 0,
          duration: 1,
          ease: "back.out(1.7)",
          delay: 0.05 * i,
        }
      );
    }
  });
};

const hideButtonsLeft = () => {
  if (circleButtonsLeft.value.length === 0) {
    isVisibleLeft.value = false;
    return;
  }

  circleButtonsLeft.value.forEach((el, i) => {
    if (el) {
      gsap.to(el, {
        x: 0,
        y: 0,
        opacity: 0,
        scale: 0,
        rotation: 180,
        duration: 0.6,
        ease: "back.in(1.7)",
        delay: 0.03 * (circleButtonsLeft.value.length - 1 - i),
        onComplete: () => {
          if (i === circleButtonsLeft.value.length - 1) {
            isVisibleLeft.value = false;
          }
        },
      });
    }
  });
};

// Functions untuk tombol kanan
const toggleButtonsRight = () => {
  if (isVisibleRight.value) {
    hideButtonsRight();
  } else {
    showButtonsRight();
  }
};

const getResponsiveRadiusButtonRight = () => {
  if (window.matchMedia("(min-width: 1024px)").matches) {
    return 150; // lg
  } else if (window.matchMedia("(min-width: 768px)").matches) {
    return 130; // md
  } else {
    return 100; // sm
  }
};

const showButtonsRight = () => {
  isVisibleRight.value = true;
  if (circleButtonsRight.value.length === 0) return; 

  circleButtonsRight.value.forEach((el, i) => {
    if (el) {
      const angle = (i * 2 * Math.PI) / 5;
      const radius = getResponsiveRadiusButtonRight();
      
      gsap.fromTo(
        el,
        { x: 0, y: 0, opacity: 0, scale: 0, rotation: -180 },
        {
          x: Math.cos(angle) * radius,
          y: Math.sin(angle) * radius,
          opacity: 1,
          scale: 1,
          rotation: 0,
          duration: 1,
          ease: "back.out(1.7)",
          delay: 0.1 * i,
        }
      );
    }
  });
};

const hideButtonsRight = () => {
  if (circleButtonsRight.value.length === 0) {
    isVisibleRight.value = false;
    return;
  }

  circleButtonsRight.value.forEach((el, i) => {
    if (el) {
      gsap.to(el, {
        x: 0,
        y: 0,
        opacity: 0,
        scale: 0,
        rotation: 180,
        duration: 0.6,
        ease: "back.in(1.7)",
        delay: 0.05 * (circleButtonsRight.value.length - 1 - i),
        onComplete: () => {
          if (i === circleButtonsRight.value.length - 1) {
            isVisibleRight.value = false;
          }
        },
      });
    }
  });
};

const handleSubButtonClickLeft = (index) => {
  console.log(`Tech Stack ${index + 1} activated: ${buttonLabelsLeft[index]}`);
};

const handleSubButtonClickRight = (index) => {
  console.log(`Soft Skill ${index + 1} activated: ${buttonLabelsRight[index]}`);
};

// Animation setup
onMounted(() => {
  // Set initial states
  gsap.set([titleRef.value, descriptionRef.value, circleBtnLeft.value, circleBtnRight.value, legendRef.value, counterRef.value], {
    opacity: 0,
    y: 100
  });

  gsap.set(particlesRef.value?.children || [], {
    opacity: 0,
    scale: 0
  });

  // Create ScrollTrigger animation
  ScrollTrigger.create({
    trigger: mainContainer.value,
    start: "top 80%",
    end: "bottom 20%",
    onEnter: () => {
      // Create timeline for coordinated animations
      const tl = gsap.timeline();

      // 1. Title animation with typewriter effect
      tl.fromTo(titleRef.value,
        { opacity: 0, y: -50, scale: 0.8 },
        { 
          opacity: 1, 
          y: 0, 
          scale: 1,
          duration: 1.2, 
          ease: "back.out(1.7)",
        }
      )

      // 2. Description with slide and fade
      .fromTo(descriptionRef.value,
        { opacity: 0, x: -100, rotationY: -15 },
        { 
          opacity: 1, 
          x: 0, 
          rotationY: 0,
          duration: 1, 
          ease: "power3.out" 
        }, "-=0.8"
      )

      // 3. Left button with bounce and rotation
      .fromTo(circleBtnLeft.value,
        { opacity: 0, y: 100, scale: 0.5, rotation: -45 },
        { 
          opacity: 1, 
          y: 0, 
          scale: 1, 
          rotation: 0,
          duration: 1.2, 
          ease: "elastic.out(1, 0.5)" 
        }, "-=0.6"
      )

      // 4. Right button with different timing
      .fromTo(circleBtnRight.value,
        { opacity: 0, y: 100, scale: 0.5, rotation: 45 },
        { 
          opacity: 1, 
          y: 0, 
          scale: 1, 
          rotation: 0,
          duration: 1.2, 
          ease: "elastic.out(1, 0.5)" 
        }, "-=1"
      )

      // 5. Legend with slide from left
      .fromTo(legendRef.value,
        { opacity: 0, x: -200, rotationY: -30 },
        { 
          opacity: 1, 
          x: 0, 
          rotationY: 0,
          duration: 1, 
          ease: "power2.out" 
        }, "-=0.8"
      )

      // 6. Counter with slide from bottom
      .fromTo(counterRef.value,
        { opacity: 0, y: 50, scale: 0.8 },
        { 
          opacity: 1, 
          y: 0, 
          scale: 1,
          duration: 0.8, 
          ease: "back.out(1.7)" 
        }, "-=0.6"
      );

      // 7. Animate particles separately with stagger
      if (particlesRef.value?.children) {
        gsap.fromTo(particlesRef.value.children,
          { opacity: 0, scale: 0, rotation: -180 },
          { 
            opacity: 1, 
            scale: 1, 
            rotation: 0,
            duration: 0.8, 
            ease: "back.out(1.7)",
            stagger: 0.1,
            delay: 0.5
          }
        );
      }
    },
    onLeave: () => {
      // Optional: animate out when leaving viewport
      gsap.to([titleRef.value, descriptionRef.value, circleBtnLeft.value, circleBtnRight.value, legendRef.value, counterRef.value], {
        opacity: 0.3,
        scale: 0.95,
        duration: 0.5,
        ease: "power2.out"
      });
    },
    onEnterBack: () => {
      // Animate back in when scrolling up
      gsap.to([titleRef.value, descriptionRef.value, circleBtnLeft.value, circleBtnRight.value, legendRef.value, counterRef.value], {
        opacity: 1,
        scale: 1,
        duration: 0.8,
        ease: "power2.out"
      });
    }
  });
});
</script>

<template>
  <div 
    ref="mainContainer"
    class=" flex items-center justify-center min-h-[90vh] relative bg-gradient-to-br from-[#030415] via-[#1E0B38] to-[#030415] overflow-hidden"
    id="about"
    >

    <!-- Background grid pattern -->
    <div class="absolute inset-0 bg-[linear-gradient(rgba(120,119,198,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(120,119,198,0.1)_1px,transparent_1px)] bg-[size:50px_50px] animate-pulse"></div>
    
    <!-- Container untuk 2 tombol -->
    <div class=" flex flex-col mt-70 sm:mt-0 sm:flex-row items-center gap-15 md:gap-10 lg:gap-70 relative z-10">
      
      <!-- Tombol Kiri (20 tech stack buttons) -->
      <div
        ref="circleBtnLeft"
        class="relative z-20 cursor-pointer group duration-1000 animate-float"
        @click="toggleButtonsLeft"
      >
        <div class="relative bg-gradient-to-r from-cyan-500 via-blue-500 to-blue-600 rounded-full p-1 shadow-2xl hover:shadow-cyan-500/25 transition-all duration-300 hover:scale-110">
          <div class="bg-slate-900 rounded-full p-3 md:p-6 relative overflow-hidden">
            <!-- Animated background -->
            <div class="absolute inset-0 bg-gradient-to-r from-cyan-500/20 via-blue-500/20 to-purple-600/20 rounded-full animate-pulse"></div>
            
            <!-- Scanning line effect -->
            <div class="absolute inset-0 rounded-full overflow-hidden">
              <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-scan"></div>
            </div>
            
            <!-- Tech Stack icon and text -->
            <div class="relative flex flex-col items-center gap-2 text-white">
              <Code2 class="w-5 h-5 md:w-6 md:h-6 lg:w-8 lg:h-8 text-cyan-400 group-hover:text-cyan-300 transition-colors duration-300" :class="{ 'animate-spin': isVisibleLeft }" />
              <span class="font-bold text-[0.7rem] md:text-[0.73rem] lg:text-sm tracking-wide text-center">TECHNICAL<br>SKILLS</span>
            </div>
            
            <!-- Glowing ring effect -->
            <div class="absolute inset-0 rounded-full border-2 border-cyan-400/30 group-hover:border-cyan-400/60 transition-all duration-300 animate-pulse-ring"></div>
          </div>
        </div>

        <!-- Sub buttons kiri (20 tech stack buttons) -->
        <button
          v-for="(icon, index) in buttonIconsLeft"
          :key="`left-${index}`"
          ref="circleButtonsLeft"
          v-show="isVisibleLeft"
          @click.stop="handleSubButtonClickLeft(index)"
          class="absolute bottom-7 left-7  md:bottom-8 md:left-8 w-9 h-9 md:w-14 md:h-14 rounded-full bg-gradient-to-r from-slate-800 to-slate-700 hover:from-cyan-600 hover:to-blue-600 shadow-lg border border-cyan-500/30 hover:border-cyan-400 transform translate-x-0 translate-y-0 transition-all duration-300 hover:scale-110 group/sub"
          :title="buttonLabelsLeft[index]"
        >
          <div class="flex items-center justify-center w-full h-full">
            <component 
              :is="icon" 
              class="w-4 h-4 md:w-6 md:h-6 text-cyan-400 group-hover/sub:text-white transition-colors duration-300" 
            />
          </div>
          
          <!-- Glowing effect on hover -->
          <div class="absolute inset-0 rounded-full bg-cyan-400/20 opacity-0 group-hover/sub:opacity-100 transition-opacity duration-300"></div>
          
          <!-- Tooltip -->
          <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-slate-800 text-cyan-400 text-xs px-3 py-2 rounded opacity-0 group-hover/sub:opacity-100 transition-opacity duration-300 whitespace-nowrap border border-cyan-500/30 z-50">
            {{ buttonLabelsLeft[index] }}
          </div>
        </button>
      </div>

      <!-- Tombol Kanan (5 soft skills buttons) -->
      <div
        ref="circleBtnRight"
        class="relative z-19 cursor-pointer group duration-1000 animate-float opacity-0"
        @click="toggleButtonsRight"
        style="animation-delay: 0.5s"
      >
        <div class="relative bg-gradient-to-r from-emerald-500 via-green-500 to-teal-600 rounded-full p-1 shadow-2xl hover:shadow-emerald-500/25 transition-all duration-300 hover:scale-110">
          <div class="bg-slate-900 rounded-full p-3 md:p-6 relative overflow-hidden">
            <!-- Animated background -->
            <div class="absolute inset-0 bg-gradient-to-r from-emerald-500/20 via-green-500/20 to-teal-600/20 rounded-full animate-pulse"></div>
            
            <!-- Scanning line effect -->
            <div class="absolute inset-0 rounded-full overflow-hidden">
              <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-emerald-400 to-transparent animate-scan" style="animation-delay: 1s"></div>
            </div>
            
            <!-- Soft Skills icon and text -->
            <div class="relative flex flex-col items-center gap-2 text-white">
              <Users class="w-5 h-5 md:w-6 md:h-6 lg:w-8 lg:h-8 text-emerald-400 group-hover:text-emerald-300 transition-colors duration-300" :class="{ 'animate-bounce': isVisibleRight }" />
              <span class="font-bold text-[0.7rem] md:text-[0.73rem] lg:text-sm tracking-wide w-15 md:w-18 lg:w-20 text-center">SOFT<br>SKILLS</span>
            </div>
             
            <!-- Glowing ring effect -->
            <div class="absolute inset-0 rounded-full border-2 border-emerald-400/30 group-hover:border-emerald-400/60 transition-all duration-300 animate-pulse-ring"></div>
          </div>
        </div>

        <!-- Sub buttons kanan (5 soft skills buttons) -->
        <button
          v-for="(icon, index) in buttonIconsRight"
          :key="`right-${index}`"
          ref="circleButtonsRight"
          v-show="isVisibleRight"
          @click.stop="handleSubButtonClickRight(index)"
          class="absolute bottom-9 left-6 w-16 h-16 rounded-full bg-gradient-to-r from-slate-800 to-slate-700 hover:from-emerald-600 hover:to-green-600 shadow-lg border border-emerald-500/30 hover:border-emerald-400 transform translate-x-0 translate-y-0 opacity-0 transition-all duration-300 hover:scale-110 group/sub z-10"
          :title="buttonLabelsRight[index]"
        >
          <div class="flex items-center justify-center w-full h-full">
            <component 
              :is="icon" 
              class="w-7 h-7 text-emerald-400 group-hover/sub:text-white transition-colors duration-300" 
            />
          </div>
          
          <!-- Glowing effect on hover -->
          <div class="absolute inset-0 rounded-full bg-emerald-400/20 opacity-0 group-hover/sub:opacity-100 transition-opacity duration-300"></div>
          
          <!-- Tooltip -->
          <div class="absolute -top-12 left-1/2 transform -translate-x-1/2 bg-slate-800 text-emerald-400 text-xs px-3 py-2 rounded opacity-0 group-hover/sub:opacity-100 transition-opacity duration-300 whitespace-nowrap border border-emerald-500/30 z-50">
            {{ buttonLabelsRight[index] }}
          </div>
        </button>
      </div>
    </div>

    <!-- Floating particles effect -->
    <div ref="particlesRef" class="absolute inset-0 overflow-hidden pointer-events-none">
      <div class="absolute top-1/4 left-1/4 w-2 h-2 bg-cyan-400 rounded-full animate-ping opacity-20"></div>
      <div class="absolute top-3/4 right-1/4 w-1 h-1 bg-purple-400 rounded-full animate-pulse opacity-30"></div>
      <div class="absolute top-1/2 left-1/6 w-1.5 h-1.5 bg-blue-400 rounded-full animate-bounce opacity-25"></div>
      <div class="absolute bottom-1/4 right-1/3 w-2 h-2 bg-emerald-300 rounded-full animate-ping opacity-15"></div>
      <div class="absolute top-1/3 right-1/6 w-1 h-1 bg-green-300 rounded-full animate-pulse opacity-20"></div>
      <div class="absolute bottom-1/3 left-1/4 w-1.5 h-1.5 bg-teal-300 rounded-full animate-bounce opacity-25"></div>
    </div>

    <!-- Title -->
    <div ref="titleRef" class="absolute top-16 left-1/2 transform -translate-x-1/2 text-center w-110 sm:w-full md:w-200  lg:w-250 opacity-0">
      <h1 class="sm:text-5xl text-4xl md:text-6xl font-bold bg-gradient-to-r from-cyan-400 via-blue-400 to-emerald-400 bg-clip-text text-transparent relative">
        About Me.
        <div class="absolute -inset-1 bg-gradient-to-r from-cyan-400/20 via-blue-400/20 to-emerald-400/20 blur-lg rounded-lg"></div>
      </h1>
      <div ref="descriptionRef" class="opacity-0">
        <p class="text-slate-300 -mt-16 text-lg leading-relaxed tracking-wide px-8">
          Experienced software developer specializing in web and mobile application development. 
          Proficient in modern technologies including <span class="text-cyan-400 font-semibold">React.js</span>, 
          <span class="text-cyan-300 font-semibold">Vue.js</span>, 
          <span class="text-blue-300 font-semibold">Next.js</span>,
          <span class="text-purple-400 font-semibold">Laravel</span>,  
          <span class="text-blue-400 font-semibold">Spring Boot</span>, and 
          <span class="text-emerald-400 font-semibold">React Native</span>. 
          Strong team collaboration skills with excellent communication abilities. 
          Committed to delivering high-quality software solutions that exceed client expectations.
        </p>
      </div>
    </div>

    <!-- Function counter -->
    <div ref="counterRef" class="absolute bottom-16 left-1/2 transform -translate-x-1/2 text-center opacity-0">
      <div class="flex gap-6">
        <div class="bg-slate-800/60 backdrop-blur-sm border border-cyan-500/30 rounded-lg px-6 py-3 hover:bg-slate-700/60 transition-colors duration-300 hover:scale-105">
          <span class="text-cyan-400 text-sm font-medium">
            {{ isVisibleLeft ? '20 Technical Skills Active' : '20 Technical Skills Ready' }}
          </span>
        </div>
        <div class="bg-slate-800/60 backdrop-blur-sm border border-emerald-500/30 rounded-lg px-6 py-3 hover:bg-slate-700/60 transition-colors duration-300 hover:scale-105">
          <span class="text-emerald-400 text-sm font-medium">
            {{ isVisibleRight ? '5 Soft Skills Active' : '5 Soft Skills Ready' }}
          </span>
        </div>
      </div>
    </div>

    <!-- Tech Stack Categories Legend -->
    <div ref="legendRef" class="absolute top-180 sm:top-1/2 left-8 transform -translate-y-1/2 opacity-0">
      <div class="bg-slate-800/80 text-xs sm:text-[0.9rem] backdrop-blur-sm border border-cyan-500/30 rounded-lg p-4 max-w-sm hover:scale-105 transition-transform duration-300">
        <h3 class="text-cyan-400 font-bold text-lg mb-3 flex items-center gap-2">
          <div class="w-2 h-2 bg-cyan-400 rounded-full animate-pulse"></div>
          Tech Stack Categories:
        </h3>
        <div class="text-md text-slate-300 space-y-2">
          <div class="flex items-center gap-2 hover:text-blue-400 transition-colors duration-200">
            <div class="w-3 h-3 bg-blue-400 rounded-full animate-pulse"></div>
            <span>Frontend: React, Vue, Next.js</span>
          </div>
          <div class="flex items-center gap-2 hover:text-green-400 transition-colors duration-200">
            <div class="w-3 h-3 bg-green-400 rounded-full animate-pulse" style="animation-delay: 0.2s"></div>
            <span>Backend: Node.js, Express, Laravel</span>
          </div>
          <div class="flex items-center gap-2 hover:text-yellow-400 transition-colors duration-200">
            <div class="w-3 h-3 bg-yellow-400 rounded-full animate-pulse" style="animation-delay: 0.4s"></div>
            <span>Database: MySQL, PostgreSQL, Redis</span>
          </div>
          <div class="flex items-center gap-2 hover:text-purple-400 transition-colors duration-200">
            <div class="w-3 h-3 bg-purple-400 rounded-full animate-pulse" style="animation-delay: 0.6s"></div>
            <span>DevOps: Docker, Microservices</span>
          </div>
          <div class="flex items-center gap-2 hover:text-pink-400 transition-colors duration-200">
            <div class="w-3 h-3 bg-pink-400 rounded-full animate-pulse" style="animation-delay: 0.8s"></div>
            <span>Mobile: React Native</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Enhanced Animations */
@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-15px) rotate(2deg); }
}

@keyframes scan {
  0% { transform: translateY(-100%) scaleX(0); opacity: 0; }
  50% { opacity: 1; scaleX: (1); }
  100% { transform: translateY(400%) scaleX(0); opacity: 0; }
}

@keyframes pulse-ring {
  0%, 100% { 
    border-color: rgba(6, 182, 212, 0.3);
    transform: scale(1);
  }
  50% { 
    border-color: rgba(6, 182, 212, 0.8);
    transform: scale(1.05);
  }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-scan {
  animation: scan 4s linear infinite;
}

.animate-pulse-ring {
  animation: pulse-ring 2s ease-in-out infinite;
}

/* Custom scrollbar for modern look */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #1e293b;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(to bottom, #06b6d4, #10b981);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(to bottom, #0891b2, #059669);
}

/* Glitch effect for enhanced visual appeal */
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
  20% { transform: translate(-1px, 1px); }
  40% { transform: translate(-1px, -1px); }
  60% { transform: translate(1px, 1px); }
  80% { transform: translate(1px, -1px); }
}

@keyframes glitch-2 {
  0%, 100% { transform: translate(0); }
  20% { transform: translate(1px, 1px); }
  40% { transform: translate(1px, -1px); }
  60% { transform: translate(-1px, 1px); }
  80% { transform: translate(-1px, -1px); }
}
</style>