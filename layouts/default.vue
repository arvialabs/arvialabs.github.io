<template>
  <div class="min-h-dvh relative">
    <NavigationBar />
    <div class="grid-bg fixed inset-0 -z-10 pointer-events-none" />
    <main class="max-w-screen-xl mx-auto p-3 xl:px-0">
      <slot />
    </main>
    <Footer />
  </div>
</template>
