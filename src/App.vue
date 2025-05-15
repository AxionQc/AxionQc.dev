<script setup lang="ts">
import { RouterView } from 'vue-router'
import { ref, onMounted, onUnmounted } from 'vue'

const canvasRef = ref<HTMLCanvasElement | null>(null)
const dots = ref<{ x: number; y: number; vx: number; vy: number }[]>([])
const initialDots = ref<{ x: number; y: number }[]>([]) // Store initial positions
const numDots = ref(0) // Change to a ref to dynamically update

const mouseX = ref(0)
const mouseY = ref(0)
const isMouseMoving = ref(false)
let mouseMoveTimeout: number | null = null

const handleMouseMove = (event: MouseEvent | TouchEvent) => {
  const clientX = event instanceof MouseEvent ? event.clientX : event.touches[0].clientX
  const clientY = event instanceof MouseEvent ? event.clientY : event.touches[0].clientY
  mouseX.value = clientX
  mouseY.value = clientY
  isMouseMoving.value = true

  if (mouseMoveTimeout) {
    clearTimeout(mouseMoveTimeout)
  }

  mouseMoveTimeout = window.setTimeout(() => {
    isMouseMoving.value = false
  }, 100)
}

const handleClick = (event: MouseEvent) => {
  if (event.button === 0) {
    // Check if left mouse button is clicked
    dots.value.forEach((dot, index) => {
      const dx = initialDots.value[index].x - dot.x
      const dy = initialDots.value[index].y - dot.y
      const distance = Math.sqrt(dx * dx + dy * dy)
      const force = 10 / (distance + 1) // Adjust the force of the explosion
      dot.vx += dx * force
      dot.vy += dy * force
    })
  }
}

const createDots = () => {
  dots.value = []
  initialDots.value = [] // Reset initial positions
  for (let i = 0; i < numDots.value; i++) {
    const x = Math.random() * window.innerWidth
    const y = Math.random() * window.innerHeight
    dots.value.push({
      x,
      y,
      vx: (Math.random() - 0.5) * 0.2, // Further slow down the speed
      vy: (Math.random() - 0.5) * 0.2, // Further slow down the speed
    })
    initialDots.value.push({ x, y }) // Store initial positions
  }
}

const updateDots = () => {
  const canvas = canvasRef.value
  if (!canvas) return
  const ctx = canvas.getContext('2d')
  if (!ctx) return

  // Set canvas size to match window sizey
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight

  // Add weak violet background color
  ctx.fillStyle = 'rgba(238, 130, 238, 0.1)'
  ctx.fillRect(0, 0, canvas.width, canvas.height)

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
        dot.vx += Math.cos(angle) * force * 0.2 // Reduce fluid-like movement force
        dot.vy += Math.sin(angle) * force * 0.2 // Reduce fluid-like movement force
      }
    } else {
      dot.vx += (Math.random() - 0.5) * 0.1 // Random movement
      dot.vy += (Math.random() - 0.5) * 0.1 // Random movement
    }

    dot.vx *= 0.98 // Increase damping to slow down movement
    dot.vy *= 0.98 // Increase damping to slow down movement

    // Apply weak repulsion force between dots
    for (let j = 0; j < dots.value.length && j < 20; j++) {
      // Reduced number of interactions
      if (j !== index) {
        const dx = dot.x - dots.value[j].x
        const dy = dot.y - dots.value[j].y
        const distance = Math.sqrt(dx * dx + dy * dy)
        const minDistance = 20 // Minimum distance to apply repulsion

        if (distance < minDistance) {
          const angle = Math.atan2(dy, dx)
          const force = (minDistance - distance) / minDistance
          dot.vx += Math.cos(angle) * force * 0.05 // Further weaken repulsion force
          dot.vy += Math.sin(angle) * force * 0.05 // Further weaken repulsion force
        }
      }
    }

    // Apply force to spread dots more evenly without forming a grid

    dot.x += dot.vx
    dot.y += dot.vy

    // Wrap around to the other side of the screen
    if (dot.x < 0) dot.x = window.innerWidth
    if (dot.x > window.innerWidth) dot.x = 0
    if (dot.y < 0) dot.y = window.innerHeight
    if (dot.y > window.innerHeight) dot.y = 0

    ctx.beginPath()
    ctx.arc(dot.x, dot.y, 2, 0, Math.PI * 2)
    ctx.fillStyle = 'rgba(238, 130, 238, 0.9)' // Change color to violet
    ctx.fill()
  })

  // Increase distance for drawing lines between dots
  for (let i = 0; i < dots.value.length; i++) {
    for (let j = i + 1; j < dots.value.length && j < i + 20; j++) {
      // Reduced number of interactions
      const dx = dots.value[i].x - dots.value[j].x
      const dy = dots.value[i].y - dots.value[j].y
      const distance = Math.sqrt(dx * dx + dy * dy)

      if (distance < 225) {
        // Increase distance to 225
        ctx.beginPath()
        ctx.moveTo(dots.value[i].x, dots.value[i].y)
        ctx.lineTo(dots.value[j].x, dots.value[j].y)
        ctx.strokeStyle = `rgba(238, 130, 238, ${1 - distance / 225})` // Adjust line color to match violet
        ctx.stroke()
      }
    }
  }

  requestAnimationFrame(updateDots)
}

const updateNumDots = () => {
  numDots.value = Math.floor((window.innerWidth * window.innerHeight) / 7500) // Scale number of dots with screen size
  createDots()
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
  window.addEventListener('touchmove', handleMouseMove) // Add touchmove event listener
  window.addEventListener('resize', updateNumDots) // Update number of dots on resize
  window.addEventListener('click', handleClick) // Add click event listener
  updateNumDots()
  updateDots()
})

onUnmounted(() => {
  window.removeEventListener('mousemove', handleMouseMove)
  window.removeEventListener('touchmove', handleMouseMove) // Remove touchmove event listener
  window.removeEventListener('resize', updateNumDots)
  window.removeEventListener('click', handleClick) // Remove click event listener
  dots.value = []
})
</script>

<template>
  <div id="app">
    <canvas ref="canvasRef" class="background-canvas"></canvas>
    <RouterView v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" />
      </transition>
    </RouterView>
  </div>
</template>

<style>
#app {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: auto; /* Enable scrolling */
  display: flex;
  flex-direction: column; /* Ensure proper stacking of elements */
  justify-content: center;
  align-items: center;
}

.background-canvas {
  position: fixed; /* Ensure the canvas stays fixed */
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(176, 91, 250, 0.059); /* Add weak violet background color */
  z-index: -1; /* Ensure canvas stays in the background */
  box-shadow: 0 0 12px rgba(115, 14, 209, 0.5); /* Reduce blur for the canvas glow */
}

#app * {
  box-sizing: border-box; /* Prevent overflow due to padding/margin */
}

.project-column {
  display: flex;
  flex-direction: column;
  width: 100%; /* Ensure it spans the full width */
  overflow-wrap: break-word; /* Prevent text overflow */
}

@media (max-width: 768px) {
  #app {
    font-size: 14px; /* Adjust font size for smaller screens */
    padding: 10px; /* Add padding to prevent text from touching edges */
    overflow-y: auto; /* Ensure vertical scrolling on mobile */
  }

  .background-canvas {
    background-color: rgba(
      176,
      91,
      250,
      0.1
    ); /* Slightly stronger background for better visibility */
  }

  .project-column {
    order: 1; /* Ensure project column is displayed below everything */
    margin-top: 20px; /* Add spacing from other elements */
    align-self: stretch; /* Ensure it spans the full width on mobile */
  }
}
</style>
