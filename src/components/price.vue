<template>
    <div id="oven">
        <div id="top-layer"></div>
        <div id="text">
            <Transition id="title" name="slide-fade-up" appear>
                <h2>{{ title }}</h2>
            </Transition>
            <Transition id="stating-transform" name="slide-fade-down" appear>
                <div id="stating">
                    <p id="start">Starting</p>
                    <p id="amount">€
                    <div id="number"></div>
                    <span v-if="perHour"> p/h</span>
                    </p>
                </div>
            </Transition>
        </div>
    </div>
</template>

<script setup>
defineProps({
    title: String,
    amount: String,
    delay: String,
    delay2: String,
    perHour: Boolean,
})
</script>

<style scoped>
#oven {
    text-align: center;
    width: 25%;
    height: 32svh;
    border-radius: 16px;
    opacity: 85%;
    background-color: black;
    background-image: url('../assets/icon/oven.png');
    background-position: center;
    background-size: 100% 100%;
    background-repeat: no-repeat;
}

#top-layer {
    height: 10svh;
}

#title {
    transition-delay: v-bind(delay);
}

h2 {
    color: rgba(217, 250, 215, 0.779);
    margin: 0;
}

#stating-transform {
    transition-delay: v-bind(delay2);
}

p {
    margin: 0;
}

#start {
    font-size: larger;
}

#amount {
    display: flex;
    justify-content: center;
    font-weight: bold;
    color: antiquewhite;
    font-size: calc(2em + 1vmin);
}


@property --num {
    syntax: "<integer>";
    initial-value: 0;
    inherits: false;
}

#number {
    margin-left: 8px;
    animation: counter 2s forwards alternate ease-in-out;
    counter-reset: num var(--num);
}

#number::after {
    content: counter(num);
}

@keyframes counter {
    from {
        --num: 0;
    }

    to {
        --num: v-bind(amount);
    }
}

@media (max-width: 1024px) {
    #oven {
        width: 55%;
        margin: 4vh 0;
    }
}
</style>