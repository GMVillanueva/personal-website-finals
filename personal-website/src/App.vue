<template>
  <div>
    <header>
      <div class="container header-content">
        <h1>My Profile</h1>
        <nav>
          <a href="#" @click.prevent="currentComponent = 'Home'">Home</a>
          <a href="#" @click.prevent="currentComponent = 'Guestbook'">Guestbook</a>
        </nav>
      </div>
    </header>
    
    <main>
      <component :is="currentComponent"></component>
    </main>
    
    <footer>
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