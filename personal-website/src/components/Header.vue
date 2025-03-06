<template>
    <header>
      <div class="header-content">
        <h1>Personal Profile</h1>
        <nav>
          <a href="#" @click="$emit('navigate', 'Home')">Home</a>
          <a href="#" @click="$emit('navigate', 'Guestbook')">Guestbook</a>
        </nav>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'Header'
  }
  </script>
  
  <style scoped>
  header {
    background-color: #3498db;
    color: white;
    width: 100%;
    padding: 1rem 2rem;
  }
  
  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  h1 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 500;
  }
  
  nav a {
    color: white;
    text-decoration: none;
    margin-left: 2rem;
    font-size: 1rem;
    transition: opacity 0.3s ease;
  }
  
  nav a:hover {
    opacity: 0.8;
  }
  </style>