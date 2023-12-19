<script setup>
const props = defineProps(['bg_image'])

</script>

<template>
    <section :style="{ backgroundImage: 'url(' + `src/assets/images/${bg_image}` + ')' }">
    </section>
</template>

<style scoped>
section {
    background-size: cover;
    background-position: center;
    max-width: 100%;
    height: 100vh;
    scroll-snap-align: start;
}
</style>