<template>
  <main class="main-container">
    <nav class="navbar">
      <ul>
        <li>
          <a href="https://bsky.app/profile/axionqc.dev" target="_blank">
            <svg
              viewBox="-50 -50 430 390"
              aria-hidden="true"
              style="width: 18px; height: 18px; vertical-align: middle; fill: #00acee"
            >
              <path
                d="M180 141.964C163.699 110.262 119.308 51.1817 78.0347 22.044C38.4971 -5.86834 23.414 -1.03207 13.526 3.43594C2.08093 8.60755 0 26.1785 0 36.5164C0 46.8542 5.66748 121.272 9.36416 133.694C21.5786 174.738 65.0603 188.607 105.104 184.156C107.151 183.852 109.227 183.572 111.329 183.312C109.267 183.642 107.19 183.924 105.104 184.156C46.4204 192.847 -5.69621 214.233 62.6582 290.33C137.848 368.18 165.705 273.637 180 225.702C194.295 273.637 210.76 364.771 295.995 290.33C360 225.702 313.58 192.85 254.896 184.158C252.81 183.926 250.733 183.645 248.671 183.315C250.773 183.574 252.849 183.855 254.896 184.158C294.94 188.61 338.421 174.74 350.636 133.697C354.333 121.275 360 46.8568 360 36.519C360 26.1811 357.919 8.61012 346.474 3.43851C336.586 -1.02949 321.503 -5.86576 281.965 22.0466C240.692 51.1843 196.301 110.262 180 141.964Z"
              ></path>
            </svg>
            Bluesky
          </a>
        </li>
        <li>
          <a href="https://github.com/AxionQc" target="_blank"
            ><i class="fab fa-github" style="color: #333"></i> GitHub</a
          >
        </li>
        <li>
          <a href="https://youtube.com/@AxionQc" target="_blank"
            ><i class="fab fa-youtube" style="color: #ff0000"></i> YouTube</a
          >
        </li>
        <li>
          <a href="https://discord.com/users/805461441514700820" target="_blank"
            ><i class="fab fa-discord" style="color: #7289da"></i> Discord</a
          >
        </li>
        <li>
          <a href="https://www.reddit.com/user/AxiosTheProot" target="_blank"
            ><i class="fab fa-reddit" style="color: #ff4500"></i> Reddit</a
          >
        </li>
        <li>
          <a href="https://steamcommunity.com/profiles/76561199097361562/" target="_blank"
            ><i class="fab fa-steam" style="color: #00adee"></i> Steam</a
          >
        </li>
      </ul>
    </nav>
    <div class="text-container">
      <p>You can contact me whenever.</p>
    </div>
  </main>
</template>

<style scoped>
.main-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  position: relative;
}

.navbar {
  position: absolute;
  top: 50%;
  left: 10%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.7);
  padding: 20px 20px; /* Adjust padding to fit content */
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  height: auto; /* Adjust height to fit content */
  border: 2px solid #dda0dd; /* Violet purple outline */
}

.navbar ul {
  list-style: none;
  display: flex;
  flex-direction: column; /* Change to column to fit items vertically */
  justify-content: space-between;
  height: 100%;
  margin: 0;
  padding: 0;
  gap: 10px; /* Add gap between items */
}

.navbar a {
  color: #fff;
  text-decoration: none;
  font-size: 18px;
}

.navbar a:hover {
  color: #dda0dd; /* Violet purple color */
}

.text-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgba(0, 0, 0, 0.7);
  padding: 20px 40px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  color: #fff;
  text-align: center;
  border: 3px solid #dda0dd; /* Violet purple outline */
}

@media (max-width: 600px) {
  .navbar {
    position: static;
    transform: none;
    margin-top: 50px; /* Further increase margin to lower the navbar */
    margin-bottom: 0px; /* Further increase margin to lower the navbar */
  }

  .text-container {
    position: static;
    transform: none;
    margin-top: 40px; /* Increase margin to lower the text container */
  }

  .main-container {
    flex-direction: column;
    justify-content: flex-start;
    padding: 20px;
    padding-top: 80px; /* Increase padding to lower everything */
  }
}
</style>
