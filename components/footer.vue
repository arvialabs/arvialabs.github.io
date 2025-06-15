<template>
  <footer class="p-3 max-w-screen-xl mx-auto">
    <div class="bg-primary/90 pt-8 pb-3 px-8 rounded-xl">
      <div class="flex flex-col gap-10">
        <h2 class="text-5xl font-medium font-serif text-blue-300" id="contact">
          Interested? Get in Touch!
        </h2>
        <ContactForm />
        <p class="text-center text-muted-foreground text-sm">
          Made with ❤️ by Arvia Labs | Copyright &copy;
          {{ new Date().getFullYear() }}
        </p>
      </div>
    </div>
  </footer>
</template>
