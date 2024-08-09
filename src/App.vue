<template>
  <div id="head">
    <Logo />
    <Intro />
  </div>
  <RouterView />
  <Footer></Footer>
</template>

<script setup>
import Logo from './components/logo.vue';
import Intro from './components/intro.vue';
import { RouterLink, RouterView } from 'vue-router'
import Footer from './components/footer.vue';
</script>

<style scoped>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

#head {
  height: 40vh;
  display: flex;
  justify-content: space-between;
}
</style>
