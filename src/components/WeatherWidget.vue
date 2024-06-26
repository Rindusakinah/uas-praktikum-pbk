<template>
  <div class="weather-widget">
    <h2>Cuaca</h2>
    <div class="search-bar">
      <input v-model="city" placeholder="Enter city name" @keyup.enter="getWeather" />
      <button @click="getWeather">Search</button>
    </div>
    <div v-if="weather" class="weather-info">
      <div class="weather-item">
        <p><strong>Location :</strong> {{ weather.name }}</p>
        <img src="../assets/loc.png" alt="location icon" />
        <div class="weather-border"></div>
      </div>
      <div class="weather-item">
        <p><strong>Temperature :</strong> {{ weather.main.temp }}°C</p>
        <img src="../assets/temp.png" alt="temperature icon" />
        <div class="weather-border"></div>
      </div>
      <div class="weather-item">
        <p><strong>Weather :</strong>
          <br> {{ weather.weather[0].description }} </p>
        <img :src="`http://openweathermap.org/img/wn/${weather.weather[0].icon}.png`" alt="weather icon" />
        <div class="weather-border"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const city = ref('')
const weather = ref(null)

const getWeather = async () => {
  const apiKey = 'b15e9858a62c81eadb4c772801a4aa29'
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=${apiKey}`

  try {
    const response = await axios.get(url)
    weather.value = response.data
  } catch (error) {
    console.error(error)
    weather.value = null
  }
}
</script>

<style scoped>
.weather-widget {
  padding: 20px;
  border: 2px solid pink;
  border-radius: 10px;
  max-width: 500px;
  margin: 150px auto;
  text-align: center;
  background: linear-gradient(to right, #ff758c, #ff7eb3);
  box-shadow: 2px 2px 2px pink;
}

.weather-widget h2 {
  color: #ffffff;
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 20px;
}

.search-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.search-bar input {
  padding: 15px;
  width: 70%;
  margin-right: 10px;
  border: 1px solid pink;  
  border-radius: 5px;
  background-color: #ff758c;
  color: #ffffff;
}

::placeholder {
  color: white;
}

.search-bar button {
  padding: 10px;
  border: 1px solid pink;
  background-color: #ff7eb3;
  color: #ffffff;
  cursor: pointer;
  border-radius: 5px;
}

.search-bar button:hover {
  background-color: #ff89a6;
}

.weather-info {
  margin-top: 20px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.weather-item {
  margin: 10px;
  border: 2px solid pink;
  border-radius: 5px;
  padding: 10px;
  flex: 1;
  background-color: #ff758c;
  text-align: center;
  width: 200px;
}

.weather-item img {
  margin-top: 10px;
  width: 35px;
  height: 35px;
}

.weather-item p {
  margin: 0;
  color: #ffffff;
}
</style>
