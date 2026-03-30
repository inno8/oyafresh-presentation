<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const headline = ref(null)
const subheadline = ref(null)
const stats = ref(null)
const cta = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  
  tl.fromTo(headline.value, 
    { opacity: 0, y: 40 },
    { opacity: 1, y: 0, duration: 0.8, ease: 'power3.out' }
  )
  .fromTo(subheadline.value,
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6, ease: 'power3.out' },
    '-=0.4'
  )
  .fromTo(stats.value,
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 0.5, ease: 'power3.out' },
    '-=0.3'
  )
  .fromTo(cta.value,
    { opacity: 0 },
    { opacity: 1, duration: 0.5 },
    '-=0.2'
  )
})
</script>

<template>
  <div class="slide hero-slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="hero-content">
      <span class="tag">🍌 OYAFRESH</span>
      <h1 ref="headline">
        Bringing African <span class="gradient-text">Groceries</span><br>
        Home to 500,000 People
      </h1>
      <p ref="subheadline" class="subtitle">
        The first dedicated African grocery delivery platform in the Netherlands.<br>
        Next-day e-bike delivery. Authentic products. Zero competitors.
      </p>
      
      <div ref="stats" class="hero-stats">
        <div class="stat-item">
          <div class="stat-value">€500M</div>
          <div class="stat-label">Market Size</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">500K</div>
          <div class="stat-label">African Diaspora</div>
        </div>
        <div class="stat-item">
          <div class="stat-value">0</div>
          <div class="stat-label">Competitors</div>
        </div>
      </div>
      
      <div ref="cta" class="cta-row">
        <span class="cta-hint">
          <span class="arrow">→</span>
          Press to discover how we're solving this
        </span>
      </div>
    </div>
    
    <div class="floating-badge animate-float">
      <span class="badge-icon">🚴</span>
      <span class="badge-text">E-Bike Delivery</span>
    </div>
  </div>
</template>

<style scoped>
.hero-slide {
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-content {
  max-width: 900px;
  text-align: center;
  z-index: 1;
}

h1 {
  font-size: 72px;
  font-weight: 800;
  line-height: 1.1;
  color: var(--white);
  margin-bottom: 24px;
}

.subtitle {
  font-size: 20px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 48px;
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
  margin-bottom: 40px;
}

.stat-item {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: 32px 24px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.stat-value {
  font-size: 48px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--green) 0%, var(--orange) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 8px;
}

.stat-label {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.6);
  font-weight: 500;
}

.cta-row {
  margin-top: 32px;
}

.cta-hint {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  font-size: 16px;
  color: rgba(255, 255, 255, 0.5);
}

.arrow {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
}

.floating-badge {
  position: absolute;
  bottom: 100px;
  right: 100px;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 16px 24px;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
  border-radius: 100px;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.badge-icon {
  font-size: 24px;
}

.badge-text {
  font-size: 14px;
  font-weight: 600;
  color: var(--white);
}

@media (max-width: 1024px) {
  h1 {
    font-size: 48px;
  }
  
  .hero-stats {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  
  .floating-badge {
    bottom: 120px;
    left: 50%;
    transform: translateX(-50%);
  }
}
</style>
