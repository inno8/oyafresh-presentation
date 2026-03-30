<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const content = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, 
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6 }
  )
  .fromTo(content.value.children, 
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 0.5, stagger: 0.15 },
    '-=0.3'
  )
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">THE PRODUCT</span>
        <h1 ref="title">OyaFresh:<br><span class="gradient-text">African Grocery Delivery</span></h1>
        
        <div ref="content" class="product-grid">
          <div class="product-item">
            <div class="product-number">1</div>
            <h3>What Does It Do?</h3>
            <p>OyaFresh delivers authentic African groceries from local shops to customers' homes via next-day e-bike delivery across Netherlands.</p>
          </div>
          
          <div class="product-item">
            <div class="product-number">2</div>
            <h3>Uniqueness</h3>
            <p><strong>First & only</strong> African grocery delivery platform in Netherlands. Combines Picnic's proven model with cultural specificity.</p>
          </div>
          
          <div class="product-item">
            <div class="product-number">3</div>
            <h3>Why Invest?</h3>
            <p>€500M untapped market, zero competition, validated business model (Picnic profitable), 500K underserved customers.</p>
          </div>
          
          <div class="product-item">
            <div class="product-number">4</div>
            <h3>How Does It Work?</h3>
            <p>Customer orders via app → Partner shops fulfill → E-bike courier delivers next day → 15% commission + €2.99 delivery fee.</p>
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
  right: -30%;
  width: 80%;
  height: 150%;
  background: radial-gradient(ellipse, rgba(16, 185, 129, 0.2) 0%, transparent 60%);
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
  color: var(--green-light);
  text-transform: uppercase;
  margin-bottom: 16px;
}

h1 {
  font-size: 64px;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 64px;
  color: var(--white);
}

.gradient-text {
  background: linear-gradient(135deg, var(--green) 0%, var(--orange) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 32px;
}

.product-item {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 40px 32px;
  text-align: left;
  position: relative;
  transition: all 0.3s ease;
}

.product-item:hover {
  background: rgba(255, 255, 255, 0.08);
  transform: translateY(-4px);
}

.product-number {
  position: absolute;
  top: 24px;
  right: 24px;
  width: 48px;
  height: 48px;
  background: linear-gradient(135deg, var(--green) 0%, var(--green-dark) 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  font-weight: 800;
  color: var(--white);
}

.product-item h3 {
  font-size: 22px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 16px;
}

.product-item p {
  font-size: 16px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
}

.product-item p strong {
  color: var(--green-light);
}

@media (max-width: 1024px) {
  h1 {
    font-size: 48px;
  }
  
  .product-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
}
</style>
