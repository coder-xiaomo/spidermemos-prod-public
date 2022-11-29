<script setup>
defineProps({
    src: {
        type: String,
        required: true
    }
})
</script>

<template>
    <div :style="{ backgroundImage: `url('${src}')` }">
        <slot></slot>
    </div>
</template>

<style scoped>
div {
    width: 100%;
    height: 100%;
    /* background-color: blue; */
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
}
</style>
