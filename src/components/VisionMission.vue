<template>
  <section class="grid grid-cols-1 md:grid-cols-8" id="services">
    <div ref="visionRef" class="py-14 px-21 col-span-8 md:col-span-4 lg:col-span-4 xl:col-span-2 bg-black text-white p-4 opacity-0">
      <h2 class="text-xl font-semibold border-l-4 border-white pl-2 mb-2">Vision</h2>
      <p class="text-sm leading-relaxed">
        To become a trusted technology partner that drives sustainable digital transformation
        in Indonesia through innovative, adaptive, and impactful software solutions.
      </p>
    </div>

    <div ref="missionRef" class="py-14 px-21 md:px-10 col-span-8 md:col-span-4 lg:col-span-4 xl:col-span-2 p-4 bg-gray-100 opacity-0">
      <h2 class="text-xl font-semibold border-l-4 border-black pl-2 mb-2">Mission</h2>
      <ul class="text-sm leading-relaxed list-disc pl-4 space-y-2">
        <li>
          Create impactful digital solutions that are tailored, user-friendly, and delivered with high quality and precision.
        </li>
        <li>
          Collaborate transparently with clients to build strong partnerships and deliver meaningful results.
        </li>
        <li>
          Empower local talent while fostering a culture of innovation, creativity, and continuous growth.
        </li>
      </ul>
    </div>

    <div ref="nameRef" class="col-span-8 my-10 xl:col-span-4 flex flex-col justify-center m-auto bg-white p-4 rounded opacity-0">
      <p class="text-3xl md:text-7xl font-bold text-center">stevara.id</p>
      <p class="text-md uppercase tracking-wide font-bold text-center">PT SAKA TEKNOKREATIF NUSANTARA</p>
    </div>
  </section>
</template>

<script>
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'CompanySection',
  mounted() {
    gsap.fromTo(
      this.$refs.visionRef,
      { opacity: 0, y: 50 },
      {
        opacity: 1,
        y: 0,
        duration: 1,
        scrollTrigger: {
          trigger: this.$refs.visionRef,
          start: 'top 80%',
          toggleActions: 'play none none reset',
        },
      }
    );

    gsap.fromTo(
      this.$refs.missionRef,
      { opacity: 0, y: 50 },
      {
        opacity: 1,
        y: 0,
        duration: 1,
        delay: 0.2,
        scrollTrigger: {
          trigger: this.$refs.missionRef,
          start: 'top 80%',
          toggleActions: 'play none none reset',
        },
      }
    );

    gsap.fromTo(
      this.$refs.nameRef,
      { opacity: 0, scale: 0.5 },
      {
        opacity: 1,
        scale: 1,
        duration: 1,
        delay: 0.4,
        scrollTrigger: {
          trigger: this.$refs.nameRef,
          start: 'top 80%',
          toggleActions: 'play none none reset',
        },
      }
    );
  },
};
</script>
