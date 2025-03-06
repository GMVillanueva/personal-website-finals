<template>
  <div class="app-container">
    <Header @navigate="navigate" />
    <main>
      <div class="content-wrapper">
        <component :is="currentComponent"></component>
      </div>
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Home from './components/Home.vue'
import Guestbook from './components/Guestbook.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Home,
    Guestbook
  },
  data() {
    return {
      currentComponent: 'Home'
    }
  },
  methods: {
    navigate(component) {
      this.currentComponent = component
    }
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
  color: #333;
  margin: 0;
  padding: 0;
  background: url('https://source.unsplash.com/1920x1080/?minimal,light') no-repeat center center fixed;
  background-size: cover;
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: rgba(255, 255, 255, 0.95);
}

main {
  flex: 1;
}

.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

h2 {
  color: #00bcd4;
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.hoverable-section {
  background: white;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.hoverable-section:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

ul {
  list-style: none;
  padding: 0;
}

ul li {
  padding: 0.5rem 0;
  padding-left: 1.5rem;
  position: relative;
}

ul li::before {
  content: "•";
  color: #ff5252;
  position: absolute;
  left: 0;
}

@media (max-width: 768px) {
  .content-wrapper {
    padding: 1rem;
  }
  
  h2 {
    font-size: 1.5rem;
  }
}
</style>