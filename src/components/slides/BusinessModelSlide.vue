<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const model = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, { opacity: 0, y: 30 }, { opacity: 1, y: 0, duration: 0.6 })
    .fromTo(model.value.children, { opacity: 0, scale: 0.95 }, { opacity: 1, scale: 1, duration: 0.5, stagger: 0.1 }, '-=0.3')
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">BUSINESS MODEL</span>
        <h1 ref="title">How We <span class="gradient-text">Make Money</span></h1>
        
        <div ref="model" class="model-layout">
          <div class="revenue-streams">
            <h3>Revenue Streams</h3>
            <div class="revenue-item">
              <div class="revenue-icon">🏪</div>
              <div class="revenue-details">
                <div class="revenue-name">Shop Commission</div>
                <div class="revenue-value">15%</div>
                <div class="revenue-desc">€9 per €60 order</div>
              </div>
            </div>
            <div class="revenue-item">
              <div class="revenue-icon">🚴</div>
              <div class="revenue-details">
                <div class="revenue-name">Delivery Fee</div>
                <div class="revenue-value">€2.99</div>
                <div class="revenue-desc">Free over €50</div>
              </div>
            </div>
            <div class="revenue-total">
              <strong>Avg Revenue/Order:</strong> €12.42
            </div>
          </div>
          
          <div class="unit-economics">
            <h3>Unit Economics</h3>
            <div class="economics-breakdown">
              <div class="econ-row">
                <span>Revenue per order</span>
                <span class="positive">€12.42</span>
              </div>
              <div class="econ-row">
                <span>Cost per order</span>
                <span class="negative">-€3.50</span>
              </div>
              <div class="econ-row total">
                <span><strong>Contribution Margin</strong></span>
                <span class="positive"><strong>€9.44</strong></span>
              </div>
              <div class="econ-detail">
                76% gross margin - Highly profitable model
              </div>
            </div>
          </div>
          
          <div class="picnic-validation full-width">
            <h3>🎯 Validated by Picnic</h3>
            <p>Picnic achieved profitability using the same model: next-day delivery + e-bike fleet + regular routes.</p>
            <div class="picnic-stats">
              <div class="picnic-stat">
                <div class="stat-value">€2B</div>
                <div class="stat-label">Picnic Revenue</div>
              </div>
              <div class="picnic-stat">
                <div class="stat-value">2023</div>
                <div class="stat-label">Break-Even Year</div>
              </div>
              <div class="picnic-stat">
                <div class="stat-value">3 years</div>
                <div class="stat-label">To Profitability</div>
              </div>
            </div>
            <p class="highlight">We're applying a proven, profitable model to an underserved niche.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content-center { text-align: left; max-width: 1200px; margin: 0 auto; }
h1 { font-size: 64px; font-weight: 800; margin-bottom: 64px; text-align: center; }
.model-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
.revenue-streams, .unit-economics, .picnic-validation { background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 20px; padding: 32px; }
.revenue-streams h3, .unit-economics h3, .picnic-validation h3 { font-size: 24px; margin-bottom: 24px; color: var(--white); }
.revenue-item { display: flex; align-items: center; gap: 16px; padding: 16px; background: rgba(255, 255, 255, 0.03); border-radius: 12px; margin-bottom: 16px; }
.revenue-icon { font-size: 32px; }
.revenue-name { font-size: 14px; color: rgba(255, 255, 255, 0.7); margin-bottom: 4px; }
.revenue-value { font-size: 24px; font-weight: 700; color: var(--green); }
.revenue-desc { font-size: 12px; color: rgba(255, 255, 255, 0.5); }
.revenue-total { margin-top: 16px; padding: 16px; background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%); border-radius: 12px; font-size: 16px; color: var(--white); }
.economics-breakdown { display: flex; flex-direction: column; gap: 12px; }
.econ-row { display: flex; justify-content: space-between; align-items: center; padding: 12px; background: rgba(255, 255, 255, 0.03); border-radius: 8px; font-size: 16px; }
.econ-row.total { background: rgba(16, 185, 129, 0.1); border: 1px solid var(--green); }
.econ-detail { margin-top: 16px; font-size: 14px; color: rgba(255, 255, 255, 0.7); text-align: center; }
.positive { color: var(--green); font-weight: 600; }
.negative { color: var(--orange); font-weight: 600; }
.full-width { grid-column: span 2; }
.picnic-validation { background: linear-gradient(135deg, rgba(16, 185, 129, 0.08) 0%, rgba(249, 115, 22, 0.08) 100%); border-color: var(--green); }
.picnic-validation p { font-size: 16px; line-height: 1.6; color: rgba(255, 255, 255, 0.9); margin-bottom: 24px; }
.picnic-stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin: 24px 0; }
.picnic-stat { text-align: center; padding: 20px; background: rgba(255, 255, 255, 0.05); border-radius: 12px; }
.stat-value { font-size: 32px; font-weight: 800; color: var(--green); margin-bottom: 8px; }
.stat-label { font-size: 12px; color: rgba(255, 255, 255, 0.6); }
.highlight { color: var(--green-light) !important; font-weight: 600; margin-top: 16px; }
@media (max-width: 1024px) {
  .model-layout { grid-template-columns: 1fr; }
  .full-width { grid-column: span 1; }
  h1 { font-size: 48px; }
}
</style>
