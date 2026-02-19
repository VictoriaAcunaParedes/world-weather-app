<template>
    <nav class="navbar navbar-expand-lg custom-navbar">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">W W App</a>
            <div class="ms-auto">
                <!-- seleccion de ciudad (1)(2)(3)-->
                <select name="" id="" class="form-select" v-model="selectedCity" @change="emitCity">
                    <option  disabled value="">Selecciona una ciudad</option>
                    <option v-for="city in cities" :key="city.name" :value="city">{{ city.name }}</option>
                </select>
            </div>
        </div>
    </nav>
</template>

<!-- FLUJO
1.selecciono ciudad
2.v-model actualiza selectedCity
3.se ejecuta emitCity
4.evento citySelected
5.appvue recibe ciudad, llama a la api, le pasa los datos a appcard, se muestra la tarjeta -->
<script setup>
import { ref } from 'vue'
import { cities } from '@/data/cities';

const selectedCity = ref("") //(2)
const emit = defineEmits(["citySelected"])

function emitCity() { //(3)
    emit("citySelected", selectedCity.value) //(4)
}

</script>


<style scoped>
.custom-navbar {
    background: #0d6efd;
    padding: 0.8rem 0;
}

.navbar-brand {
    color: white;
}

.navbar-brand:hover {
    color: #dadcdf;
}

.form-select {
    transition: all 0.3s ease;
    }

.form-select:focus {
    box-shadow: 0 0 0 3px rgba(255,255,255,0.35);
    border-color: white;
    outline: none;
    }

</style>
