<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const canvasRef = ref<HTMLCanvasElement | null>(null)
const dots = ref<{ x: number; y: number; vx: number; vy: number }[]>([])
const numDots = 350

const mouseX = ref(0)
const mouseY = ref(0)
const isMouseMoving = ref(false)
let mouseMoveTimeout: number | null = null

const handleMouseMove = (event: MouseEvent) => {
  mouseX.value = event.clientX
  mouseY.value = event.clientY
  isMouseMoving.value = true

  if (mouseMoveTimeout) {
    clearTimeout(mouseMoveTimeout)
  }

  mouseMoveTimeout = window.setTimeout(() => {
    isMouseMoving.value = false
  }, 100)
}

const createDots = () => {
  for (let i = 0; i < numDots; i++) {
    dots.value.push({
      x: Math.random() * window.innerWidth,
      y: Math.random() * window.innerHeight,
      vx: (Math.random() - 0.5) * 0.5, // Slow down the speed
      vy: (Math.random() - 0.5) * 0.5, // Slow down the speed
    })
  }
}

const updateDots = () => {
  const canvas = canvasRef.value
  if (!canvas) return
  const ctx = canvas.getContext('2d')
  if (!ctx) return

  // Set canvas size to match window size
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight

  ctx.clearRect(0, 0, canvas.width, canvas.height)

  dots.value.forEach((dot, index) => {
    if (isMouseMoving.value) {
      const dx = mouseX.value - dot.x
      const dy = mouseY.value - dot.y
      const distance = Math.sqrt(dx * dx + dy * dy)
      const maxDistance = 150 // Increase max distance for smoother interaction

      if (distance < maxDistance) {
        const angle = Math.atan2(dy, dx)
        const force = (maxDistance - distance) / maxDistance
        dot.vx += Math.cos(angle) * force * 0.5 // Stronger fluid-like movement closer to the mouse
        dot.vy += Math.sin(angle) * force * 0.5 // Stronger fluid-like movement closer to the mouse
      }
    } else {
      dot.vx += (Math.random() - 0.5) * 0.1 // Random movement
      dot.vy += (Math.random() - 0.5) * 0.1 // Random movement
      dot.vx *= 0.95 // Gradually slow down to normal movement
      dot.vy *= 0.95 // Gradually slow down to normal movement
    }

    // Apply repulsion force between dots
    for (let j = 0; j < dots.value.length && j < 50; j++) {
      if (j !== index) {
        const dx = dot.x - dots.value[j].x
        const dy = dot.y - dots.value[j].y
        const distance = Math.sqrt(dx * dx + dy * dy)
        const minDistance = 20 // Minimum distance to apply repulsion

        if (distance < minDistance) {
          const angle = Math.atan2(dy, dx)
          const force = (minDistance - distance) / minDistance
          dot.vx += Math.cos(angle) * force * 0.01
          dot.vy += Math.sin(angle) * force * 0.01
        }
      }
    }

    dot.x += dot.vx
    dot.y += dot.vy

    // Wrap around to the other side of the screen
    if (dot.x < 0) dot.x = window.innerWidth
    if (dot.x > window.innerWidth) dot.x = 0
    if (dot.y < 0) dot.y = window.innerHeight
    if (dot.y > window.innerHeight) dot.y = 0

    ctx.beginPath()
    ctx.arc(dot.x, dot.y, 2, 0, Math.PI * 2)
    ctx.fillStyle = 'rgba(221, 160, 221, 0.8)' // Change color to purple
    ctx.fill()
  })

  // Increase distance for drawing lines between dots
  for (let i = 0; i < dots.value.length; i++) {
    for (let j = i + 1; j < dots.value.length && j < i + 50; j++) {
      const dx = dots.value[i].x - dots.value[j].x
      const dy = dots.value[i].y - dots.value[j].y
      const distance = Math.sqrt(dx * dx + dy * dy)

      if (distance < 225) {
        // Increase distance to 225
        ctx.beginPath()
        ctx.moveTo(dots.value[i].x, dots.value[i].y)
        ctx.lineTo(dots.value[j].x, dots.value[j].y)
        ctx.strokeStyle = `rgba(221, 160, 221, ${1 - distance / 150})` // Change color to purple
        ctx.stroke()
      }
    }
  }

  requestAnimationFrame(updateDots)
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
  createDots()
  updateDots()
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove)
  dots.value = []
})
</script>

<template>
  <main class="main-container">
    <canvas ref="canvasRef" class="background-canvas"></canvas>
    <nav class="navbar">
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Socials</a></li>
      </ul>
    </nav>
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

.background-canvas {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

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
</style>
