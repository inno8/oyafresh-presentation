<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const features = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, 
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6 }
  )
  .fromTo(features.value.children, 
    { opacity: 0, scale: 0.9 },
    { opacity: 1, scale: 1, duration: 0.5, stagger: 0.15 },
    '-=0.3'
  )
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="content-center">
        <span class="tag">THE SOLUTION</span>
        <h1 ref="title">
          <span class="gradient-text">OyaFresh</span> Works Like This
        </h1>
        
        <div ref="features" class="solution-steps">
          <div class="step">
            <div class="step-number">1</div>
            <div class="step-icon">📱</div>
            <h3>Browse & Order</h3>
            <p>500+ African products from multiple shops in one app</p>
          </div>
          
          <div class="arrow">→</div>
          
          <div class="step">
            <div class="step-number">2</div>
            <div class="step-icon">🏪</div>
            <h3>Shops Fulfill</h3>
            <p>Partner shops prepare orders (15% commission)</p>
          </div>
          
          <div class="arrow">→</div>
          
          <div class="step">
            <div class="step-number">3</div>
            <div class="step-icon">🚴</div>
            <h3>E-Bike Delivery</h3>
            <p>Next-day delivery, €2.99 fee (free over €50)</p>
          </div>
          
          <div class="arrow">→</div>
          
          <div class="step success">
            <div class="step-number">✓</div>
            <div class="step-icon">🎉</div>
            <h3>Happy Customer</h3>
            <p>Authentic food at home, 3 hours saved</p>
          </div>
        </div>
        
        <div class="value-props">
          <div class="value-prop">
            <strong>For Customers:</strong> Convenience + Authentic Products
          </div>
          <div class="value-prop">
            <strong>For Shops:</strong> New Revenue + Customer Acquisition
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content-center {
  text-align: center;
  max-width: 1400px;
  margin: 0 auto;
}

h1 {
  font-size: 64px;
  font-weight: 800;
  margin-bottom: 64px;
}

.solution-steps {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  margin-bottom: 48px;
}

.step {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 32px 24px;
  min-width: 220px;
  position: relative;
}

.step.success {
  background: linear-gradient(135deg, rgba(16, 185, 129, 0.15) 0%, rgba(249, 115, 22, 0.15) 100%);
  border-color: var(--green);
}

.step-number {
  position: absolute;
  top: -12px;
  left: 20px;
  width: 32px;
  height: 32px;
  background: var(--green);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  font-weight: 700;
  color: var(--white);
}

.step-icon {
  font-size: 48px;
  margin-bottom: 16px;
}

.step h3 {
  font-size: 20px;
  font-weight: 700;
  color: var(--white);
  margin-bottom: 8px;
}

.step p {
  font-size: 14px;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.5;
}

.arrow {
  font-size: 32px;
  color: var(--green);
  font-weight: bold;
}

.value-props {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
  margin-top: 48px;
}

.value-prop {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  padding: 24px;
  font-size: 16px;
  color: rgba(255, 255, 255, 0.9);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.value-prop strong {
  color: var(--green-light);
}

@media (max-width: 1024px) {
  .solution-steps {
    flex-direction: column;
  }
  
  .arrow {
    transform: rotate(90deg);
  }
  
  h1 {
    font-size: 48px;
  }
  
  .value-props {
    grid-template-columns: 1fr;
  }
}
</style>
