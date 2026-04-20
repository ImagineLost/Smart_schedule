<script>
export default {
    data() {
        return {
            currentTheme: 'light',
            logo: '../assets/img/Logo.png'
        }
    },
    methods: {
    }
}
</script>

<template>
    <header>
    <nav class="navbar light position-sticky top-0 z-3">
        <div class="container">
            <div>
                <a href="#" class="d-flex align-items-center text-decoration-none">
                    <img src="../assets/img/Logo.png" alt="Logo" class="logo">
                    <span>Smart Schedule</span>
                </a>
            </div>
        </div>
    </nav>
    </header>  
</template>

<style> 
.light {
    background-color: #f0f0f0;
    border-bottom: 1px solid #a5a5a5;
}

.logo {
    width: 10%;
    height: 10%;
    margin-right: 5px;
}
</style>
