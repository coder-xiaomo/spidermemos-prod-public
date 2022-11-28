<script setup>
defineProps({
    text: {
        type: String,
        required: true
    }
})
</script>

<template>
    <div class="navbar-item">
        <span>{{ text }}</span>
    </div>
</template>

<style scoped>
.navbar-item {
    display: inline-block;
    cursor: pointer;
}
</style>
