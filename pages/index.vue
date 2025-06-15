<template>
  <main class="my-24 lg:my-36 flex flex-col gap-20 px-4">
    <section
      class="flex flex-col lg:flex-row lg:items-center lg:justify-between gap-5"
    >
      <div class="flex flex-col gap-2 max-w-prose lg:max-w-3/5">
        <h1 class="text-4xl lg:text-6xl font-medium font-serif">
          Free Your Team From Repetitive Software Work.
        </h1>
        <h3 class="text-lg lg:text-2xl text-muted-foreground">
          Turn any tutorial, manual, or training guide into working automation.
          Let your people focus on the work that actually needs human creativity
          and judgment.
        </h3>
        <div class="flex mt-5 gap-5 items-center">
          <ConcentricRings>
            <NuxtLink to="#contact">
              <Button
                class="w-[150px] md:w-[250px] p-6 rounded-none cursor-pointer"
              >
                Get in Touch!
              </Button>
            </NuxtLink>
          </ConcentricRings>
          <ConcentricRings>
            <NuxtLink to="#how-it-works">
              <Button
                variant="secondary"
                class="w-[150px] border border-primary p-6 rounded-none cursor-pointer"
              >
                How it works?
              </Button>
            </NuxtLink>
          </ConcentricRings>
        </div>
      </div>

      <div class="flex mt-10 lg:mt-0 w-full justify-center">
        <div class="w-[90%] lg:w-full">
          <img
            class="max-w-full h-auto shadow-lg rounded-xl border border-primary"
            src="/images/execution.svg"
            alt="Hero illustration"
          />
        </div>
      </div>
    </section>
    <section class="flex flex-col gap-8" id="features">
      <span class="flex flex-col gap-2">
        <h2 class="text-3xl lg:text-4xl font-medium font-serif max-w-3/5">
          Turn Your Team's Expertise Into Instant Automation
        </h2>
        <h3 class="text-xl max-w-prose text-muted-foreground">
          Extract every step from existing guides, manuals, or have an expert
          record themselves doing the task once. We'll turn it into reliable
          automation that handles those same processes whenever you need.
        </h3>
      </span>
      <ul class="grid grid-cols-1 md:grid-cols-2 gap-5">
        <li v-for="feature in featureList" :key="feature.title">
          <FeatureCard
            :title="feature.title"
            :description="feature.description"
            :icon="feature.icon"
            :color="feature.color as `--${string}`"
          />
        </li>
      </ul>
    </section>
    <section class="flex flex-col gap-8" id="how-it-works">
      <span class="flex flex-col gap-2">
        <h2 class="text-3xl lg:text-4xl font-medium font-serif max-w-3/5">
          Here's How We Make It Happen
        </h2>
        <h3 class="text-xl max-w-prose text-muted-foreground">
          From your existing knowledge to working automation in four simple
          steps. No technical setup required.
        </h3>
      </span>
      <ProcessStepper :steps="processSteps" />
      <div class="w-[90%] lg:w-full flex flex-col items-center">
        <div class="flex items-start gap-5">
          <div>
            <img
              class="max-w-full h-auto shadow-lg rounded-xl border border-primary"
              src="/images/learning-01.svg"
              alt="Learning Module Creation"
            />
          </div>
          <div>
            <img
              class="max-w-full h-auto shadow-lg rounded-xl border border-primary"
              src="/images/learning-02.svg"
              alt="Learning Module Creation"
            />
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup lang="ts">
import {
  SearchIcon,
  CircleCheckBigIcon,
  RefreshCcwIcon,
  WrenchIcon,
} from "lucide-vue-next";

const featureList = [
  {
    icon: SearchIcon,
    color: "--color-orange-100",
    title: "Smart Step Extraction",
    description:
      "Automatically identifies each discrete action sequence from any tutorial or manual.",
  },
  {
    icon: CircleCheckBigIcon,
    color: "--color-violet-100",
    title: "Built-in Validation",
    description:
      "Creates checkpoints to ensure each workflow step completes successfully.",
  },
  {
    icon: RefreshCcwIcon,
    color: "--color-green-100",
    title: "Reusable Modules",
    description:
      "Train once, deploy across your entire team and scale effortlessly.",
  },
  {
    icon: WrenchIcon,
    color: "--color-yellow-100",
    title: "Works With Your Tools",
    description:
      "Integrates seamlessly with the software you already use daily.",
  },
];

const processSteps = [
  {
    step: 1,
    title: "Upload your guide",
    description: "Upload your guide to get started.",
  },
  {
    step: 2,
    title: "Extract steps",
    description: "Extract the steps from your guide.",
  },
  {
    step: 3,
    title: "Review and refine",
    description: "Review and refine the steps.",
  },
  {
    step: 4,
    title: "Create automation",
    description: "Create an automation from the steps.",
  },
];
</script>
