<script setup>
import { computed, ref } from 'vue'

const count = ref(0)

const status = computed(() => {
  if (count.value > 0) return 'Positif'
  if (count.value < 0) return 'Négatif'
  return 'Nul'
})

const valueClass = computed(() => {
  if (count.value > 0) return 'positive'
  if (count.value < 0) return 'negative'
  return 'zero'
})

function increment() {
  count.value++
}

function decrement() {
  count.value--
}

function reset() {
  count.value = 0
}
</script>

<template>
  <div class="counter">
    <h1>Compteur Vue.js</h1>
    <p class="value" :class="valueClass">{{ count }}</p>
    <p class="status">{{ status }}</p>
    <div class="actions">
      <button class="minus" type="button" @click="decrement">−</button>
      <button class="reset" type="button" @click="reset">Reset</button>
      <button class="plus" type="button" @click="increment">+</button>
    </div>
  </div>
</template>

<style scoped>
.counter {
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 16px;
  padding: 32px 40px;
  text-align: center;
  min-width: 280px;
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.25);
}

h1 {
  font-size: 1.4rem;
  font-weight: 600;
  margin-bottom: 16px;
}

.value {
  font-size: 4rem;
  font-weight: 700;
  line-height: 1;
  margin-bottom: 8px;
}

.status {
  margin-bottom: 24px;
  font-size: 0.95rem;
  opacity: 0.85;
}

.positive {
  color: #4ade80;
}

.negative {
  color: #f87171;
}

.zero {
  color: #f8fafc;
}

.actions {
  display: flex;
  gap: 10px;
  justify-content: center;
}

button {
  border: none;
  border-radius: 8px;
  padding: 10px 18px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  color: #fff;
  min-width: 52px;
}

button:hover {
  opacity: 0.9;
}

.minus {
  background: #ef4444;
}

.plus {
  background: #22c55e;
}

.reset {
  background: #64748b;
}
</style>
