<template>
  <div id="price-row">
    <Price title="Website" amount=850 delay="0.5s" delay2="1s"></Price>
    <Price title="Mobile App" amount=3000 delay="1.5s" delay2="2s"></Price>
    <Price title="Support" amount=20 delay="2.5s" delay2="3s" perHour=true></Price>
  </div>
</template>

<script setup>
import Price from '../components/price.vue';

</script>

<style scoped>
#price-row {
  width: 67.5%;
  margin: 0 auto;
}

@media (max-width: 1024px) {
  #price-row {
    width: 100%;
    flex-direction: column;
    align-items: center;
  }
}
</style>