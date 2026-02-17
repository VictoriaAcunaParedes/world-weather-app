<template>
    <div class="card shadow h-100 weather-card">
        <div class="card-header bg-primary text-white text-center">
            <h5 class="mb-0"> {{ city }}</h5>
            <small>{{ country }}</small>
        </div>
        <div class="card-body text-center">
            <h2>{{temperature}}°C</h2>
            <p class="text-muted">{{ description }}</p>
            <ul class="list-group list-group-flush mt-3">
                <li class="list-group-item">Sensacion termica:{{ feels_like }}°C</li>
                <li class="list-group-item">Humedad: {{ humidity }}%</li>
                <li class="list-group-item">Viento: {{ wind_speed }}km/h</li>
            </ul>
        </div>
    </div>
</template>

<script setup>
    defineProps({
        city: String,
        country: String,
        temperature: Number,
        feels_like: Number,
        humidity: Number,
        wind_speed: Number,
        description: String
    })
</script>

<style scoped>
    .weather-card {
        transition: transform 0.2s ease;
    }

    .weather-card:hover {
        transform: translateY(-5px);
    }
</style>