<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const financials = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, { opacity: 0, y: 30 }, { opacity: 1, y: 0, duration: 0.6 })
    .fromTo(financials.value.children, { opacity: 0, y: 20 }, { opacity: 1, y: 0, duration: 0.5, stagger: 0.1 }, '-=0.3')
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">FINANCIALS</span>
        <h1 ref="title">
          <span class="gradient-text">€38K Profit</span> Year 1,<br>
          Break-Even Month 5
        </h1>
        
        <div ref="financials" class="financials-grid">
          <div class="financial-card highlight">
            <div class="card-icon">📈</div>
            <div class="card-label">Year 1 Revenue</div>
            <div class="card-value">€138K</div>
            <div class="card-detail">11,150 orders • €60 AOV</div>
          </div>
          
          <div class="financial-card">
            <div class="card-icon">💰</div>
            <div class="card-label">Year 1 Profit</div>
            <div class="card-value text-green">€38K</div>
            <div class="card-detail">27% net margin</div>
          </div>
          
          <div class="financial-card">
            <div class="card-icon">⚡</div>
            <div class="card-label">Break-Even</div>
            <div class="card-value">Month 5</div>
            <div class="card-detail">780 orders/month</div>
          </div>
          
          <div class="timeline-card full-width">
            <h3>3-Year Projection</h3>
            <div class="timeline">
              <div class="timeline-item">
                <div class="timeline-year">Year 1</div>
                <div class="timeline-metric">
                  <div class="metric-label">Revenue</div>
                  <div class="metric-value">€138K</div>
                </div>
                <div class="timeline-metric">
                  <div class="metric-label">Profit</div>
                  <div class="metric-value text-green">€38K</div>
                </div>
                <div class="timeline-note">Amsterdam only • 750 customers</div>
              </div>
              
              <div class="timeline-arrow">→</div>
              
              <div class="timeline-item">
                <div class="timeline-year">Year 2</div>
                <div class="timeline-metric">
                  <div class="metric-label">Revenue</div>
                  <div class="metric-value">€300K</div>
                </div>
                <div class="timeline-metric">
                  <div class="metric-label">Profit</div>
                  <div class="metric-value text-green">€60K</div>
                </div>
                <div class="timeline-note">+ Rotterdam • 1,875 customers</div>
              </div>
              
              <div class="timeline-arrow">→</div>
              
              <div class="timeline-item">
                <div class="timeline-year">Year 3</div>
                <div class="timeline-metric">
                  <div class="metric-label">Revenue</div>
                  <div class="metric-value">€750K</div>
                </div>
                <div class="timeline-metric">
                  <div class="metric-label">Profit</div>
                  <div class="metric-value text-green">€165K</div>
                </div>
                <div class="timeline-note">4 cities • 3,750 customers</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content-center { text-align: center; max-width: 1200px; margin: 0 auto; }
h1 { font-size: 64px; font-weight: 800; line-height: 1.2; margin-bottom: 64px; }
.financials-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
.financial-card { background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 20px; padding: 32px; text-align: center; }
.financial-card.highlight { background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%); border-color: var(--green); }
.card-icon { font-size: 48px; margin-bottom: 16px; }
.card-label { font-size: 14px; color: rgba(255, 255, 255, 0.6); margin-bottom: 12px; }
.card-value { font-size: 48px; font-weight: 800; color: var(--white); margin-bottom: 8px; }
.card-value.text-green { color: var(--green); }
.card-detail { font-size: 14px; color: rgba(255, 255, 255, 0.7); }
.timeline-card { grid-column: span 3; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 20px; padding: 40px; }
.timeline-card h3 { font-size: 24px; margin-bottom: 32px; color: var(--white); text-align: center; }
.timeline { display: flex; align-items: center; justify-content: space-between; gap: 24px; }
.timeline-item { flex: 1; background: rgba(255, 255, 255, 0.03); border-radius: 16px; padding: 24px; text-align: center; }
.timeline-year { font-size: 16px; font-weight: 700; color: var(--green); margin-bottom: 16px; }
.timeline-metric { margin-bottom: 12px; }
.metric-label { font-size: 12px; color: rgba(255, 255, 255, 0.6); margin-bottom: 4px; }
.metric-value { font-size: 28px; font-weight: 700; color: var(--white); }
.metric-value.text-green { color: var(--green); }
.timeline-note { font-size: 12px; color: rgba(255, 255, 255, 0.5); margin-top: 12px; }
.timeline-arrow { font-size: 32px; color: var(--green); font-weight: bold; }
@media (max-width: 1024px) {
  .financials-grid { grid-template-columns: 1fr; }
  .timeline-card { grid-column: span 1; }
  .timeline { flex-direction: column; }
  .timeline-arrow { transform: rotate(90deg); }
  h1 { font-size: 48px; }
}
</style>
