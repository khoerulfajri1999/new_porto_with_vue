<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { 
  ExternalLink, Github, Code2, Smartphone, 
  Globe, Database, Zap, Monitor, 
  Rocket, Star, Eye, Heart,
  Calendar, User, Tag
} from "lucide-vue-next";
import porto1 from "../assets/porto1.png";
import porto2 from "../assets/porto2.png";
import porto3 from "../assets/porto3.png";
import porto4 from "../assets/porto4.png";
import porto5 from "../assets/porto5.png";
import porto6 from "../assets/porto6.png";

const portfolioCards = ref([]);
const titleRef = ref(null);
const subtitleRef = ref(null);

// Portfolio data
const portfolioData = [
  {
    id: 1,
    title: "Bantu-In (Volunteering App)",
    description: "This application connects volunteer seekers with volunteers through three user roles: admin, volunteer, and seeker, built with Java Spring Boot, React JS, React Native, JWT, and Material UI, volunteers can search and apply for verified tasks with map access and receive reviews upon completion, seekers can create tasks that require admin approval and payment before being available to volunteers, while admins verify all user accounts, approve tasks, view detailed task information including distance, and access monthly and yearly registration and income analytics charts.",
    image: porto1,
    technologies: ["React JS", "Spring Boot", "React Native", "JWT", "Redux", "Material UI", "PostgreeSql"],
    category: "Web Application & Mobile Application",
    status: "Completed",
    year: "2025",
    github: "https://docs.google.com/document/d/1_b0vLrHIREelhqPdR3OLuBTFqg2n02zixcsVChZgNo4/edit?usp=sharing",
    demo: "https://demo.com",
    color: "from-blue-500 to-cyan-500"
  },
  {
    id: 2,
    title: "My Event",
    description: "This event management application is built using Node js, Express.js, Sequelize, Mysql, Vue Js, and Pinia, featuring user management (authentication, profile, photo upload, roles, status), event and ticket management, ticket purchase transactions with status tracking and automatic QR code attendance, as well as a responsive dashboard for event organizers with full integration between the frontend and backend.",
    image: porto2,
    technologies: ["Node JS", "Express JS", "Vue JS", "Pinia", "Mysql"],
    category: "Web Application",
    status: "Completed",
    year: "2025",
    github: "https://docs.google.com/document/d/1p4zdt68E4uQq4tVRceIDHa5Cq32ZuCKZQwDhKLeHvRI/edit?usp=sharing",
    demo: "https://demo.com",
    color: "from-emerald-500 to-teal-500"
  },
  {
    id: 3,
    title: "Pure",
    description: "Pure is a web based Point of Sale (POS) application built with Laravel and Livewire, featuring a comprehensive store menu, customer and transaction management including product categorization, customer data tracking, real time financial monitoring, receipt printing and monthly Excel exports, powered by a MySQL database.",
    image: porto3,
    technologies: ["Laravel", "Livewire", "Mysql"],
    category: "Web Application",
    status: "Completed",
    year: "2025",
    github: "https://github.com/khoerulfajri1999/pure-POS",
    demo: "https://demo.com",
    color: "from-purple-500 to-pink-500"
  },
  {
    id: 4,
    title: "E-Commerce",
    description: "This ecommerce application, built with React JS and Spring Boot using JWT for security and Midtrans as the payment gateway, features separate user and admin views, the admin view provides product stock analysis, top 5 product insights, and sales reports filterable by month, while the user view includes cart, checkout, invoice, and order tracking through various statuses such as draft, payment, packing, shipping, completed, and canceled, all supported by an intuitive user interface and a streamlined checkout system for accurate total calculation, styled with PrimeReact.",
    image: porto4,
    technologies: ["Spring Boot", "React JS", "JWT", "Midtrans", "Primereact", "PostgreeSql"],
    category: "Web Application",
    status: "Completed",
    year: "2025",
    github: "https://docs.google.com/document/d/1PtRNoEQARc92zEsaYWehe8DGG8iltQwUoe5SVvQOrNU/edit?usp=sharing",
    demo: "https://demo.com",
    color: "from-orange-500 to-red-500"
  },
  {
    id: 5,
    title: "Chatting App",
    description: "ChatApp is an authentication based chat application built with React Native and Firebase, featuring sign up, sign in, forgot password recovery, and sign out using Firebase Authentication, a responsive UI styled with Nativewind and react native responsive screen, data storage in Firestore with structured collections for users, chat requests, and messages, and profile photo uploads via Cloudinary using expo image picker.",
    image: porto5,
    technologies: ["React Native", "Firebase"],
    category: "Mobile Application",
    status: "Completed",
    year: "2025",
    github: "https://github.com/khoerulfajri1999/chatApp",
    demo: "https://demo.com",
    color: "from-indigo-500 to-blue-500"
  },
  {
    id: 6,
    title: "Toko Tsunny",
    description: "Toko Tsunny is a mobile based transaction management application built with React Native and connected to a Go backend using Docker, MySQL as the main database, and Redis for caching, enabling users to manage products, categories, and daily transactions with role-based access where admins can record income and expenses with product details, display time-based graphs, export monthly reports in PDF format, while users can view products and contact the admin via WhatsApp.",
    image: porto6,
    technologies: ["React Native", "Golang", "Docker", "Redis", "Mysql"],
    category: "Mobile Application",
    status: "Completed",
    year: "2025",
    github: "https://docs.google.com/document/d/1vds2T4a9izuYHLnSmEe7gQJdKpojSan4ym1R2UZ3xLs/edit?usp=sharing",
    demo: "https://demo.com",
    color: "from-yellow-500 to-orange-500"
  }
];

const getTechIcon = (tech) => {
  const iconMap = {
    'React JS': Code2,
    'Node JS': Database,
    'Vue JS': Zap,
    'Next JS': Globe,
    'React Native': Smartphone,
    'Spring Boot': Database,
    'MongoDB': Database,
    'PostgreSQL': Database,
    'Firebase': Database,
    'Docker': Monitor,
    'AWS': Globe,
    'Python': Code2,
    'default': Code2
  };
  return iconMap[tech] || iconMap.default;
};

const getStatusColor = (status) => {
  return status === 'Completed' ? 'text-emerald-400' : 'text-yellow-400';
};

const handleCardClick = (project) => {
  console.log(`Opening project: ${project.title}`);
};

const handleGithubClick = (url, event) => {
  event.stopPropagation();
  window.open(url, '_blank');
};

const handleDemoClick = (url, event) => {
  event.stopPropagation();
  window.open(url, '_blank');
};

onMounted(() => {
  // Animate title and subtitle
  gsap.fromTo(titleRef.value, 
    { y: -50, opacity: 0 },
    { y: 0, opacity: 1, duration: 1, ease: "power3.out" }
  );
  
  gsap.fromTo(subtitleRef.value,
    { y: -30, opacity: 0 },
    { y: 0, opacity: 1, duration: 1, delay: 0.3, ease: "power3.out" }
  );

  // Animate portfolio cards
  gsap.fromTo(portfolioCards.value,
    { y: 100, opacity: 0, scale: 0.8 },
    { 
      y: 0, 
      opacity: 1, 
      scale: 1,
      duration: 0.8,
      delay: 0.6,
      stagger: 0.2,
      ease: "back.out(1.7)"
    }
  );
});
</script>

<template>
  <div 
  class="min-h-screen relative bg-gradient-to-tr from-[#030415] via-[#1E0B38] to-[#030415] overflow-hidden"
  id="project"
  >
    <div class="absolute inset-0 bg-[linear-gradient(rgba(120,119,198,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(120,119,198,0.1)_1px,transparent_1px)] bg-[size:50px_50px]"></div>
    
    <!-- Animated Background Elements -->
    <div class="absolute inset-0">

      <!-- Floating geometric shapes -->
      <div class="absolute top-20 left-20 w-4 h-4 bg-cyan-400/20 rotate-45 animate-pulse"></div>
      <div class="absolute top-40 right-32 w-6 h-6 bg-emerald-400/20 rounded-full animate-bounce"></div>
      <div class="absolute bottom-32 left-40 w-3 h-3 bg-purple-400/20 rotate-12 animate-ping"></div>
      <div class="absolute bottom-20 right-20 w-5 h-5 bg-blue-400/20 rounded-full animate-pulse"></div>
      
      <!-- Glowing orbs -->
      <div class="absolute top-1/4 left-1/4 w-32 h-32 bg-gradient-to-r from-cyan-500/10 to-blue-500/10 rounded-full blur-xl animate-pulse"></div>
      <div class="absolute bottom-1/4 right-1/4 w-40 h-40 bg-gradient-to-r from-emerald-500/10 to-teal-500/10 rounded-full blur-xl animate-pulse"></div>
    </div>

    <div class="relative z-10 container mx-auto px-6 py-16">
      <!-- Header Section -->
      <div class="text-center mb-16">
        <h1 
          ref="titleRef"
          class="text-6xl font-bold bg-gradient-to-r from-cyan-400 via-blue-400 to-emerald-400 bg-clip-text text-transparent mb-4"
        >
          Portfolio Projects
        </h1>
        <p 
          ref="subtitleRef"
          class="text-lg text-slate-300 max-w-3xl mx-auto leading-relaxed"
        >
          Showcasing innovative web and mobile applications built with cutting-edge technologies. 
          Each project represents a unique solution crafted with precision and creativity.
        </p>
      </div>

      <!-- Portfolio Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 max-w-7xl mx-auto">
        <div
          v-for="project in portfolioData"
          :key="project.id"
          ref="portfolioCards"
          @click="handleCardClick(project)"
          class="group relative bg-slate-900/50 backdrop-blur-sm border border-slate-700/50 rounded-2xl overflow-hidden cursor-pointer transform transition-all duration-500 hover:scale-105 hover:border-cyan-400/50 hover:shadow-2xl hover:shadow-cyan-500/20"
        >
          <!-- Project Image -->
          <div class="relative overflow-hidden">
            <img 
              :src="project.image" 
              :alt="project.title"
              class="w-full h-48 object-cover transition-transform duration-700 group-hover:scale-110"
            />
            <div :class="`absolute inset-0 bg-gradient-to-t ${project.color} opacity-20 group-hover:opacity-30 transition-opacity duration-300`"></div>
            
            <!-- Status Badge -->
            <div class="absolute top-4 left-4">
              <span :class="`px-3 py-1 text-xs font-semibold rounded-full bg-slate-900/80 backdrop-blur-sm ${getStatusColor(project.status)}`">
                {{ project.status }}
              </span>
            </div>
            
            <!-- Year Badge -->
            <div class="absolute top-4 right-4">
              <span class="px-3 py-1 text-xs font-semibold rounded-full bg-slate-900/80 backdrop-blur-sm text-slate-300 flex items-center gap-1">
                <Calendar class="w-3 h-3" />
                {{ project.year }}
              </span>
            </div>

            <!-- Hover Overlay -->
            <div class="absolute inset-0 bg-slate-900/80 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
              <div class="flex gap-4">
                <button
                  @click="handleGithubClick(project.github, $event)"
                  class="p-3 bg-slate-800/80 rounded-full hover:bg-slate-700 transition-colors duration-200 hover:scale-110 transform"
                >
                  <Github class="w-5 h-5 text-white" />
                </button>
              </div>
            </div>
          </div>

          <!-- Project Content -->
          <div class="p-6">
            <!-- Category -->
            <div class="flex items-center gap-2 mb-3">
              <Tag class="w-4 h-4 text-cyan-400" />
              <span class="text-sm text-cyan-400 font-medium">{{ project.category }}</span>
            </div>

            <!-- Title -->
            <h3 class="text-xl font-bold text-white mb-3 group-hover:text-cyan-400 transition-colors duration-300">
              {{ project.title }}
            </h3>

            <!-- Description -->
            <p class="text-slate-400 text-sm leading-relaxed mb-4 line-clamp-3">
              {{ project.description }}
            </p>

            <!-- Technologies -->
            <div class="flex flex-wrap gap-2 mb-4">
              <div
                v-for="tech in project.technologies"
                :key="tech"
                class="flex items-center gap-1 px-2 py-1 bg-slate-800/50 rounded-lg text-xs text-slate-300 hover:bg-slate-700/50 transition-colors duration-200"
              >
                <component :is="getTechIcon(tech)" class="w-3 h-3" />
                {{ tech }}
              </div>
            </div>

            <!-- Footer -->
            <div class="flex items-center justify-between pt-4 border-t border-slate-700/50">
              <div class="flex items-center gap-2 text-slate-400 text-sm">
                <Eye class="w-4 h-4" />
                <span>View Details</span>
              </div>
              <div class="flex items-center gap-1">
                <Heart class="w-4 h-4 text-slate-400 hover:text-red-400 transition-colors duration-200 cursor-pointer" />
                <Star class="w-4 h-4 text-slate-400 hover:text-yellow-400 transition-colors duration-200 cursor-pointer" />
              </div>
            </div>
          </div>

          <!-- Glowing border effect -->
          <div class="absolute inset-0 rounded-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none">
            <div :class="`absolute inset-0 rounded-2xl bg-gradient-to-r ${project.color} opacity-20 blur-sm`"></div>
          </div>
        </div>
      </div>

      <!-- Stats Section -->
      <div class="mt-20 grid grid-cols-1  md:grid-cols-3 gap-6 max-w-3xl mx-auto">
        <div class="text-center p-6 bg-slate-900/30 backdrop-blur-sm rounded-xl border border-slate-700/30">
          <div class="text-3xl font-bold text-cyan-400 mb-2">6+</div>
          <div class="text-slate-400 text-sm">Projects Completed</div>
        </div>
        <div class="text-center p-6 bg-slate-900/30 backdrop-blur-sm rounded-xl border border-slate-700/30">
          <div class="text-3xl font-bold text-emerald-400 mb-2">15+</div>
          <div class="text-slate-400 text-sm">Technologies Used</div>
        </div>
        <div class="text-center p-6 bg-slate-900/30 backdrop-blur-sm rounded-xl border border-slate-700/30">
          <div class="text-3xl font-bold text-purple-400 mb-2">2+</div>
          <div class="text-slate-400 text-sm">Years Experience</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* Custom animations */
@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-10px) rotate(5deg); }
}

@keyframes pulse-glow {
  0%, 100% { box-shadow: 0 0 20px rgba(6, 182, 212, 0.3); }
  50% { box-shadow: 0 0 40px rgba(6, 182, 212, 0.6); }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-pulse-glow {
  animation: pulse-glow 2s ease-in-out infinite;
}

/* Scrollbar styling */
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
</style>