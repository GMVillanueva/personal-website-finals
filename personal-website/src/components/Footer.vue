<template>
    <footer>
      <div class="footer-content">
        <p>© {{ new Date().getFullYear() }} Personal Profile. All rights reserved.</p>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: 'Footer'
  }
  </script>
  
  <style scoped>
  footer {
    background-color: #2c3e50;
    color: white;
    width: 100%;
    padding: 1rem 2rem;
  }
  
  .footer-content {
    text-align: left;
    font-size: 0.9rem;
  }
  </style>