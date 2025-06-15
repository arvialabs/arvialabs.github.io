<template>
  <div class="relative group inline-block">
    <div
      v-for="i in 3"
      :key="i"
      class="concentric"
      :class="borderClass"
      :style="`--n:${i}`"
    />
    <slot />
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  variant?: "primary" | "secondary";
}>();

const borderClass = computed(() =>
  props.variant === "secondary"
    ? "border border-secondary"
    : "border border-primary",
);
</script>

<style scoped>
.concentric {
  --step: 3px;
  position: absolute;
  inset: 0;
  z-index: -1;
  pointer-events: none;

  transform: translate3d(calc(var(--n) * 0px), calc(var(--n) * 0px), 0);

  transition: transform 0.25s ease-out;
  will-change: transform;
}

.group:hover .concentric {
  transform: translate3d(
    calc(var(--n) * var(--step)),
    calc(var(--n) * var(--step)),
    0
  );
}
</style>
