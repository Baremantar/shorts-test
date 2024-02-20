<script setup>
  import Flicking from './components/Flicking.vue';
</script>

<template>
  <main>
    <div class="wrapper">
      <Flicking/>
    </div>
  </main>
</template>

<style scoped>
main {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  main {
    display: flex;
    place-items: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  main .wrapper {
    display: flex;
    justify-content: center;
  }
}
</style>
