<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const roadmap = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, { opacity: 0, y: 30 }, { opacity: 1, y: 0, duration: 0.6 })
    .fromTo(roadmap.value.children, { opacity: 0, scale: 0.95 }, { opacity: 1, scale: 1, duration: 0.5, stagger: 0.15 }, '-=0.3')
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">THE ROADMAP</span>
        <h1 ref="title">
          From <span class="gradient-text">Funding</span><br>
          to Market Leader
        </h1>
        
        <div ref="roadmap" class="roadmap-timeline">
          <div class="phase">
            <div class="phase-label">April 2026</div>
            <div class="phase-title">💰 Secure Funding</div>
            <ul>
              <li>€50K Qredits loan approved</li>
              <li>Finalize shop partnerships (4 shops)</li>
              <li>E-bike fleet procurement</li>
            </ul>
          </div>
          
          <div class="phase-connector">↓</div>
          
          <div class="phase">
            <div class="phase-label">May-July 2026</div>
            <div class="phase-title">🛠️ Build MVP</div>
            <ul>
              <li>iOS/Android app development (3 months)</li>
              <li>Payment integration (Mollie/iDEAL)</li>
              <li>Courier hiring + training (3 staff)</li>
            </ul>
          </div>
          
          <div class="phase-connector">↓</div>
          
          <div class="phase highlight">
            <div class="phase-label">August 2026</div>
            <div class="phase-title">🚀 Soft Launch</div>
            <ul>
              <li>Amsterdam Zuidoost pilot (150 customers)</li>
              <li>Validate operations + logistics</li>
              <li>Gather user feedback</li>
            </ul>
          </div>
          
          <div class="phase-connector">↓</div>
          
          <div class="phase">
            <div class="phase-label">Sept-Dec 2026</div>
            <div class="phase-title">📈 Scale to Break-Even</div>
            <ul>
              <li>Expand to Noord + West Amsterdam</li>
              <li>Reach 780 orders/month (break-even)</li>
              <li>Add 5 more shops</li>
            </ul>
          </div>
          
          <div class="phase-connector">↓</div>
          
          <div class="phase success">
            <div class="phase-label">2027</div>
            <div class="phase-title">🌍 Multi-City Expansion</div>
            <ul>
              <li>Rotterdam launch (120K diaspora)</li>
              <li>The Hague + Utrecht (Year 3)</li>
              <li>€750K revenue by Year 3</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content-center { text-align: center; max-width: 900px; margin: 0 auto; }
h1 { font-size: 64px; font-weight: 800; line-height: 1.2; margin-bottom: 64px; }
.roadmap-timeline { display: flex; flex-direction: column; gap: 16px; }
.phase { background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 16px; padding: 24px 32px; text-align: left; }
.phase.highlight { background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%); border-color: var(--green); }
.phase.success { background: rgba(16, 185, 129, 0.1); border-color: var(--green); }
.phase-label { font-size: 12px; font-weight: 700; letter-spacing: 1px; color: var(--green); margin-bottom: 8px; }
.phase-title { font-size: 22px; font-weight: 700; color: var(--white); margin-bottom: 16px; }
.phase ul { list-style: none; padding: 0; margin: 0; }
.phase li { font-size: 15px; line-height: 1.8; color: rgba(255, 255, 255, 0.8); padding-left: 24px; position: relative; }
.phase li::before { content: "✓"; position: absolute; left: 0; color: var(--green); font-weight: bold; }
.phase-connector { text-align: center; font-size: 28px; color: var(--green); font-weight: bold; }
@media (max-width: 1024px) {
  h1 { font-size: 48px; }
}
</style>
