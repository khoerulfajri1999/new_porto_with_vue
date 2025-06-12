<template>
    <div>
      <div
        class=" bg-black/90 text-white relative overflow-hidden flex flex-col"
      >
        <div class="absolute inset-0 z-0">
          <img
            src="../assets/bg-image-dark-laptop.webp"
            alt="stevara.id-background"
            class="w-full h-full object-cover opacity-80"
          />
          <div class="absolute inset-0 bg-black/40"></div>
        </div>
  
        <div class="container mx-auto">
           <!-- <UnderContruction /> -->
           <Header @toggle-menu="toggleMenu" />
           <MobileMenu :isMenuOpen="isMenuOpen" @toggle-menu="toggleMenu" />
           <HeroSection @go-to-shop="goToShop" />
           <HeroFooter @open-social="openSocial" />
           <div class="absolute bottom-5 left-1/2 transform -translate-x-1/2 z-10">
             <ChevronDown class="w-20 h-20 text-white animate-bounce" />
           </div>
         </div>
      </div>
      <VisionMission />
      <CompanyProfileSection />
      <ContactSection />
      <Footer />
    </div>
  </template>
  
  <script>
  import { ChevronDown } from "lucide-vue-next";
  
  import Header from "./layout/Header.vue";
  import MobileMenu from "./layout/MobileMenu.vue";
  import HeroSection from "./HeroSection.vue";
  import HeroFooter from "./layout/HeroFooter.vue";
  import VisionMission from "./VisionMission.vue";
  import CompanyProfileSection from "./CompanyProfileSection.vue";
  import Footer from "./layout/Footer.vue";
  import UnderContruction from "./layout/UnderContruction.vue";
  import ContactSection from "./ContactSection.vue";
  
  export default {
    name: "LandingPage",
    components: {
      Header,
      HeroSection,
      HeroFooter,
      MobileMenu,
      CompanyProfileSection,
      VisionMission,
      Footer,
      ContactSection,
      UnderContruction,
      ChevronDown,
    },
    data() {
      return {
        isMenuOpen: false,
      };
    },
    methods: {
      toggleMenu() {
        this.isMenuOpen = !this.isMenuOpen;
      },
      goToShop() {
        console.log("Navigating to contact/shop page");
      },
      openSocial(platform) {
        const urls = {
          facebook: "https://facebook.com/stevara",
          instagram: "https://instagram.com/stevara",
          twitter: "https://twitter.com/stevara",
        };
        window.open(urls[platform], "_blank");
      },
    },
  };
  </script>
  
  <style scoped>
  @keyframes float {
    0%,
    100% {
      transform: translateY(0px);
    }
    50% {
      transform: translateY(-10px);
    }
  }
  
  .animate-float {
    animation: float 3s ease-in-out infinite;
  }
  
  * {
    transition: all 0.3s ease;
  }
  
  ::-webkit-scrollbar {
    width: 4px;
  }
  
  ::-webkit-scrollbar-track {
    background: rgba(255, 255, 255, 0.1);
  }
  
  ::-webkit-scrollbar-thumb {
    background: rgba(255, 255, 255, 0.3);
    border-radius: 2px;
  }
  
  ::-webkit-scrollbar-thumb:hover {
    background: rgba(255, 255, 255, 0.5);
  }
  </style>
  