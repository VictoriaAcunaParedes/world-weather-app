<template>
  <div class="app-wrapper">
    <!-- evento @ que ejecuta la funcion fetch -->
    <AppNavbar @citySelected="fetchWeather" />
    <AppHero title="The World Weather App" subtitle="Consulta el clima actual alrededor del mundo" />

    <div class="container my-5 py-4 flex-grow-1 text-center">
      <!-- empty state, para cuando aun no recibo los datos del clima(no hay card) -->
      <div v-if="!weatherData" class="empty-state py-5">
        <i class="fas fa-cloud-sun empty-icon mb-3"></i>
        <h5 class="fw-bold text-white">Busca una ciudad</h5>
        <p class="text-light small"> Escoge una ciudad desde el buscador para ver el clima actual</p>
      </div>
      <transition name="fade-slide"> 
        <!-- con v-if se muestra la card solo cuando hay datos -->
        <div v-if="weatherData"> 
          <!-- datos procesados para la appcard (props)-->
          <AppCard 
            :city="selectedCityName" 
            :currentTemp="weatherData.current_weather.temperature"
            :windSpeed="weatherData.current_weather.windspeed" 
            :tomorrowMax="weatherData.daily.temperature_2m_max[1]"
            :tomorrowMin="weatherData.daily.temperature_2m_min[1]"
            :description="translateWeatherCode(weatherData.current_weather.weathercode)"
            :iconClass="getWeatherIcon(weatherData.current_weather.weathercode)"
            :date="new Date(weatherData.current_weather.time).toLocaleDateString()" />
        </div>
      </transition>
      
    </div>
    <AppFooter />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import AppCard from './components/AppCard.vue';
import AppHero from './components/AppHero.vue';
import AppNavbar from './components/AppNavbar.vue';
import AppFooter from './components/AppFooter.vue';

const weatherData = ref(null)
const selectedCityName = ref("")

// guardo el nombre de la ciudad seleccionada y vamos con la peticion fetch
async function fetchWeather(city) {
  selectedCityName.value = city.name

  const url = `https://api.open-meteo.com/v1/forecast?latitude=${city.lat}&longitude=${city.lon}&daily=temperature_2m_max,temperature_2m_min&current_weather=true&timezone=auto`

  const response = await fetch(url)
  const data = await response.json()
  weatherData.value = data
}

// convierto codigo numerico de la API en descripcion clara
function translateWeatherCode(code) {
  const codes = {
    0: "Despejado",
    1: "Mayormente despejado",
    2: "Parcialmente nublado",
    3: "Nublado",
    45: "Niebla",
    48: "Niebla con escarcha",
    51: "Llovizna",
    61: "Lluvia ligera",
    63: "Lluvia moderada",
    65: "Lluvia intensa",
    71: "Nieve ligera",
    80: "Chubascos"
  }
  return codes[code] || "Clima variable"
}

// mapeo de codigo de API a clases de fontawesome
function getWeatherIcon(code) {
  if (code >= 95) { return "fas fa-bolt weather-storm" } //tormenta
  if (code >= 71 && code <= 77) {return "fas fa-snowflake weather-snow"} //nieve
  if (code >= 51 && code <= 67) {return "fas fa-cloud-rain weather-rain"} //lluvia
  if (code === 45 || code === 48) {return "fas fa-smog weather-smog"} //niebla
  if (code >= 1 && code <= 3) {return "fas fa-cloud-sun weather-cloudy"} //nubes
  if (code === 0) {return "fas fa-sun weather-sun"} //soleado

  return "fas fa-cloud weather-cloudy"
}
</script>


<!-- PENDIENTE ! Mover estilos globales -->
<style>
  html, body, #app {
    height: 100%;
    background-color: #0b5ed7;
  }

  .app-wrapper {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .empty-icon {
    font-size: 3rem;
    opacity: 0.8;
    color: white;
  }
/* transition */
  .fade-slide-enter-active {
    transition: all 0.4s ease;
  }

.fade-slide-enter-from {
    opacity: 0;
    transform: translateY(15px);
  }
</style>
