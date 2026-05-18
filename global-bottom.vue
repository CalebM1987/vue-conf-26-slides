<template>
  <!-- Soft Vue-tinted radial mesh behind everything -->
  <div class="mesh-bg" aria-hidden="true" />
  <!-- Tiny SVG-noise overlay for tactile texture -->
  <div class="grain" aria-hidden="true" />
</template>

<style scoped>
.mesh-bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
  background:
    radial-gradient(60% 50% at 12% 8%, rgba(66, 211, 146, 0.10) 0%, transparent 70%),
    radial-gradient(50% 45% at 92% 94%, rgba(100, 126, 255, 0.09) 0%, transparent 70%),
    radial-gradient(35% 30% at 88% 14%, rgba(66, 184, 131, 0.05) 0%, transparent 70%);
}

.grain {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
  opacity: 0.05;
  mix-blend-mode: overlay;
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 1  0 0 0 0 1  0 0 0 0 1  0 0 0 1 0'/></filter><rect width='100%' height='100%' filter='url(%23n)'/></svg>");
  background-size: 200px 200px;
}
</style>
