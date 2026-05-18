<script setup lang="ts">
import { useNav } from '@slidev/client'
const { currentSlideNo, total } = useNav()
</script>

<template>
  <!-- Brand mark + slide counter, suppressed on the cover slide -->
  <div v-if="currentSlideNo > 1" class="brand-mark" aria-hidden="true">
    <span class="dot" />
    <span class="title">Stop Using One AI Tool for Everything</span>
    <span class="sep">·</span>
    <span class="num">{{ String(currentSlideNo).padStart(2, '0') }} / {{ String(total).padStart(2, '0') }}</span>
  </div>
</template>

<style scoped>
.brand-mark {
  position: absolute;
  bottom: 0.9rem;
  right: 1.25rem;
  display: flex;
  align-items: center;
  gap: 0.55rem;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted, #8896a8);
  opacity: 0.55;
  z-index: 100;
  pointer-events: none;
}

.dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--vue-green-light, #42d392);
  box-shadow: 0 0 8px var(--vue-green-light, #42d392);
}

.sep {
  opacity: 0.4;
}

.num {
  color: var(--vue-green-light, #42d392);
}
</style>
