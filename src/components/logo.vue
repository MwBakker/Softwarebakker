<template>
    <transition name="grow-logo">
        <div id="logo" v-if="show">
            <img :src=imageUrl>
        </div>
    </transition>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
const imageUrl = computed(
    () => new URL(`../assets/icon/logo-dark.png`, import.meta.url).href
);

const show = ref(false);

onMounted(() => {
    show.value = true;
});

</script>

<style scoped>
#logo {
    position: absolute;
    height: 40vh;
    width: 27.5%;
    background-color: darkcyan;
    border-bottom-right-radius: 85%;
    /* border-right: 1.5px solid rgb(1, 72, 83); */ 

    img {
        display: block;
        height: 22vh;
        margin: auto;
        margin: 5vh 0 0 7%
    }
}

.grow-logo-enter-active {
    animation: growLogo 2s ease;
}

@keyframes growLogo {
    from {
        width: 0;
        height: 0;
    }

    to {
        width: 27.5%;
        height: 40vh;
    }
}

@media (max-width: 1024px) {
    #logo {
        width: 100%;
        border-bottom-left-radius: 25%;
        border-bottom-right-radius: 25%;
        height: 24vh;

        img {
            margin: auto;
        }
    }
}
</style>
