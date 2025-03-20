<script setup lang="ts"></script>

<template>
  <main class="main-container">
    <nav class="navbar">
      <ul>
        <li><a href="https://blueskyweb.xyz" target="_blank">Bluesky</a></li>
        <li><a href="https://github.com" target="_blank">GitHub</a></li>
        <li><a href="https://youtube.com" target="_blank">YouTube</a></li>
        <li><a href="https://discord.com" target="_blank">Discord</a></li>
      </ul>
    </nav>
  </main>
</template>

<style scoped>


.navbar {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgba(0, 0, 0, 0.7);
  padding: 10px 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
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
</style>
