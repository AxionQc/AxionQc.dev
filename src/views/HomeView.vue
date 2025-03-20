<template>
  <main class="main-container">
    <!-- Removed background canvas -->
    <div class="sidebar">
      <h2>Navigation</h2>
      <ul><picture>
        <source media="(min-width: )" srcset="">
        <img src="" alt="">
      </picture>
        <li><a href="#about-me">👤 About Me</a></li>
        <li><a href="#projects">📁 Projects</a></li>
        <li><a href="#skills">💡 Skills</a></li>
        <li><a href="#contact">📞 Contact</a></li>
      </ul>
    </div>
    <div class="content">
      <div class="text-container">
        <h1>Hi, Im AxionQc, Come take a look around</h1>
        <p>Welcome to my portfolio website. Here you can find information about my projects I'm currently working on, skills, and experience.</p>
      </div>
      <!-- Reverted container positions -->
      <div class="section-container about-me" id="about-me">
        <h2>About Me</h2>
        <p>I am a passionate developer with experience in various technologies. I love creating innovative solutions and learning new things.</p>


      </div>
      <div class="section-container projects" id="projects">
        <h2>Projects</h2>
        <ul>
          <li>Reparios: Reparios will be a 3D Multiplayer Co-Op game where you get sent to stations and planets to repair machines and restock inventory.</li>
          <li>Celestial Drift: Celestial drift is a 2d adventure game about an astronaut who wakes up alone in his Station. Will you Be able to solve the mystery and come back home?</li>
          <li>AxionLabs: AxionLabs is a Pc Assembling/OEM company im starting to attempt to give people the best computers for the cheapest price</li>
        </ul>


      </div>
      <div class="section-container skills" id="skills">
        <h2>Skills</h2>
        <p>Assembling Computers, Server Maintenance, Very Light coding</p>


      </div>
      <div class="section-container contact" id="contact">
        <h2>Contact</h2>
        <p>Feel free to reach out to me on any of my Socials.</p>


      </div>
    </div>
  </main>
</template>

<style scoped>
.main-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #fff;
  overflow-y: scroll; /* Enable scrolling */
  padding-top: 80px; /* Lower everything to avoid overlapping the navbar */
}

/* Removed background canvas styles */

.sidebar {
  position: fixed;
  top: 20px;
  right: 20px;
  width: 150px;
  background-color: rgba(0, 0, 0, 0.7);
  padding: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
  border: 1px solid rgba(221, 160, 221, 0.5); /* Purple semi-transparent outline */
  transition: top 0.3s ease; /* Add transition for sliding effect */
}

.sidebar h2 {
  font-size: 16px;
  margin-bottom: 10px;
}

.sidebar ul {
  list-style-type: none;
  padding: 0;
}

.sidebar ul li {
  margin: 5px 0;
}

.sidebar ul li a {
  color: #fff;
  text-decoration: none;
  font-size: 14px;
}

.content {
  width: 80%;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  margin-top: 60px; /* Make content go down more */
}

.text-container {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  outline: 2px solid rgba(221, 160, 221, 0.5); /* Purple semi-transparent outline */
  margin-bottom: 20px;
}

.section-container {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  outline: 2px solid rgba(221, 160, 221, 0.5); /* Purple semi-transparent outline */
  margin-bottom: 20px;
  width: 60%; /* Make containers less wide */
}

.section-container h2 {
  margin-bottom: 10px;
}

.section-container ul {
  list-style-type: disc;
  padding-left: 20px;
  text-align: left;
}

.section-container p, .section-container li {
  margin: 10px 0;
}
</style>
