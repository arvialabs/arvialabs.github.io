<template>
  <ConcentricRings class="w-full">
    <Card
      class="group rounded-none border-primary shadow-lg"
      :style="{
        '--card-color': `var(${color})`,
        '--card-color-alpha': `color-mix(in oklch, var(${color}) 90%, transparent)`,
      }"
    >
      <div class="strip p-6 w-4/5"><component :is="icon" /></div>
      <CardHeader>
        <CardTitle class="text-xl">{{ title }}</CardTitle>
        <CardDescription class="text-muted-foreground">{{
          description
        }}</CardDescription>
      </CardHeader>
    </Card>
  </ConcentricRings>
</template>

<script setup lang="ts">
const { title, description, icon, color } = defineProps<{
  title: string;
  description: string;
  icon: any;
  color: `--${string}`; // CSS variable for color
}>();
</script>

<style scoped>
.group {
  background-color: var(--card-color);
  transition: background-color 0.3s ease-in-out;
}

.group:hover {
  background-color: var(--card-color-alpha);
}

.strip {
  background-color: var(--card-color);
  filter: brightness(0.9);
}
</style>
