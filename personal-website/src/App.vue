<template>
  <div class="app-wrapper">
    <header class="header">
      <div class="container header-content">
        <h1>My Profile</h1>
        <nav class="nav">
          <a 
            href="#" 
            @click.prevent="currentComponent = 'Home'"
            :class="{ active: currentComponent === 'Home' }"
          >Home</a>
          <a 
            href="#" 
            @click.prevent="currentComponent = 'Guestbook'"
            :class="{ active: currentComponent === 'Guestbook' }"
          >Guestbook</a>
        </nav>
      </div>
    </header>
    
    <main class="main">
      <div class="container main-content">
        <component :is="currentComponent"></component>
      </div>
    </main>
    
    <footer class="footer">
      <div class="container">
        <p>© {{ new Date().getFullYear() }} Personal Profile. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script>
import Home from './components/Home.vue'
import Guestbook from './components/Guestbook.vue'

export default {
  name: 'App',
  components: {
    Home,
    Guestbook
  },
  data() {
    return {
      currentComponent: 'Home'
    }
  }
}
</script>

<style>
/* Reset and base styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  line-height: 1.6;
  background-color: #f5f5f5;
  min-height: 100vh;
}

/* Layout */
.app-wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  width: 100%;
}

/* Header */
.header {
  background-color: #2c3e50;
  padding: 1rem 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header h1 {
  color: white;
  font-size: 1.5rem;
}

/* Navigation */
.nav {
  display: flex;
  gap: 1.5rem;
}

.nav a {
  color: white;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

.nav a:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.nav a.active {
  background-color: rgba(255, 255, 255, 0.2);
}

/* Main content */
.main {
  flex: 1;
  padding: 2rem 0;
}

.main-content {
  display: flex;
  justify-content: center;
  align-items: flex-start;
}

/* Footer */
.footer {
  background-color: #2c3e50;
  color: white;
  padding: 1rem 0;
  margin-top: auto;
}

.footer p {
  text-align: center;
}

/* Responsive design */
@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
  
  .nav {
    justify-content: center;
  }
}
</style>