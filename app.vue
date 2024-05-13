<template>
  <div class="body">
    <NavBar />
    <NuxtPage />
  </div>
</template>

<style lang="postcss">
@tailwind base;

*{
  color: white;
  font-family: Poppins;
}

.body{
  @apply bg-[--color-bg];
  height: 100%;

}

@layer base {
  :root{
    --color-bg: #04050E;
    --color-primary: #0047FF;
  }
}

</style>
