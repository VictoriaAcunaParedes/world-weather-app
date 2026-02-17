<template>
    <section class="hero d-flex align-items-center justify-content-center text-center">
        <div>
            <h1 class="display-4 fw-bold">{{ title }}</h1>
            <p class="lead">{{ subtitle }}</p>
        </div>
    </section>
</template>

<script setup>
    defineProps({
        title: String,
        subtitle: String
    })
</script>


<style scoped>
    .hero {
        background: linear-gradient(135deg, #0d6efd, #0dcaf0);
        color: white;
        height: 40vh;
    }
</style>