<template>
  <div class="home-container">
    <section class="profile">
      <img src="https://scontent.fmnl25-7.fna.fbcdn.net/v/t39.30808-6/453785427_8152310394826037_7553184774730877772_n.jpg?_nc_cat=111&ccb=1-7&_nc_sid=a5f93a&_nc_eui2=AeF0XC7fuN1drtpkTgmagYfyMpP1l7pZ96Myk_WXuln3oy6Cehmb1IYEaMwFIinOvTcdHheG2k8C4jKy_lFfRP1r&_nc_ohc=eRh6tx9UAt0Q7kNvgGE2O6k&_nc_zt=23&_nc_ht=scontent.fmnl25-7.fna&_nc_gid=AaKOH-G9eCTGHVZdC7jmOO6&oh=00_AYCPMwmsDpxmVnl5ZgAladr5tbQWIUUwN_iocxTy5HJzhQ&oe=674E6FD5" 
           alt="Profile Picture" 
           class="profile-image">
      <h1>[Your Name]</h1>
      <p>Computer Science Student & Aspiring Developer</p>
    </section>

    <section class="hoverable">
      <h2>About Me</h2>
      <p>Welcome to my personal profile! I'm passionate about technology and development. Currently pursuing a degree in Computer Science, I'm excited about building a successful career in software development.</p>
    </section>

    <section class="hoverable">
      <h2>Education & Achievements</h2>
      <ul>
        <li>Highschool Graduate</li>
        <li>Senior Highschool Graduate</li>
        <li>College Shiftee</li>
      </ul>
    </section>

    <section class="hoverable">
      <h2>IT Experience</h2>
      <ul>
        <li>Computer building</li>
        <li>FiveM Developer</li>
        <li>Habbo Retros Developer</li>
      </ul>
    </section>

    <section class="hoverable">
      <h2>Hobbies & Interests</h2>
      <ul>
        <li>Gaming</li>
        <li>Movies</li>
        <li>Buying and Selling</li>
      </ul>
    </section>

    <section class="hoverable">
      <h2>Goals In Life / Dream</h2>
      <ul>
        <li>To be a successful developer</li>
        <li>To be able to provide a comfortable life</li>
      </ul>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>

<style scoped>
.home-container {
  max-width: 100%;
}

.profile {
  text-align: center;
  margin-bottom: 2rem;
}

.profile-image {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 1rem;
}

h1 {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.hoverable {
  padding: 1rem;
  margin-bottom: 1rem;
  border: 1px solid #eaeaea;
  border-radius: 4px;
  transition: box-shadow 0.3s ease;
}

.hoverable:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.651);
}

ul {
  list-style-type: none;
  padding-left: 0;
}

li {
  margin-bottom: 0.5rem;
}
</style>