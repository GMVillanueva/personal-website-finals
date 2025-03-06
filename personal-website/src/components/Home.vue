<template>
  <div class="container">
    <div class="card">
      <h1 class="title">Personal Profile Web page</h1>
      
      <div class="content-grid">
        <div class="content-column">
          <section class="section">
            <h2 class="section-title">About Me</h2>
            <p>
              Welcome to my personal profile! I'm passionate about technology and development.
            </p>
          </section>
          
          <section class="section">
            <h2 class="section-title">Education / Achievements</h2>
            <ul class="list">
              <li>Highschool Graduate</li>
              <li>Senior Highschool Graduate</li>
              <li>College Shiftee</li>
            </ul>
          </section>
          
          <section class="section">
            <h2 class="section-title">Course</h2>
            <ul class="list">
              <li>Former BA Business Administration and Management</li>
              <li>Current Computer Science</li>
            </ul>
          </section>
        </div>
        
        <div class="content-column">
          <section class="section">
            <h2 class="section-title">IT Experience</h2>
            <ul class="list">
              <li>Computer building</li>
              <li>FiveM Developer</li>
              <li>Habbo Retros Developer</li>
            </ul>
          </section>
          
          <section class="section">
            <h2 class="section-title">Hobbies & Interests</h2>
            <ul class="list">
              <li>Gaming</li>
              <li>Movies</li>
              <li>Buying and Selling</li>
            </ul>
          </section>
          
          <section class="section">
            <h2 class="section-title">Goals In Life / Dream</h2>
            <ul class="list">
              <li>To be a successful developer</li>
              <li>To be able to provide a comfortable life</li>
            </ul>
          </section>
        </div>
      </div>
    </div>
    
    <div class="card">
      <h2 class="gallery-title">Picture Gallery</h2>
      <div class="gallery">
        <h3 class="gallery-subtitle">Recent Photo</h3>
        <div class="gallery-grid">
          <div class="gallery-item">
            <img 
              src="https://github.com/GMVillanueva/personal-website-finals/raw/main/personal-website/img/482461755_963297175534887_9148725664306783511_n.jpg" 
              alt="Den lalabs" 
              class="gallery-image"
            />
          </div>
          <div class="gallery-item">
            <img 
              src="https://github.com/GMVillanueva/personal-website-finals/raw/main/personal-website/img/482364440_1615990952418499_1992289064492331814_n.jpg" 
              alt="Lalabs den" 
              class="gallery-image"
            />
          </div>
          <div class="gallery-item">
            <img 
              src="https://github.com/GMVillanueva/personal-website-finals/raw/main/personal-website/img/481783438_531627353284518_1477088235843197324_n.jpg" 
              alt="Shades" 
              class="gallery-image"
            />
          </div>
          <div class="gallery-item">
            <img 
              src="https://github.com/GMVillanueva/personal-website-finals/raw/main/personal-website/img/481719931_1288568819110925_4081401323568267308_n.jpg" 
              alt="Setup" 
              class="gallery-image"
            />
          </div>
          <div class="gallery-item">
            <img 
              src="https://github.com/GMVillanueva/personal-website-finals/raw/main/personal-website/img/481796888_1196781338716167_2077672232120609431_n.jpg" 
              alt="Setup 1" 
              class="gallery-image"
            />
          </div>
          <div class="gallery-item">
            <img 
              src="https://github.com/GMVillanueva/personal-website-finals/raw/main/personal-website/img/481965755_1191415489224216_1732928015112449294_n.jpg" 
              alt="Setup 2" 
              class="gallery-image"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 2rem;
  margin-bottom: 2rem;
}

.title {
  font-size: 2.5rem;
  color: #2c3e50;
  text-align: center;
  margin-bottom: 2rem;
}

.content-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}

.content-column {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.section {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 6px;
  border-left: 4px solid #3498db;
}

.section-title {
  color: #3498db;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e9ecef;
}

.list {
  list-style-type: none;
  padding-left: 0;
}

.list li {
  margin-bottom: 0.5rem;
  padding-left: 1.5rem;
  position: relative;
}

.list li::before {
  content: "•";
  color: #3498db;
  position: absolute;
  left: 0;
}

.gallery-title {
  font-size: 2rem;
  color: #2c3e50;
  text-align: center;
  margin-bottom: 1.5rem;
}

.gallery {
  text-align: center;
}

.gallery-subtitle {
  color: #3498db;
  margin-bottom: 1rem;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.gallery-item {
  aspect-ratio: 16/9;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.gallery-item:hover {
  transform: scale(1.05);
}

.gallery-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 8px;
}

/* Responsive Design */
@media (max-width: 768px) {
  .content-grid {
    grid-template-columns: 1fr;
  }
  
  .container {
    padding: 1rem;
  }
  
  .card {
    padding: 1.5rem;
  }
  
  .title {
    font-size: 2rem;
  }
  
  .gallery-grid {
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 0.75rem;
  }
}

@media (max-width: 480px) {
  .gallery-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 0.5rem;
  }
}
</style>