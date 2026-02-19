<template>
    <footer class="footer">
        <div class="container text-center">
            <div class="divider mb-4"></div>
            <h6 class="fw-bold mb-2">W W App</h6>
            <p class="mb-2 small"> App desarrollada con Vue.js consumiendo datos en tiempo real desde 
                <a href="https://open-meteo.com/" target="_blank" class="footer-link">Open-Meteo API</a></p>
            
            <div class="social-icons mb-3">
                <a href="https://github.com/VictoriaAcunaParedes" target="_blank" class="icon-link"><i class="fab fa-github"></i></a>
            </div>
            
        </div>

    </footer>
</template>

<script setup></script>

<style scoped>
    .footer {
    background: #0b5ed7; 
    color: white;
    padding: 2rem 0;
    margin-top: auto;
    }

    .divider {
    width: 250px;
    height: 3px;
    background: white;
    margin: 0 auto;
    border-radius: 5px;
    opacity: 0.6;
    }

    .footer-link {
    color: white;
    text-decoration: underline;
    }

    .footer-link:hover {
    opacity: 0.8;
    }

    .social-icons {
    font-size: 1.6rem;
    }

.icon-link {
    color: white;
    margin: 0 10px;
    transition: transform 0.2s ease, opacity 0.2s ease;
    }

.icon-link:hover {
    transform: translateY(-3px);
    opacity: 0.8;
    }
</style>