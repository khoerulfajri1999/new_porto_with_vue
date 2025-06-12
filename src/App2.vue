<template>
  <div class="flex flex-col min-h-screen text-white">
    <!-- Section dengan background -->
    <div class="relative h-screen overflow-hidden bg-black/90">
      <!-- Background Image -->
      <div class="absolute inset-0 z-0">
        <img
          src="../assets/bg-image-dark-laptop.webp"
          alt="stevara.id-background"
          class="w-full h-full object-cover opacity-80"
        />
        <div class="absolute inset-0 bg-black/40"></div>
      </div>

      <!-- Hero & Header Content (z-10) -->
      <div class="relative z-10 flex flex-col h-full">
        <!-- <UnderContruction /> -->
        <Header @toggle-menu="toggleMenu" />
        <MobileMenu :isMenuOpen="isMenuOpen" @toggle-menu="toggleMenu" />
        <HeroSection @go-to-shop="goToShop" />
        <HeroFooter @open-social="openSocial" />
        <div class="absolute bottom-5 left-1/2 transform -translate-x-1/2">
          <ChevronDown class="w-20 h-20 text-white animate-bounce" />
        </div>
      </div>
    </div>

    <!-- Section tanpa background -->
    <VisionMission />
    <CompanyProfileSection />
    <ContactSection />
    <Footer />
  </div>
</template>
