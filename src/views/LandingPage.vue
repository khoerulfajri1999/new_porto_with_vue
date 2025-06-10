<template>
  <div>
    <div
      class="h-screen bg-black/90 text-white relative overflow-hidden flex flex-col"
    >
      <div class="absolute inset-0 z-0">
        <img
          src="../assets/bg-image-minimalist-plant.jpg"
          alt="stevara.id-background"
          class="w-full h-full object-cover opacity-80"
        />
        <div class="absolute inset-0 bg-black/40"></div>
      </div>

      <HeaderSection @toggle-menu="toggleMenu" />
      <MainContent @go-to-shop="goToShop" />
      <MainFooterSection @open-social="openSocial" />
      <MobileMenu :isMenuOpen="isMenuOpen" @toggle-menu="toggleMenu" />

      <div class="absolute bottom-16 left-1/2 transform -translate-x-1/2 z-10">
        <ChevronDown class="w-6 h-6 text-white animate-bounce" />
      </div>
    </div>
    <VisionMission />
    <CompanyProfile />
    <FooterSection />
  </div>
</template>

<script>
import { ChevronDown } from "lucide-vue-next";
import HeaderSection from "../components/HeaderSection.vue";
import MainContent from "../components/MainContent.vue";
import MainFooterSection from "../components/MainFooterSection.vue";
import MobileMenu from "../components/MobileMenu.vue";
import CompanyProfile from "../components/CompanyProfile.vue";
import VisionMission from "../components/VisionMission.vue";
import FooterSection from "../components/FooterSection.vue";

export default {
  name: "LandingPage",
  components: {
    HeaderSection,
    MainContent,
    MainFooterSection,
    MobileMenu,
    CompanyProfile,
    VisionMission,
    FooterSection,
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
