<script setup>
import WeatherForecast from './components/WeatherForecast.vue'
</script>

<template>
  <div class="app">
    <header>
      <h1>Ocean Fish Control</h1>
      <p>A .NET Core Web API with Vue.js Frontend</p>
    </header>
    <main>
      <WeatherForecast />
    </main>
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  padding: 20px;
}

header {
  text-align: center;
  margin-bottom: 40px;
  padding: 20px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

header h1 {
  margin: 0;
  font-size: 2.5em;
}

header p {
  margin: 10px 0 0 0;
  font-size: 1.2em;
  opacity: 0.9;
}

main {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
