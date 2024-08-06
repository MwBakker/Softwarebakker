<template>
    <div id="price">
        <div id="oven">
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
#price {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    text-align: center;
    width: 27.5%;
    border: 1px solid gray;
    border-top: 120px solid transparent;
    border-bottom: 120px solid transparent;
    background-image: url('../assets/icon/oven.png');
    background-position: center;
    background-repeat: no-repeat;
}

#oven {
    width: 68%;
    margin: 32px auto 0 auto;
    background-color: black;
}

#title {
    transition-delay: v-bind(delay);
}

h2 {
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
</style>