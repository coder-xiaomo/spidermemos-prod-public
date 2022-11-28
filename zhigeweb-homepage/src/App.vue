<script setup>
import TheWelcome from './components/TheWelcome.vue'
import Navbar from './components/header/Navbar.vue';
</script>

<template>
    <header>
        <Navbar />
    </header>
    <main>
        <TheWelcome />
    </main>
</template>

<style scoped>
header {
    height: 48px;
    width: 100%;
    padding: 0 30px;
    padding: 0 6vw;
    box-shadow: 0 2px 10px 0 rgb(0 0 0 / 10%);
}

main {
    max-width: 960px;
}

@media (min-width: 760px) {
    header {
        padding: 0 96px;
        padding: 0 10vw;
    }
}

/* @media (min-width: 960px) {
  header {
    padding: 0 110px;
    padding: 0 14vw;
  }
} */
</style>
