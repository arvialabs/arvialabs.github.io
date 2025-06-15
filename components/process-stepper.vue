<template>
  <div class="flex flex-col md:flex-row gap-5 md:gap-2">
    <div
      class="flex flex-row md:flex-col flex-1 items-center md:items-start gap-2"
      v-for="step in steps"
      :key="step.step"
    >
      <Button class="rounded-full p-7 text-xl font-bold" size="icon">{{
        step.step
      }}</Button>
      <div>
        <div class="font-semibold text-lg">{{ step.title }}</div>
        <div class="text-muted-foreground">
          {{ step.description }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const { steps } = defineProps<{
  steps: {
    step: number;
    title: string;
    description: string;
  }[];
}>();
</script>
