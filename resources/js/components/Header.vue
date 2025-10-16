<template>
  <header class="header">
    <nav class="nav">
      <div class="logo">
        <svg class="logo-svg" width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="20" cy="20" r="18" stroke="#4f46e5" stroke-width="3" fill="#fbff14" />
          <text x="50%" y="55%" text-anchor="middle" fill="#222" font-size="16" font-family="Poppins, Arial, sans-serif" dy=".3em">TB</text>
        </svg>
        <h1>Terkkos Billiard's Club</h1>
      </div>

      <ul class="nav-links" :class="{ open: menuOpen }" v-show="menuOpen || windowWidth > 768">
        <li><a href="#">Inicio</a></li>
        <li><a href="#">Reservas</a></li>
        <li><a href="#">Torneos</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
      <div class="profile">
        <img src="https://i.pravatar.cc/40?u=usuario" alt="Perfil" class="avatar" />
        <span class="username">Usuario</span>
      </div>
      <button class="menu-btn" @click="toggleMenu">
        <span class="menu-icon">☰</span>
      </button>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuOpen: false,
      windowWidth: window.innerWidth,
    };
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.handleResize);
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    handleResize() {
      this.windowWidth = window.innerWidth;
      if (this.windowWidth > 768) {
        this.menuOpen = false;
      }
    },
  },
};
</script>

<style scoped>
.header {
  background: #fbff14;
  color: #000000;
  padding: 0.5rem 1rem;
}
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  position: relative;
}
.logo h1 {
  font-size: 1.5rem;
  font-weight: 600;
  letter-spacing: 1px;
}
.nav-links {
  display: flex;
  gap: 1.5rem;
  list-style: none;
  margin: 0;
  padding: 0;
}
.nav-links li a {
  text-decoration: none;
  color: #222;
  font-weight: 500;
  transition: color 0.2s;
}
.nav-links li a:hover {
  color: #4f46e5;
}
.profile {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #4f46e5;
}
.username {
  font-size: 1rem;
  font-weight: 500;
}
.menu-btn {
  display: none;
  background: none;
  border: none;
  font-size: 2rem;
  cursor: pointer;
}
@media (max-width: 768px) {
  .nav-links {
    flex-direction: column;
    width: 100%;
    background: #fbff14;
    position: absolute;
    top: 60px;
    left: 0;
    padding: 1rem 0;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  }
  .nav-links:not(.open) {
    display: none;
  }
  .menu-btn {
    display: block;
  }
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}
.logo-svg {
  flex-shrink: 0;
  width: 40px;
  height: 40px;
  display: inline-block;
}
/* Scoped SVG text fix */
.logo-svg text {
  font-family: 'Poppins', Arial, sans-serif;
  font-size: 16px;
  font-weight: 600;
}
</style>