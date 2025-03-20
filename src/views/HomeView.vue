<template>
  <main class="main-container">
    <!-- Removed background canvas -->
    <nav class="navbar">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Socials</a></li>
      </ul>
    </nav>
    <div class="text-container">
      <h1>Hi, Come take a look around</h1>
      <p></p>
    </div>
  </main>
</template>

<style scoped>
.main-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  overflow: hidden;
}

/* Removed background canvas styles */

.navbar {
  position: absolute;
  top: 5%;
  left: 50%;
  transform: translate(-50%, 0);
  background-color: rgba(0, 0, 0, 0.7);
  padding: 10px 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  outline: 2px solid rgba(221, 160, 221, 0.5); /* Purple semi-transparent outline */
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 20px;
  margin: 0;
  padding: 0;
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
  text-align: center;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  outline: 2px solid rgba(221, 160, 221, 0.5); /* Purple semi-transparent outline */
  background-color: rgba(87, 22, 191, 0.587); /* Very weak violet tint */
}
</style>
