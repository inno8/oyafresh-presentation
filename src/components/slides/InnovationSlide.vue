<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const innovation = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, 
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6 }
  )
  .fromTo(innovation.value.children, 
    { opacity: 0, x: -30 },
    { opacity: 1, x: 0, duration: 0.5, stagger: 0.1 },
    '-=0.3'
  )
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-orange"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">CREATIVITY & INNOVATION</span>
        <h1 ref="title">
          Technology &<br>
          <span class="gradient-text">Competitive Moats</span>
        </h1>
        
        <div ref="innovation" class="innovation-grid">
          <div class="innovation-card">
            <div class="card-icon">🏗️</div>
            <h3>Technology Backbone</h3>
            <div class="tech-stack">
              <div class="tech-item"><strong>Django + PostgreSQL</strong> • Scalable backend</div>
              <div class="tech-item"><strong>React Native</strong> • Cross-platform mobile app</div>
              <div class="tech-item"><strong>PostGIS</strong> • Geospatial routing optimization</div>
              <div class="tech-item"><strong>Mollie + iDEAL</strong> • Payment integration</div>
            </div>
          </div>
          
          <div class="innovation-card">
            <div class="card-icon">🔒</div>
            <h3>Intellectual Property</h3>
            <ul>
              <li><strong>Proprietary route optimization</strong> for e-bike delivery</li>
              <li><strong>Customer database</strong> (2,000+ from oyacompare)</li>
              <li><strong>Shop partnership agreements</strong> (exclusive early contracts)</li>
              <li><strong>Brand recognition</strong> in African diaspora community</li>
            </ul>
          </div>
          
          <div class="innovation-card highlight">
            <div class="card-icon">🚀</div>
            <h3>Why We're Superior</h3>
            <ul>
              <li><strong>Cultural expertise</strong> — Team understands market deeply</li>
              <li><strong>Existing infrastructure</strong> — oyacompare platform foundation</li>
              <li><strong>Shop relationships</strong> — Trust already established</li>
              <li><strong>First-mover advantage</strong> — 12-18 month head start</li>
            </ul>
          </div>
          
          <div class="innovation-card">
            <div class="card-icon">🛡️</div>
            <h3>Defensibility</h3>
            <ul>
              <li><strong>Network effects</strong> — More shops = more customers = more shops</li>
              <li><strong>High switching costs</strong> — Customers trust our curation</li>
              <li><strong>Capital intensive</strong> — €50K + operational expertise to replicate</li>
              <li><strong>Market knowledge</strong> — Years understanding diaspora needs</li>
            </ul>
          </div>
        </div>
        
        <div class="bottom-note">
          💡 <strong>Picnic took 7 years to profitability.</strong> We leverage their proven model in an underserved niche, reaching break-even in 5 months.
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.slide {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #0F172A 0%, #1E293B 100%);
  padding: 60px;
}

.bg-gradient-orange {
  position: absolute;
  bottom: -40%;
  left: -20%;
  width: 60%;
  height: 120%;
  background: radial-gradient(ellipse, rgba(249, 115, 22, 0.15) 0%, transparent 60%);
  pointer-events: none;
}

.slide-content {
  max-width: 1400px;
  width: 100%;
  z-index: 1;
}

.content-center {
  text-align: center;
}

.tag {
  display: inline-block;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 2px;
  color: var(--orange-light);
  text-transform: uppercase;
  margin-bottom: 16px;
}

h1 {
  font-size: 64px;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 48px;
}

.gradient-text {
  background: linear-gradient(135deg, var(--orange) 0%, var(--green) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.innovation-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
  margin-bottom: 32px;
}

.innovation-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 32px;
  text-align: left;
  transition: all 0.3s ease;
}

.innovation-card:hover {
  background: rgba(255, 255, 255, 0.08);
  transform: translateY(-4px);
}

.innovation-card.highlight {
  background: linear-gradient(135deg, rgba(249, 115, 22, 0.1) 0%, rgba(16, 185, 129, 0.1) 100%);
  border-color: var(--orange);
}

.card-icon {
  font-size: 40px;
  margin-bottom: 16px;
}

.innovation-card h3 {
  font-size: 22px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 20px;
}

.tech-stack {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.tech-item {
  font-size: 15px;
  line-height: 1.5;
  color: rgba(255, 255, 255, 0.8);
  padding-left: 20px;
  position: relative;
}

.tech-item::before {
  content: "▸";
  position: absolute;
  left: 0;
  color: var(--orange);
}

.tech-item strong {
  color: var(--orange-light);
}

.innovation-card ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.innovation-card li {
  font-size: 15px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
  padding-left: 24px;
  position: relative;
}

.innovation-card li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: var(--green);
  font-weight: bold;
}

.innovation-card li strong {
  color: var(--green-light);
}

.bottom-note {
  background: rgba(255, 255, 255, 0.05);
  border-left: 4px solid var(--orange);
  border-radius: 8px;
  padding: 16px 24px;
  font-size: 16px;
  color: rgba(255, 255, 255, 0.9);
  text-align: left;
}

.bottom-note strong {
  color: var(--orange-light);
}

@media (max-width: 1024px) {
  h1 {
    font-size: 48px;
  }
  
  .innovation-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
}
</style>
