<template>
    <nav class="navbar navbar-expand-lg custom-navbar">
        <div class="container">
            <a class="navbar-brand fw-bold" href="#">W W App</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup"
                aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse justify-content-end" id="navbarNavAltMarkup">
                <ul class="navbar-nav">
                    <li class="nav-item"><a class="nav-link active-link" href="#">Inicio</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Ciudades</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Contacto</a></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script setup>
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
    color: #f8f9fa;
}

.nav-link {
    color: white;
    transition: opacity 0.2s ease;
}

.nav-link:hover {
    opacity: 0.7;
}

.active-link {
    font-weight: bold;
    border-bottom: 2px solid white;
}
</style>
