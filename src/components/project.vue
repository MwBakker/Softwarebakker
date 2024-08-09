<template>
    <a :href="'https://www.' + link + ''">
        <div class="project">
            <Transition name="slide-fade-up" :style="'transition-delay:' + delay + 's'">
                <img v-if="isVisible" id="heatwave" :src="heatWave">
            </Transition>
            <Transition :name="'slide-fade-' + direction + ''" :style="'transition-delay:' + delay + 's'">
                <img v-if="isVisible" :src="imageUrl">
            </Transition>
            <img id="plate" :src="plate">
        </div>
    </a>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
    name: String,
    link: String,
    isVisible: Boolean,
    direction: String,
    delay: String
})

const imageUrl = computed(
    () => new URL(`../assets/icon/${props.name}.png`, import.meta.url).href
);

const heatWave = computed(
    () => new URL(`../assets/icon/heat.png`, import.meta.url).href
);

const plate = computed(
    () => new URL(`../assets/icon/plate.png`, import.meta.url).href
);
</script>

<style scoped>
.project {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: auto 0;
}

#heatwave {
    width: 96px;
    height: 7vh;
    margin-bottom: 2vh;
    -webkit-animation: mirror 0.65s infinite steps(1, start);
    -webkit-transform: none;
    transform: none;
}

@keyframes mirror {

    0%,
    100% {
        transform: scaleX(1);
    }

    50% {
        transform: scaleX(-1);
    }
}

#plate {
    height: 5vh;
    width: 320px;
    margin-top: 1vh;
    opacity: 80%;
}

img {
    height: 10vh;
}
</style>