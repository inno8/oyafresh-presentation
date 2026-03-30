<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const ask = ref(null)
const contact = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, { opacity: 0, y: 40 }, { opacity: 1, y: 0, duration: 0.8 })
    .fromTo(ask.value, { opacity: 0, scale: 0.95 }, { opacity: 1, scale: 1, duration: 0.6 }, '-=0.4')
    .fromTo(contact.value, { opacity: 0 }, { opacity: 1, duration: 0.5 }, '-=0.2')
})
</script>

<template>
  <div class="slide final-slide">
    <div class="bg-gradient bg-gradient-green"></div>
    <div class="bg-gradient bg-gradient-orange"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <h1 ref="title">
          Let's Bring<br>
          <span class="gradient-text">African Groceries</span><br>
          Home
        </h1>
        
        <div ref="ask" class="ask-box">
          <div class="ask-amount">€50,000</div>
          <div class="ask-purpose">Qredits Microloan</div>
          
          <div class="use-of-funds">
            <div class="fund-item">
              <span class="fund-label">Platform Development</span>
              <span class="fund-value">€12K (24%)</span>
            </div>
            <div class="fund-item">
              <span class="fund-label">E-Bike Fleet</span>
              <span class="fund-value">€9K (18%)</span>
            </div>
            <div class="fund-item">
              <span class="fund-label">Courier Salaries</span>
              <span class="fund-value">€13.5K (27%)</span>
            </div>
            <div class="fund-item">
              <span class="fund-label">Marketing</span>
              <span class="fund-value">€8K (16%)</span>
            </div>
            <div class="fund-item">
              <span class="fund-label">Operations + Reserve</span>
              <span class="fund-value">€7.5K (15%)</span>
            </div>
          </div>
          
          <div class="roi-section">
            <h3>Return on Investment</h3>
            <div class="roi-stats">
              <div class="roi-stat">
                <div class="roi-label">Break-Even</div>
                <div class="roi-value">Month 5</div>
              </div>
              <div class="roi-stat">
                <div class="roi-label">Year 1 Profit</div>
                <div class="roi-value">€38K</div>
              </div>
              <div class="roi-stat">
                <div class="roi-label">3-Year Profit</div>
                <div class="roi-value">€263K</div>
              </div>
            </div>
          </div>
        </div>
        
        <div ref="contact" class="contact-section">
          <div class="contact-info">
            <div class="contact-name">Yanick Assignon</div>
            <div class="contact-title">Founder, itec</div>
            <div class="contact-details">
              <div class="contact-item">📧 yanick007.dev@gmail.com</div>
              <div class="contact-item">🌐 oyacompare.com | afrikits.nl</div>
            </div>
          </div>
          
          <div class="cta-final">
            <div class="cta-text">Let's serve 500,000 people together 🚀</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.final-slide { background: linear-gradient(135deg, #0F172A 0%, #1E293B 50%, #0F172A 100%); }
.content-center { text-align: center; max-width: 1000px; margin: 0 auto; }
h1 { font-size: 72px; font-weight: 800; line-height: 1.1; margin-bottom: 48px; }
.ask-box { background: rgba(255, 255, 255, 0.05); backdrop-filter: blur(20px); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 24px; padding: 48px; margin-bottom: 48px; }
.ask-amount { font-size: 72px; font-weight: 800; background: linear-gradient(135deg, var(--green) 0%, var(--orange) 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; margin-bottom: 12px; }
.ask-purpose { font-size: 24px; color: rgba(255, 255, 255, 0.8); font-weight: 600; margin-bottom: 40px; }
.use-of-funds { display: flex; flex-direction: column; gap: 12px; margin-bottom: 40px; }
.fund-item { display: flex; justify-content: space-between; align-items: center; padding: 16px 20px; background: rgba(255, 255, 255, 0.03); border-radius: 12px; }
.fund-label { font-size: 16px; color: rgba(255, 255, 255, 0.9); }
.fund-value { font-size: 16px; font-weight: 700; color: var(--green); }
.roi-section { background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%); border-radius: 16px; padding: 32px; }
.roi-section h3 { font-size: 20px; font-weight: 700; color: var(--white); margin-bottom: 24px; }
.roi-stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }
.roi-stat { text-align: center; }
.roi-label { font-size: 14px; color: rgba(255, 255, 255, 0.6); margin-bottom: 8px; }
.roi-value { font-size: 32px; font-weight: 800; color: var(--green); }
.contact-section { background: rgba(255, 255, 255, 0.03); border-radius: 20px; padding: 32px; }
.contact-name { font-size: 32px; font-weight: 700; color: var(--white); margin-bottom: 8px; }
.contact-title { font-size: 18px; color: var(--green-light); margin-bottom: 24px; }
.contact-details { display: flex; flex-direction: column; gap: 12px; margin-bottom: 32px; }
.contact-item { font-size: 16px; color: rgba(255, 255, 255, 0.8); }
.cta-final { padding-top: 24px; border-top: 1px solid rgba(255, 255, 255, 0.1); }
.cta-text { font-size: 24px; font-weight: 600; background: linear-gradient(135deg, var(--green) 0%, var(--orange) 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
@media (max-width: 1024px) {
  h1 { font-size: 48px; }
  .ask-amount { font-size: 56px; }
  .roi-stats { grid-template-columns: 1fr; }
}
</style>
