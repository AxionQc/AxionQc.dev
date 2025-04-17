<template>
  <main class="main-container">
    <div class="socials-sidebar">
      <ul>
        <li>
          <a href="https://bsky.app/profile/axionqc.dev" target="_blank">
            <svg
              viewBox="-50 -50 430 390"
              aria-hidden="true"
              style="width: 24px; height: 24px; fill: #00acee"
            >
              <path
                d="M180 141.964C163.699 110.262 119.308 51.1817 78.0347 22.044C38.4971 -5.86834 23.414 -1.03207 13.526 3.43594C2.08093 8.60755 0 26.1785 0 36.5164C0 46.8542 5.66748 121.272 9.36416 133.694C21.5786 174.738 65.0603 188.607 105.104 184.156C107.151 183.852 109.227 183.572 111.329 183.312C109.267 183.642 107.19 183.924 105.104 184.156C46.4204 192.847 -5.69621 214.233 62.6582 290.33C137.848 368.18 165.705 273.637 180 225.702C194.295 273.637 210.76 364.771 295.995 290.33C360 225.702 313.58 192.85 254.896 184.158C252.81 183.926 250.733 183.645 248.671 183.315C250.773 183.574 252.849 183.855 254.896 184.158C294.94 188.61 338.421 174.74 350.636 133.697C354.333 121.275 360 46.8568 360 36.519C360 26.1811 357.919 8.61012 346.474 3.43851C336.586 -1.02949 321.503 -5.86576 281.965 22.0466C240.692 51.1843 196.301 110.262 180 141.964Z"
              ></path>
            </svg>
          </a>
        </li>
        <li>
          <a href="https://github.com/AxionQc" target="_blank">
            <i class="fab fa-github" style="font-size: 24px; color: #333"></i>
          </a>
        </li>
        <li>
          <a href="https://youtube.com/@AxionQc" target="_blank">
            <i class="fab fa-youtube" style="font-size: 24px; color: #ff0000"></i>
          </a>
        </li>
        <li>
          <a href="https://discord.com/users/805461441514700820" target="_blank">
            <i class="fab fa-discord" style="font-size: 24px; color: #7289da"></i>
          </a>
        </li>
        <li>
          <a href="https://www.reddit.com/user/AxiosTheProot" target="_blank">
            <i class="fab fa-reddit" style="font-size: 24px; color: #ff4500"></i>
          </a>
        </li>
        <li>
          <a href="https://steamcommunity.com/profiles/76561199097361562/" target="_blank">
            <i class="fab fa-steam" style="font-size: 24px; color: #00adee"></i>
          </a>
        </li>
      </ul>
    </div>
    <div class="content">
      <img src="/Avatar.png" alt="Descriptive Alt Text" class="top-image" />
      <div class="text-container">
        <h1>Hi, Im AxionQc, Come take a look around</h1>
        <p>Welcome, Here you can find information about my projects I'm currently working on, skills, and experience.</p>
      </div>
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
  justify-content: center; /* Center content vertically */
  color: #fff;
  overflow: hidden; /* Prevent scrolling */
  padding: 20px; /* Add padding for spacing */
}

.socials-sidebar {
  position: fixed;
  top: 50%;
  left: 20px;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.socials-sidebar ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.socials-sidebar li {
  display: flex;
  justify-content: center;
  align-items: center;
}

.socials-sidebar a {
  text-decoration: none;
}

.socials-sidebar a:hover {
  opacity: 0.8;
}

.content {
  width: 100%;
  max-width: 1200px; /* Limit content width */
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* Create a 4-column grid */
  grid-template-rows: auto; /* Allow rows to adjust dynamically */
  grid-gap: 20px; /* Add spacing between sections */
  align-items: stretch; /* Stretch items to fill available space */
}

.top-image {
  grid-column: span 4; /* Span all columns */
  max-width: 200px; /* Adjust size as needed */
  max-height: 200px; /* Adjust size as needed */
  border-radius: 50%; /* Make the image circular */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  justify-self: center; /* Center the image horizontally */
}

.text-container {
  grid-column: span 4; /* Make the text container span all columns */
}

.section-container.about-me {
  grid-column: span 2; /* Span 2 columns */
  grid-row: span 1; /* Span 1 row */
}

.section-container.projects {
  grid-column: span 2; /* Span 2 columns */
  grid-row: span 2; /* Span 2 rows */
}

.section-container.skills {
  grid-column: span 1; /* Span 1 column */
  grid-row: span 1; /* Span 1 row */
}

.section-container.contact {
  grid-column: span 1; /* Span 1 column */
  grid-row: span 1; /* Span 1 row */
}

.text-container, .section-container {
  text-align: center;
  background-color: rgba(138, 43, 226, 0.15); /* Less bright semi-transparent violet */
  backdrop-filter: blur(5px); /* Add blur for frosted glass effect */
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
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
