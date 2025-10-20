<script setup>
import { ref, onMounted } from 'vue'

const weatherData = ref([])
const loading = ref(false)
const error = ref(null)

const fetchWeather = async () => {
  loading.value = true
  error.value = null
  try {
    const response = await fetch('/api/weatherforecast')
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }
    weatherData.value = await response.json()
  } catch (e) {
    error.value = e.message
    console.error('Error fetching weather data:', e)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchWeather()
})
</script>

<template>
  <div class="weather-forecast">
    <h2>Weather Forecast</h2>
    
    <button @click="fetchWeather" :disabled="loading" class="refresh-btn">
      {{ loading ? 'Loading...' : 'Refresh' }}
    </button>

    <div v-if="error" class="error">
      Error: {{ error }}
    </div>

    <div v-if="!loading && weatherData.length > 0" class="weather-list">
      <div v-for="(forecast, index) in weatherData" :key="index" class="weather-item">
        <div class="date">{{ forecast.date }}</div>
        <div class="temp">{{ forecast.temperatureC }}°C / {{ forecast.temperatureF }}°F</div>
        <div class="summary">{{ forecast.summary }}</div>
      </div>
    </div>

    <div v-else-if="!loading && weatherData.length === 0 && !error" class="no-data">
      No weather data available
    </div>
  </div>
</template>

<style scoped>
.weather-forecast {
  padding: 20px;
  max-width: 800px;
  margin: 0 auto;
}

h2 {
  color: #42b883;
  margin-bottom: 20px;
}

.refresh-btn {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  margin-bottom: 20px;
}

.refresh-btn:hover:not(:disabled) {
  background-color: #35a372;
}

.refresh-btn:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

.error {
  color: #ff4444;
  padding: 10px;
  background-color: #ffe6e6;
  border-radius: 4px;
  margin-bottom: 20px;
}

.weather-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 15px;
}

.weather-item {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 15px;
  background-color: #f9f9f9;
  transition: transform 0.2s, box-shadow 0.2s;
}

.weather-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.date {
  font-weight: bold;
  color: #333;
  margin-bottom: 8px;
}

.temp {
  font-size: 18px;
  color: #42b883;
  margin-bottom: 8px;
}

.summary {
  color: #666;
  font-style: italic;
}

.no-data {
  color: #999;
  padding: 20px;
  text-align: center;
}
</style>
