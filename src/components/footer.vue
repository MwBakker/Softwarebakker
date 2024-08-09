<template>
    <div id="footer">
        <img :src=imageUrl />
    </div>
</template>

<script setup>
import { computed } from 'vue';
const imageUrl = computed(
    () => new URL(`../assets/icon/logo.png`, import.meta.url).href
);
</script>

<style scoped>
#footer {
    position: relative;
    height: 32vh;
}

img {
    position: absolute;
    bottom: 0;
    margin: 12px;
    height: 3vh;
}
</style>
