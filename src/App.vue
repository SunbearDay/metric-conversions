<script setup lang="ts">
import FahrenheitCelsius from './components/FahrenheitCelsius.vue';
</script>

<template>
  <div class="app">
    <header>
      <h1>Metric Conversions</h1>
    </header>

    <main>
      <FahrenheitCelsius />
    </main>

    <footer>
      <p>Metric Conversions</p>
    </footer>

  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
