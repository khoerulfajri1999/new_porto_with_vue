<template>
  <div class="hero-container">
    <div class="hero-content">
      <!-- Left Content -->
      <div class="content-left">
        <div class="hero-text">
          <h1 class="main-title">
            We are<br />
            <span class="highlight">Connection.</span>
          </h1>

          <div class="description">
            <p>We are technology, innovation and creativity combined.</p>
            <p>We are the experience of true digital transformation</p>
            <p>that goes beyond traditional limitations.</p>
          </div>

          <div class="cta-section">
            <button class="cta-button">CONNECT</button>
            <div class="cta-tagline">
              <div>Everything</div>
              <div>we can be</div>
            </div>
          </div>
        </div>

        <div class="powered-by">
          <div class="powered-text">Powered by</div>
          <div class="company-name">STEVARA TEKNOKREATIF.</div>
        </div>
      </div>

      <!-- Right Content - Floating Elements -->
      <div class="content-right">
        <div class="floating-elements">
          <!-- Tech Items -->
          <div class="floating-item item-1">
            <div class="tech-card laptop">
              <div class="screen"></div>
              <div class="keyboard"></div>
            </div>
          </div>

          <div class="floating-item item-2">
            <div class="tech-card phone">
              <div class="phone-screen"></div>
            </div>
          </div>

          <div class="floating-item item-3">
            <div class="tech-card tablet">
              <div class="tablet-screen"></div>
            </div>
          </div>

          <div class="floating-item item-4">
            <div class="tech-card code-block">
              <div class="code-line"></div>
              <div class="code-line short"></div>
              <div class="code-line"></div>
            </div>
          </div>

          <div class="floating-item item-5">
            <div class="tech-card database">
              <div class="db-cylinder"></div>
              <div class="db-cylinder"></div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Social Media Icons -->
    <div class="social-icons">
      <a href="#" class="social-icon facebook">f</a>
      <a href="#" class="social-icon instagram">ig</a>
      <a href="#" class="social-icon twitter">tw</a>
    </div>

    <!-- Scroll Indicator -->
    <div class="scroll-indicator">
      <svg
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
      >
        <path d="M7 13l3 3 7-7"></path>
        <path d="M12 17V3"></path>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroSection",
  mounted() {
    this.animateFloatingItems();
  },
  methods: {
    animateFloatingItems() {
      const items = document.querySelectorAll(".floating-item");
      items.forEach((item, index) => {
        item.style.animationDelay = `${index * 0.5}s`;
      });
    },
  },
};
</script>

<style scoped>
.hero-container {
  min-height: calc(100vh - 80px);
  position: relative;
  overflow: hidden;
}

.hero-content {
  display: flex;
  align-items: center;
  min-height: calc(100vh - 80px);
  padding: 0 40px;
}

.content-left {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 70vh;
}

.hero-text {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 40px;
}

.main-title {
  font-size: 5rem;
  font-weight: 900;
  line-height: 0.9;
  margin: 0;
  letter-spacing: -2px;
}

.highlight {
  color: #0ea5e9;
}

.description {
  font-size: 16px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
  max-width: 500px;
}

.description p {
  margin: 0 0 8px 0;
}

.cta-section {
  display: flex;
  align-items: center;
  gap: 32px;
}

.cta-button {
  background: #0ea5e9;
  color: white;
  border: none;
  padding: 16px 40px;
  font-size: 16px;
  font-weight: bold;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
  letter-spacing: 1px;
}

.cta-button:hover {
  background: #0284c7;
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(14, 165, 233, 0.3);
}

.cta-tagline {
  font-size: 14px;
  line-height: 1.2;
  color: rgba(255, 255, 255, 0.7);
}

.powered-by {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.6);
}

.company-name {
  font-weight: bold;
  color: white;
  margin-top: 4px;
  letter-spacing: 1px;
}

.content-right {
  width: 50%;
  height: 100vh;
  position: relative;
}

.floating-elements {
  position: relative;
  width: 100%;
  height: 100%;
}

.floating-item {
  position: absolute;
  animation: float 6s ease-in-out infinite;
}

.floating-item.item-1 {
  top: 20%;
  right: 20%;
  animation-delay: 0s;
}

.floating-item.item-2 {
  top: 60%;
  right: 40%;
  animation-delay: 1s;
}

.floating-item.item-3 {
  top: 40%;
  right: 10%;
  animation-delay: 2s;
}

.floating-item.item-4 {
  top: 10%;
  right: 50%;
  animation-delay: 3s;
}

.floating-item.item-5 {
  top: 70%;
  right: 15%;
  animation-delay: 4s;
}

.tech-card {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 12px;
  padding: 20px;
  transition: all 0.3s ease;
}

.tech-card:hover {
  transform: scale(1.05);
  background: rgba(255, 255, 255, 0.15);
}

/* Laptop */
.laptop {
  width: 80px;
  height: 60px;
}

.screen {
  width: 60px;
  height: 35px;
  background: #1f2937;
  border-radius: 4px;
  margin-bottom: 5px;
  position: relative;
}

.screen::after {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 4px;
  height: 4px;
  background: #0ea5e9;
  border-radius: 50%;
}

.keyboard {
  width: 70px;
  height: 15px;
  background: #374151;
  border-radius: 2px;
}

/* Phone */
.phone {
  width: 40px;
  height: 70px;
}

.phone-screen {
  width: 100%;
  height: 100%;
  background: #1f2937;
  border-radius: 8px;
  position: relative;
}

.phone-screen::after {
  content: "";
  position: absolute;
  bottom: 8px;
  left: 50%;
  transform: translateX(-50%);
  width: 20px;
  height: 2px;
  background: #0ea5e9;
  border-radius: 1px;
}

/* Tablet */
.tablet {
  width: 60px;
  height: 80px;
}

.tablet-screen {
  width: 100%;
  height: 100%;
  background: #1f2937;
  border-radius: 6px;
}

/* Code Block */
.code-block {
  width: 70px;
  height: 50px;
}

.code-line {
  height: 3px;
  background: #0ea5e9;
  margin-bottom: 4px;
  border-radius: 2px;
}

.code-line.short {
  width: 60%;
}

/* Database */
.database {
  width: 50px;
  height: 60px;
}

.db-cylinder {
  width: 100%;
  height: 20px;
  background: #0ea5e9;
  border-radius: 25px;
  margin-bottom: 8px;
  opacity: 0.8;
}

.db-cylinder:last-child {
  opacity: 0.6;
}

.social-icons {
  position: fixed;
  right: 24px;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 16px;
  z-index: 50;
}

.social-icon {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  font-weight: bold;
  text-decoration: none;
  color: white;
  transition: all 0.3s ease;
}

.facebook {
  background: #1877f2;
}
.instagram {
  background: #e4405f;
}
.twitter {
  background: #1da1f2;
}

.social-icon:hover {
  transform: translateX(-8px);
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
}

.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  animation: bounce 2s infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0px) rotate(0deg);
  }
  33% {
    transform: translateY(-20px) rotate(5deg);
  }
  66% {
    transform: translateY(-10px) rotate(-3deg);
  }
}

@keyframes bounce {
  0%,
  100% {
    transform: translateX(-50%) translateY(0);
  }
  50% {
    transform: translateX(-50%) translateY(-10px);
  }
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
    padding: 20px;
  }

  .content-left,
  .content-right {
    width: 100%;
  }

  .content-left {
    height: auto;
    gap: 40px;
  }

  .main-title {
    font-size: 3rem;
  }

  .content-right {
    height: 50vh;
  }

  .social-icons {
    position: relative;
    right: auto;
    top: auto;
    transform: none;
    flex-direction: row;
    justify-content: center;
    margin-top: 40px;
  }
}
</style>
