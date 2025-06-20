<template>
  <div>
    <div
      class="min-h-screen relative bg-gradient-to-tr from-[#030415] via-[#1E0B38] to-[#030415] text-white overflow-hidden flex flex-col"
    >
    <div class="absolute inset-0 bg-[linear-gradient(rgba(120,119,198,0.1)_1px,transparent_1px),linear-gradient(90deg,rgba(120,119,198,0.1)_1px,transparent_1px)] bg-[size:50px_50px]"></div>
    

         <!-- <UnderContruction /> -->
         <Header @toggle-menu="toggleMenu" />
         <MobileMenu :isMenuOpen="isMenuOpen" @toggle-menu="toggleMenu" />
         <HeroSection @open-social="openSocial" />
         <HeroFooter />
         
    </div>
    <!-- <VisionMission /> -->
    <SkillSection />
    <ProjectSection />
    <!-- <CompanyProfileSection /> -->
    <ContactSection />
    <Footer />
  </div>
</template>

<script>
import { defineAsyncComponent } from 'vue'
import { ChevronDown } from "lucide-vue-next";

// Eager loaded (langsung dimuat saat halaman dibuka)
import Header from "../components/layout/Header.vue";
import MobileMenu from "../components/layout/MobileMenu.vue";
import HeroSection from "../components/HeroSection.vue";
import Footer from "../components/layout/Footer.vue";
import HeroFooter from "../components/layout/HeroFooter.vue";

// Lazy loaded (baru dimuat saat dibutuhkan)
const ContactSection = defineAsyncComponent(() =>
  import("../components/ContactSection.vue")
)
const SkillSection = defineAsyncComponent(() =>
  import("../components/SkillSection.vue")
)
const ProjectSection = defineAsyncComponent(() =>
  import("../components/ProjectSection.vue")
)

export default {
  name: "LandingPage",
  components: {
    Header,
    HeroSection,
    MobileMenu,
    Footer,
    HeroFooter,
    ContactSection,
    SkillSection,
    ProjectSection,
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
        linkedin: "https://www.linkedin.com/in/khoerul-fajri-93698a229/",
        github: "https://github.com/khoerulfajri1999/",
        whatsapp: "https://wa.me/62882003233343",
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
