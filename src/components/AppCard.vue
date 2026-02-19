<template>
    <div class="card h-100 weather-card text-center">
        <div class="card-header bg-primary text-white">
            <h4 class="mb-0"> {{ city }}</h4>
            <small>{{ date }}</small>
        </div>
        <div class="card-body">
            <!-- CLIMA ACTUAL -->
            <i :class="iconClass" class="weather-icon"></i>
            <h2 class="display-5 fw-bold">{{ currentTemp }} °C</h2>
            <p class="text-uppercase small opacity-75">{{ description }}</p>
            <p> 🌬Viento: {{ windSpeed }} km/h</p>

            <hr>

            <!-- PRONOSTICO MAÑANA -->
            <h5 class="mt-3">Pronostico mañana</h5>
            <p class="mb-1">🌡Max: {{ tomorrowMax }} °C</p>
            <p>🌡Min: {{ tomorrowMin }} °C</p>

        </div>
    </div>
</template>

<script setup>
    defineProps({
        city: String,
        currentTemp: Number,
        windSpeed: Number,
        tomorrowMax: Number,
        tomorrowMin: Number,
        description: String,
        iconClass: String,
        date: String
    })
</script>

<style scoped>

    .weather-card {
        transition: transform 0.2s ease;
        border-radius: 12px;
        max-width: 500px;
        margin: auto;
        box-shadow: 0 10px 25px rgba(0,0,0,0.5);
    }

    .weather-card:hover {
        transform: translateY(-5px);
    }

    .weather-icon {
        font-size: 3rem;
        margin-bottom: 10px;
        transition: transform 0.3s ease;
    }

    .weather-icon:hover {
        transform: scale(1.1);
    }

    .weather-sun {
        color: #ffc107;
    }

    .weather-cloudy {
        color: #b8bbbe;
    }

    .weather-rain {
        color: #0dcaf0;
    }

    .weather-storm {
        color: #f59f00;
    }

    .weather-snow {
        color: #cce3eb;
    }

    .weather-smog {
        color: #adb5bd;
    }  
</style>