<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const market = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, { opacity: 0, y: 30 }, { opacity: 1, y: 0, duration: 0.6 })
    .fromTo(market.value.children, { opacity: 0, y: 20 }, { opacity: 1, y: 0, duration: 0.5, stagger: 0.1 }, '-=0.3')
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-orange"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">THE MARKET</span>
        <h1 ref="title">
          <span class="gradient-text">€500M</span> Opportunity,<br>
          Zero Competition
        </h1>
        
        <div ref="market" class="market-grid">
          <div class="market-card large">
            <div class="market-label">TAM</div>
            <div class="market-value">€500M</div>
            <div class="market-desc">African diaspora grocery spending in Netherlands annually</div>
          </div>
          
          <div class="market-card">
            <div class="market-label">SAM</div>
            <div class="market-value">€150M</div>
            <div class="market-desc">Online-ready segment (30% of TAM)</div>
          </div>
          
          <div class="market-card">
            <div class="market-label">SOM Year 1</div>
            <div class="market-value">€750K</div>
            <div class="market-desc">0.5% market share, Amsterdam focus</div>
          </div>
          
          <div class="market-card full-width highlight">
            <div class="competitor-section">
              <h3>🎯 First-Mover Advantage</h3>
              <div class="competitor-list">
                <div class="competitor-item">
                  <span class="competitor-name">Picnic</span>
                  <span class="competitor-products">0 African products</span>
                </div>
                <div class="competitor-item">
                  <span class="competitor-name">Flink / AH / Jumbo</span>
                  <span class="competitor-products">5-20 products only</span>
                </div>
                <div class="competitor-item">
                  <span class="competitor-name">African Shops</span>
                  <span class="competitor-products">No delivery capability</span>
                </div>
                <div class="competitor-item success">
                  <span class="competitor-name">OyaFresh</span>
                  <span class="competitor-products">500+ products + delivery ✓</span>
                </div>
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
.market-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
.market-card { background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 20px; padding: 32px; }
.market-card.large { grid-row: span 2; display: flex; flex-direction: column; justify-content: center; }
.market-card.full-width { grid-column: span 3; }
.market-card.highlight { background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%); border-color: var(--green); }
.market-label { font-size: 14px; font-weight: 600; color: var(--green-light); margin-bottom: 8px; letter-spacing: 1px; }
.market-value { font-size: 48px; font-weight: 800; color: var(--white); margin-bottom: 12px; }
.market-desc { font-size: 14px; color: rgba(255, 255, 255, 0.7); line-height: 1.5; }
.competitor-section h3 { font-size: 24px; margin-bottom: 24px; color: var(--white); }
.competitor-list { display: flex; flex-direction: column; gap: 16px; }
.competitor-item { display: flex; justify-content: space-between; align-items: center; padding: 16px 20px; background: rgba(255, 255, 255, 0.03); border-radius: 12px; }
.competitor-item.success { background: rgba(16, 185, 129, 0.1); border: 1px solid var(--green); }
.competitor-name { font-size: 16px; font-weight: 600; color: var(--white); }
.competitor-products { font-size: 14px; color: rgba(255, 255, 255, 0.7); }
@media (max-width: 1024px) {
  .market-grid { grid-template-columns: 1fr; }
  .market-card.full-width { grid-column: span 1; }
  h1 { font-size: 48px; }
}
</style>
