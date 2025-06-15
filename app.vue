<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
  <Toaster />
</template>

<script setup lang="ts">
import { Toaster } from "vue-sonner";
import "~/assets/css/bg.css";
import "vue-sonner/style.css";

useHead({
  title: "Arvia",
  link: [
    {
      rel: "icon",
      type: "image/svg+xml",
      href: "/favicon.svg",
    },
  ],
});
</script>
