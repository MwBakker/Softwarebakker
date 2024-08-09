<template>
    <Transition :name="'slide-fade-' + direction + ''" :style="'transition-delay:' + delay + 's'">
        <img v-if="isVisible" class="skill" :src="imageUrl">
    </Transition>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
    name: String,
    isVisible: Boolean,
    direction: String,
})

const imageUrl = computed(
    () => new URL(`../assets/icon/${props.name}.png`, import.meta.url).href
);
</script>

<style scoped>
.skill {
    margin: auto 0;
}

img {
    height: 10vh;
}
</style>