<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const team = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, 
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6 }
  )
  .fromTo(team.value.children, 
    { opacity: 0, scale: 0.95 },
    { opacity: 1, scale: 1, duration: 0.5, stagger: 0.1 },
    '-=0.3'
  )
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">THE TEAM</span>
        <h1 ref="title">
          Built by <span class="gradient-text">Proven Founders</span>
        </h1>
        
        <div ref="team" class="team-content">
          <div class="company-section">
            <h2>itec</h2>
            <p class="company-desc">Tech company with <strong>2 live products</strong> serving African diaspora in Netherlands</p>
            
            <div class="products">
              <div class="product-badge">
                <div class="badge-icon">🛒</div>
                <div class="badge-content">
                  <div class="badge-name">oyacompare.com</div>
                  <div class="badge-desc">2,000+ users finding African shops</div>
                </div>
              </div>
              
              <div class="product-badge">
                <div class="badge-icon">🍱</div>
                <div class="badge-content">
                  <div class="badge-name">afrikits.nl</div>
                  <div class="badge-desc">African meal kit subscription platform</div>
                </div>
              </div>
            </div>
          </div>
          
          <div class="team-section">
            <h3>Core Team</h3>
            <div class="team-members">
              <div class="member">
                <div class="member-role">Founder & Software Developer</div>
                <div class="member-name">Yanick Assignon</div>
                <div class="member-skills">Python • Vue.js • Django • Full Stack</div>
              </div>
              
              <div class="member">
                <div class="member-role">DevOps Engineer</div>
                <div class="member-skills">Azure • DigitalOcean • Infrastructure</div>
              </div>
              
              <div class="member">
                <div class="member-role">Data Scientist</div>
                <div class="member-skills">Analytics • Market Research</div>
              </div>
            </div>
          </div>
          
          <div class="advantage-box">
            <h4>🎯 Competitive Advantage</h4>
            <p>Only team with <strong>existing user base (2,000+ customers)</strong> + <strong>shop relationships</strong> + <strong>proven execution</strong> in this market</p>
          </div>
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

.bg-gradient-green {
  position: absolute;
  top: -50%;
  left: -30%;
  width: 80%;
  height: 150%;
  background: radial-gradient(ellipse, rgba(16, 185, 129, 0.2) 0%, transparent 60%);
  pointer-events: none;
}

.slide-content {
  max-width: 1200px;
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
  color: var(--green-light);
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
  background: linear-gradient(135deg, var(--green) 0%, var(--orange) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.team-content {
  display: flex;
  flex-direction: column;
  gap: 32px;
  text-align: left;
}

.company-section {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 32px;
}

.company-section h2 {
  font-size: 32px;
  font-weight: 800;
  color: var(--green);
  margin-bottom: 12px;
}

.company-desc {
  font-size: 18px;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 24px;
}

.company-desc strong {
  color: var(--green-light);
}

.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.product-badge {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px;
  background: rgba(255, 255, 255, 0.03);
  border-radius: 12px;
}

.badge-icon {
  font-size: 32px;
  flex-shrink: 0;
}

.badge-name {
  font-size: 16px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 4px;
}

.badge-desc {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.7);
}

.team-section {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 32px;
}

.team-section h3 {
  font-size: 24px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 24px;
}

.team-members {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.member {
  padding: 20px;
  background: rgba(255, 255, 255, 0.03);
  border-radius: 12px;
}

.member-role {
  font-size: 14px;
  font-weight: 600;
  color: var(--green-light);
  margin-bottom: 8px;
}

.member-name {
  font-size: 18px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 8px;
}

.member-skills {
  font-size: 13px;
  color: rgba(255, 255, 255, 0.6);
}

.advantage-box {
  background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%);
  border: 1px solid var(--green);
  border-radius: 16px;
  padding: 24px 32px;
  text-align: center;
}

.advantage-box h4 {
  font-size: 20px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 12px;
}

.advantage-box p {
  font-size: 16px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.9);
}

.advantage-box strong {
  color: var(--green-light);
}

@media (max-width: 1024px) {
  h1 {
    font-size: 48px;
  }
  
  .products,
  .team-members {
    grid-template-columns: 1fr;
  }
}
</style>
