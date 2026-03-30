<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import gsap from 'gsap'

// Slides following RIO24 guidelines
import HeroSlide from './components/slides/HeroSlide.vue'
import ProductSlide from './components/slides/ProductSlide.vue'
import ProblemSlide from './components/slides/ProblemSlide.vue'
import SolutionSlide from './components/slides/SolutionSlide.vue'
import BusinessModelSlide from './components/slides/BusinessModelSlide.vue'
import InnovationSlide from './components/slides/InnovationSlide.vue'
import FinancialsSlide from './components/slides/FinancialsSlide.vue'
import CompetitiveEdgeSlide from './components/slides/CompetitiveEdgeSlide.vue'
import TeamSlide from './components/slides/TeamSlide.vue'
import AskSlide from './components/slides/AskSlide.vue'

const slides = [
  HeroSlide,
  ProductSlide,
  ProblemSlide,
  SolutionSlide,
  BusinessModelSlide,
  InnovationSlide,
  FinancialsSlide,
  CompetitiveEdgeSlide,
  TeamSlide,
  AskSlide
]

const currentSlide = ref(0)
const isTransitioning = ref(false)
const slideContainer = ref(null)

const goToSlide = (index) => {
  if (isTransitioning.value || index === currentSlide.value) return
  if (index < 0 || index >= slides.length) return
  
  isTransitioning.value = true
  
  const direction = index > currentSlide.value ? 1 : -1
  
  gsap.to(slideContainer.value, {
    opacity: 0,
    y: direction * -30,
    duration: 0.3,
    ease: 'power2.in',
    onComplete: () => {
      currentSlide.value = index
      gsap.fromTo(slideContainer.value, 
        { opacity: 0, y: direction * 30 },
        { 
          opacity: 1, 
          y: 0, 
          duration: 0.4, 
          ease: 'power2.out',
          onComplete: () => {
            isTransitioning.value = false
          }
        }
      )
    }
  })
}

const nextSlide = () => goToSlide(currentSlide.value + 1)
const prevSlide = () => goToSlide(currentSlide.value - 1)

const handleKeydown = (e) => {
  if (e.key === 'ArrowRight' || e.key === ' ') {
    e.preventDefault()
    nextSlide()
  } else if (e.key === 'ArrowLeft') {
    e.preventDefault()
    prevSlide()
  } else if (e.key === 'Home') {
    e.preventDefault()
    goToSlide(0)
  } else if (e.key === 'End') {
    e.preventDefault()
    goToSlide(slides.length - 1)
  }
}

// Touch/swipe support
let touchStartX = 0
let touchStartY = 0

const handleTouchStart = (e) => {
  touchStartX = e.touches[0].clientX
  touchStartY = e.touches[0].clientY
}

const handleTouchEnd = (e) => {
  const touchEndX = e.changedTouches[0].clientX
  const touchEndY = e.changedTouches[0].clientY
  const diffX = touchStartX - touchEndX
  const diffY = touchStartY - touchEndY
  
  if (Math.abs(diffX) > Math.abs(diffY) && Math.abs(diffX) > 50) {
    if (diffX > 0) nextSlide()
    else prevSlide()
  }
}

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
  window.addEventListener('touchstart', handleTouchStart)
  window.addEventListener('touchend', handleTouchEnd)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
  window.removeEventListener('touchstart', handleTouchStart)
  window.removeEventListener('touchend', handleTouchEnd)
})
</script>

<template>
  <div class="presentation">
    <!-- Progress bar -->
    <div class="progress-bar">
      <div 
        class="progress-fill" 
        :style="{ width: `${((currentSlide + 1) / slides.length) * 100}%` }"
      ></div>
    </div>
    
    <!-- Slide counter -->
    <div class="slide-counter">
      {{ currentSlide + 1 }} / {{ slides.length }}
    </div>
    
    <!-- Navigation hints -->
    <div class="nav-hint nav-hint-left" @click="prevSlide" v-show="currentSlide > 0">
      <span>←</span>
    </div>
    <div class="nav-hint nav-hint-right" @click="nextSlide" v-show="currentSlide < slides.length - 1">
      <span>→</span>
    </div>
    
    <!-- Slides container -->
    <div ref="slideContainer" class="slide-container">
      <component :is="slides[currentSlide]" :key="currentSlide" />
    </div>
    
    <!-- Bottom navigation dots -->
    <div class="nav-dots">
      <button 
        v-for="(_, index) in slides" 
        :key="index"
        class="nav-dot"
        :class="{ active: index === currentSlide }"
        @click="goToSlide(index)"
      ></button>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --green: #10B981;
  --green-light: #34D399;
  --green-dark: #059669;
  --orange: #F97316;
  --orange-light: #FB923C;
  --yellow: #F59E0B;
  --dark: #0F172A;
  --gray: #64748B;
  --light: #F1F5F9;
  --white: #FFFFFF;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--dark);
  color: var(--white);
  overflow: hidden;
  -webkit-font-smoothing: antialiased;
}

.presentation {
  width: 100vw;
  height: 100vh;
  position: relative;
  overflow: hidden;
}

.slide-container {
  width: 100%;
  height: 100%;
}

/* Progress bar */
.progress-bar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: rgba(255, 255, 255, 0.1);
  z-index: 1000;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--green) 0%, var(--orange) 100%);
  transition: width 0.3s ease;
}

/* Slide counter */
.slide-counter {
  position: fixed;
  top: 24px;
  right: 24px;
  z-index: 1000;
  font-size: 14px;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.6);
  background: rgba(0, 0, 0, 0.3);
  padding: 8px 16px;
  border-radius: 20px;
  backdrop-filter: blur(10px);
}

/* Navigation hints */
.nav-hint {
  position: fixed;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1000;
  width: 60px;
  height: 120px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.nav-hint:hover {
  opacity: 1;
}

.nav-hint span {
  font-size: 32px;
  color: rgba(255, 255, 255, 0.8);
}

.nav-hint-left {
  left: 20px;
}

.nav-hint-right {
  right: 20px;
}

/* Navigation dots */
.nav-dots {
  position: fixed;
  bottom: 24px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1000;
  display: flex;
  gap: 8px;
}

.nav-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  border: none;
  background: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: all 0.3s ease;
  padding: 0;
}

.nav-dot:hover {
  background: rgba(255, 255, 255, 0.6);
}

.nav-dot.active {
  background: var(--white);
  width: 24px;
  border-radius: 4px;
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .slide-counter {
    top: 12px;
    right: 12px;
    font-size: 12px;
    padding: 6px 12px;
  }
  
  .nav-hint {
    display: none;
  }
  
  .nav-dots {
    bottom: 16px;
    gap: 6px;
  }
  
  .nav-dot {
    width: 6px;
    height: 6px;
  }
  
  .nav-dot.active {
    width: 18px;
  }
}

/* Slide base mobile styles */
@media (max-width: 768px) {
  .slide {
    padding: 20px !important;
  }
  
  .slide h1 {
    font-size: 28px !important;
  }
  
  .slide h2 {
    font-size: 24px !important;
  }
  
  .slide h3 {
    font-size: 18px !important;
  }
  
  .slide p {
    font-size: 14px !important;
  }
}
</style>
