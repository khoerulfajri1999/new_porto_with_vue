<template>
  <nav class="navbar">
    <div class="nav-left">
      <div class="logo-section">
        <div class="logo-box">stevara.id</div>
        <div class="tagline">
          <div>Everything</div>
          <div>We Can Be</div>
        </div>
      </div>

      <div class="location-tag">Purwokerto</div>
    </div>

    <div class="nav-right">
      <div class="cart-icon">
        <svg
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
        >
          <circle cx="9" cy="21" r="1"></circle>
          <circle cx="20" cy="21" r="1"></circle>
          <path
            d="m1 1 4 4 2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"
          ></path>
        </svg>
        <span class="cart-count">0</span>
      </div>

      <div class="menu-icon">
        <div class="menu-line"></div>
        <div class="menu-line"></div>
        <div class="menu-line"></div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style scoped>
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 24px 40px;
  position: relative;
  z-index: 100;
}

.nav-left {
  display: flex;
  align-items: center;
  gap: 32px;
}

.logo-section {
  display: flex;
  align-items: center;
  gap: 16px;
}

.logo-box {
  border: 2px solid white;
  padding: 8px 16px;
  font-size: 16px;
  font-weight: bold;
  letter-spacing: 1px;
}

.tagline {
  font-size: 14px;
  line-height: 1.2;
  font-weight: 500;
}

.location-tag {
  border: 1px solid rgba(255, 255, 255, 0.3);
  padding: 4px 12px;
  font-size: 12px;
  background: rgba(255, 255, 255, 0.1);
}

.nav-right {
  display: flex;
  align-items: center;
  gap: 24px;
}

.cart-icon {
  position: relative;
  cursor: pointer;
  padding: 8px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  transition: all 0.3s ease;
}

.cart-icon:hover {
  background: rgba(255, 255, 255, 0.1);
}

.cart-count {
  position: absolute;
  top: -8px;
  right: -8px;
  background: #0ea5e9;
  color: white;
  font-size: 12px;
  font-weight: bold;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.menu-icon {
  cursor: pointer;
  padding: 8px;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  gap: 3px;
  transition: all 0.3s ease;
}

.menu-icon:hover {
  background: rgba(255, 255, 255, 0.1);
}

.menu-line {
  width: 16px;
  height: 2px;
  background: white;
  transition: all 0.3s ease;
}

@media (max-width: 768px) {
  .navbar {
    padding: 16px 20px;
  }

  .nav-left {
    gap: 16px;
  }

  .location-tag {
    display: none;
  }
}
</style>
