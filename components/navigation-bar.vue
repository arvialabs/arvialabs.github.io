<template>
  <header class="fixed w-full p-3 z-20">
    <div
      class="max-w-screen-xl px-8 py-4 mx-auto bg-primary/75 shadow-lg backdrop-blur-sm rounded-xl"
    >
      <div class="flex items-center justify-between">
        <NuxtLink to="/">
          <h3 class="text-2xl font-medium font-serif text-background">Arvia</h3>
        </NuxtLink>
        <nav>
          <NuxtLink
            v-for="link in links"
            :key="link.name"
            :to="link.href"
            class="text-sm md:text-base text-background hover:text-blue-300 px-2 md:px-4 py-2"
            >{{ link.name }}</NuxtLink
          >
        </nav>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
const links = [
  { name: "How it Works?", href: "#how-it-works" },
  { name: "Contact Us", href: "#contact" },
];

const isActive = ref(false);
const currentLink = ref("");
</script>
