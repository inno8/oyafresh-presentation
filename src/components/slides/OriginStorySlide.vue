<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'

const title = ref(null)
const story = ref(null)

onMounted(() => {
  const tl = gsap.timeline()
  tl.fromTo(title.value, 
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 0.6 }
  )
  .fromTo(story.value, 
    { opacity: 0, x: -30 },
    { opacity: 1, x: 0, duration: 0.8 },
    '-=0.3'
  )
})
</script>

<template>
  <div class="slide">
    <div class="bg-gradient bg-gradient-green"></div>
    
    <div class="slide-content">
      <div class="split-layout">
        <div class="left-side">
          <span class="tag">THE STORY</span>
          <h1 ref="title">
            From <span class="gradient-text">oyacompare</span><br>
            to OyaFresh
          </h1>
        </div>
        
        <div ref="story" class="right-side">
          <div class="story-section">
            <div class="year">2024</div>
            <h3>oyacompare Launched</h3>
            <p>Platform helping African diaspora find and compare African shops in Netherlands. 2,000+ registered users.</p>
          </div>
          
          <div class="arrow-down">↓</div>
          
          <div class="story-section">
            <div class="insight-badge">💡 KEY INSIGHT</div>
            <h3>Users Asked: "Can You Deliver?"</h3>
            <ul>
              <li>73% travel >5km to African shops</li>
              <li>Users search for shops then drive 30-60 min</li>
              <li>No one offers delivery for African products</li>
            </ul>
          </div>
          
          <div class="arrow-down">↓</div>
          
          <div class="story-section success">
            <div class="year">2026</div>
            <h3>OyaFresh Born</h3>
            <p><strong>Same customers. Same shops. New service: DELIVERY.</strong></p>
            <p class="highlight">oyacompare proves demand exists. OyaFresh fulfills it.</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.split-layout {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 80px;
  align-items: center;
}

.left-side h1 {
  font-size: 64px;
  font-weight: 800;
  line-height: 1.2;
}

.right-side {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.story-section {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 16px;
  padding: 32px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.story-section.success {
  background: linear-gradient(135deg, rgba(16, 185, 129, 0.1) 0%, rgba(249, 115, 22, 0.1) 100%);
  border-color: var(--green);
}

.year {
  display: inline-block;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 2px;
  color: var(--green);
  background: rgba(16, 185, 129, 0.2);
  padding: 6px 12px;
  border-radius: 6px;
  margin-bottom: 16px;
}

.insight-badge {
  display: inline-block;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 1px;
  color: var(--orange);
  background: rgba(249, 115, 22, 0.2);
  padding: 6px 12px;
  border-radius: 6px;
  margin-bottom: 16px;
}

.story-section h3 {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 16px;
  color: var(--white);
}

.story-section p {
  font-size: 16px;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
}

.story-section ul {
  list-style: none;
  padding: 0;
}

.story-section li {
  font-size: 16px;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.8);
  padding-left: 24px;
  position: relative;
}

.story-section li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: var(--green);
  font-weight: bold;
}

.arrow-down {
  text-align: center;
  font-size: 32px;
  color: var(--green);
}

.highlight {
  color: var(--green-light) !important;
  font-weight: 600;
  margin-top: 12px;
}

@media (max-width: 1024px) {
  .split-layout {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .left-side h1 {
    font-size: 48px;
  }
}
</style>
