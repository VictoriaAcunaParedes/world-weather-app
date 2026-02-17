<template>
  <AppNavbar />
  <AppHero 
    title="The World Weather App"
    subtitle="Consulta el clima actual alrededor del mundo"
  />

  <div class="container mt-5">
    <div class="row g-4">
      <div
        class="col-md-4"
        v-for="city in clima"
        :key="city.id"
      >
        <AppCard
          :city="city.city"
          :country="city.country"
          :temperature="city.temperature"
          :feels_like="city.feels_like"
          :humidity="city.humidity"
          :wind_speed="city.wind_speed"
          :description="city.description"
        />
      </div>
    </div>
  </div>

</template>

<script setup>
import AppCard from './components/AppCard.vue';
import AppHero from './components/AppHero.vue';
import AppNavbar from './components/AppNavbar.vue';
import clima from './data/clima.json'
</script>



<style scoped>
</style>
