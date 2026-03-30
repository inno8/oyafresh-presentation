<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const problems = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, 
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6, ease: 'power3.out' }
  )
  .fromTo(problems.value.children, 
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 0.5, stagger: 0.1, ease: 'power3.out' },
    '-=0.3'
  )
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-orange"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">THE PROBLEM</span>
        <h1 ref="title">
          500,000 People,<br>
          <span class="gradient-text">No Solution</span>
        </h1>
        
        <div ref="problems" class="problems-grid">
          <div class="problem-card">
            <div class="problem-icon">🚗</div>
            <div class="problem-stat">30-60 min</div>
            <div class="problem-text">Drive to African shops</div>
            <div class="problem-detail">73% of customers travel >5km for authentic products</div>
          </div>
          
          <div class="problem-card">
            <div class="problem-icon">🛒</div>
            <div class="problem-stat">3 hours</div>
            <div class="problem-text">Every shopping trip</div>
            <div class="problem-detail">Travel + parking + shopping + return home</div>
          </div>
          
          <div class="problem-card">
            <div class="problem-icon">❌</div>
            <div class="problem-stat">0 options</div>
            <div class="problem-text">No delivery platforms</div>
            <div class="problem-detail">Picnic, AH, Flink don't stock African products</div>
          </div>
          
          <div class="problem-card highlight">
            <div class="problem-icon">💡</div>
            <div class="problem-stat">High Pain</div>
            <div class="problem-text">7.3/10 severity score</div>
            <div class="problem-detail">= High willingness to pay for solution</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content-center {
  text-align: center;
  max-width: 1200px;
  margin: 0 auto;
}

h1 {
  font-size: 64px;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 64px;
}

.problems-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}

.problem-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  padding: 32px 24px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: transform 0.3s ease;
}

.problem-card:hover {
  transform: translateY(-8px);
}

.problem-card.highlight {
  background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%);
  border-color: var(--green);
}

.problem-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.problem-stat {
  font-size: 32px;
  font-weight: 800;
  color: var(--orange);
  margin-bottom: 8px;
}

.problem-text {
  font-size: 18px;
  font-weight: 600;
  color: var(--white);
  margin-bottom: 12px;
}

.problem-detail {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.6);
  line-height: 1.5;
}

@media (max-width: 1024px) {
  .problems-grid {
    grid-template-columns: 1fr 1fr;
  }
  
  h1 {
    font-size: 48px;
  }
}
</style>
