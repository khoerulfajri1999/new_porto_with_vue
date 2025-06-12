<template>
  <section
    ref="aboutSection"
    id="about"
    class="text-gray-800 bg-white overflow-hidden"
  >
    <div class="flex flex-col lg:flex-row items-stretch">
      <!-- Left Section: Company Info -->
      <div
        ref="leftSection"
        class="lg:w-1/2 bg-gray-100 px-21 py-12 lg:px-20 lg:py-20 flex flex-col justify-center"
      >
        <h1
          ref="heading"
          class="text-3xl lg:text-4xl font-bold text-black mb-6 leading-tight"
        >
          PT SAKA TEKNOKREATIF NUSWANTARA
        </h1>

        <p class="text-gray-700 leading-relaxed mb-4">
          PT Saka Teknokreatif Nuswantara is a technology company engaged in the
          development of
          <span class="font-medium italic"
            >web-based software, mobile applications, and web services</span
          >. We focus on developing internal information systems and digital
          solutions tailored to client needs.
        </p>
        <p class="text-gray-700 leading-relaxed">
          With an adaptive approach and emphasis on process efficiency, we have
          experience handling various IT projects closely related to internal
          business processes, including financial management, operational data
          tracking, registration systems, and data visualization for decision
          support.
        </p>
      </div>

      <!-- Right Section: Photo & Quote -->
      <div
        ref="rightSection"
        class="lg:w-1/2 flex flex-col items-end sm:items-center justify-center relative px-21 py-30 lg:px-20"
      >
        <div class="absolute inset-0 z-0">
          <img
            src="../assets/texture-bg.webp"
            alt="stevara.id-background"
            class="w-full h-full object-cover opacity-80"
          />
          <div class="absolute inset-0 bg-black/40"></div>
        </div>
        <!-- Photo & Bubble -->
        <div
          class="relative flex flex-row justify-between items-center sm:flex-col sm:items-center"
        >
          <!-- Bubble -->
          <div
            ref="bubble"
            class="absolute -top-8 sm:-top-16 -left-48 sm:-left-25 lg:-left-40 bg-yellow-300 text-black text-xs sm:text-sm lg:text-md p-4 z-10 rounded-xl shadow-xl w-[250px] sm:w-[200px] lg:w-[300px] text-center order-2 sm:order-1"
          >
            <p class="italic leading-relaxed">
              “We believe that great technology is not just about features, but
              about solving real problems in a simple and reliable way.”
            </p>
          </div>

          <!-- Image -->
          <div
            ref="photo"
            class="w-46 h-46 sm:w-76 sm:h-76 lg:w-100 lg:h-100 rounded-full overflow-hidden border-4 border-gray-300 shadow-lg"
          >
            <img
              src="../assets/People.png"
              alt="Agung Tri Wibowo"
              class="w-full h-full object-cover"
            />
          </div>
        </div>

        <!-- Nama -->
        <div ref="caption" class="mt-6 text-center">
          <p class="font-semibold text-lg text-white">
            Agung Tri Wibowo, S.Kom
          </p>
          <p class="text-sm text-neutral-400">
            Director of PT SAKA TEKNOKREATIF NUSWANTARA
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "AboutSection",
  mounted() {
    // H1: dari atas ke bawah
    gsap.from(this.$refs.heading, {
      scrollTrigger: {
        trigger: this.$refs.heading,
        start: "top 80%",
        toggleActions: "restart none none none",
      },
      y: -50,
      opacity: 0,
      duration: 1,
      ease: "power2.out",
    });

    // Paragraf-paragraf: dari kiri ke kanan
    const paragraphs = this.$refs.leftSection.querySelectorAll("p");
    paragraphs.forEach((el, index) => {
      gsap.from(el, {
        scrollTrigger: {
          trigger: el,
          start: "top 85%",
          toggleActions: "restart none none none",
        },
        x: -80,
        opacity: 0,
        duration: 1,
        delay: index * 0.2,
        ease: "power2.out",
      });
    });

    // Foto: scale & fade in
    gsap.from(this.$refs.photo, {
      scrollTrigger: {
        trigger: this.$refs.photo,
        toggleActions: "restart none none none",
      },
      opacity: 0,
      scale: 0.5,
      duration: 1,
      ease: "back.out(1.7)",
      delay: 0.2,
    });

    // Bubble: dari kiri
    gsap.from(this.$refs.bubble, {
      scrollTrigger: {
        trigger: this.$refs.bubble,
        toggleActions: "restart none none none",
      },
      x: -200,
      opacity: 0,
      duration: 1,
      ease: "power2.out",
      delay: 0.4,
    });

    // Caption: dari bawah
    gsap.from(this.$refs.caption, {
      scrollTrigger: {
        trigger: this.$refs.caption,
        toggleActions: "restart none none none",
      },
      y: 50,
      opacity: 0,
      duration: 1,
      ease: "power2.out",
      delay: 0.6,
    });
  },
};
</script>

<style scoped>
/* Responsif bila perlu */
@media (max-width: 1024px) {
  .bubble {
    top: -12rem !important;
  }
}
</style>
