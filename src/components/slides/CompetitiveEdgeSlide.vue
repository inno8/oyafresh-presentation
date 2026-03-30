<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const advantages = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, { opacity: 0, y: 30 }, { opacity: 1, y: 0, duration: 0.6 })
    .fromTo(advantages.value.children, { opacity: 0, x: -30 }, { opacity: 1, x: 0, duration: 0.5, stagger: 0.1 }, '-=0.3')
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-orange"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">COMPETITIVE EDGE</span>
        <h1 ref="title">
          Why We'll <span class="gradient-text">Win</span>
        </h1>
        
        <div ref="advantages" class="advantages-list">
          <div class="advantage-card">
            <div class="advantage-icon">🎯</div>
            <div class="advantage-content">
              <h3>First-Mover Advantage</h3>
              <p>12-18 month head start before larger players notice this niche. Time to build defensible moats.</p>
            </div>
          </div>
          
          <div class="advantage-card">
            <div class="advantage-icon">🔗</div>
            <div class="advantage-content">
              <h3>Existing Customer Base</h3>
              <p>2,000+ oyacompare users already searching for African shops. Built-in demand, zero cold start.</p>
            </div>
          </div>
          
          <div class="advantage-card">
            <div class="advantage-icon">🤝</div>
            <div class="advantage-content">
              <h3>Pre-Existing Shop Relationships</h3>
              <p>Partnership with kings Afro Food, Amanksmarket, SPICEBAZAAR via oyacompare. Trust already built.</p>
            </div>
          </div>
          
          <div class="advantage-card">
            <div class="advantage-icon">🌍</div>
            <div class="advantage-content">
              <h3>Cultural Expertise</h3>
              <p>itec team understands African diaspora needs. Not a "generic platform"—built specifically for this community.</p>
            </div>
          </div>
          
          <div class="advantage-card">
            <div class="advantage-icon">💰</div>
            <div class="advantage-content">
              <h3>Cost Efficiency</h3>
              <p>E-bike delivery 3-5x cheaper than van-based delivery in dense urban areas. Sustainable + profitable.</p>
            </div>
          </div>
          
          <div class="advantage-card highlight">
            <div class="advantage-icon">✅</div>
            <div class="advantage-content">
              <h3>Proven Track Record</h3>
              <p><strong>itec has successfully launched oyacompare.com + afrikits.nl.</strong> We execute and deliver.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content-center { text-align: center; max-width: 1000px; margin: 0 auto; }
h1 { font-size: 64px; font-weight: 800; margin-bottom: 64px; }
.advantages-list { display: flex; flex-direction: column; gap: 20px; }
.advantage-card { display: flex; align-items: flex-start; gap: 24px; padding: 24px 32px; background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 16px; text-align: left; transition: all 0.3s ease; }
.advantage-card:hover { background: rgba(255, 255, 255, 0.08); transform: translateX(8px); }
.advantage-card.highlight { background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%); border-color: var(--green); }
.advantage-icon { font-size: 40px; flex-shrink: 0; }
.advantage-content h3 { font-size: 20px; font-weight: 700; color: var(--white); margin-bottom: 8px; }
.advantage-content p { font-size: 16px; line-height: 1.6; color: rgba(255, 255, 255, 0.8); }
@media (max-width: 1024px) {
  h1 { font-size: 48px; }
  .advantage-card { flex-direction: column; text-align: center; }
}
</style>
