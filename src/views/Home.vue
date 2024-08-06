<template>
    <div id="home">
        <div id="head">
            <Logo />
            <Intro />
        </div>
        <div id="content">
            <div id="price-row">
                <Price title="Website" amount=850 delay="0.5s" delay2="1s"></Price>
                <Price title="Mobile App" amount=3000 delay="1.5s" delay2="2s"></Price>
                <Price title="Support" amount=20 delay="2.5s" delay2="3s" perHour=true></Price>
            </div>
        </div>
    </div>
</template>
<script setup>

import Logo from '../components/logo.vue';
import Intro from '../components/intro.vue';
import Price from '../components/price.vue';

</script>

<style scoped>
#head {
    display: flex;
    justify-content: space-between;
}

#content {
    border-top-left-radius: 50%;
    border-top-right-radius: 50%;
    /* box-shadow: 0 4px 2px -2px rgb(1, 53, 1); */
    background-color: black;
    border-top: 1.5px solid rgb(1, 53, 1);
    min-height: 44vh;
}

#price-row {
    display: flex;
    justify-content: space-between;
    width: 67.5%;
    margin: 8vh auto;
}
</style>