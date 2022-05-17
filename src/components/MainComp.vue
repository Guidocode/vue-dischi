<template>
  <main>

    <div class="gb-container container-cards p-5">

      <CardComp />

    </div>

  </main>
</template>

<script>
import CardComp from './CardComp.vue';
export default {
    name: "MainComp",
    components: { CardComp }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

main{
  background-color: darken($primary-color, 5.5%);
  flex-grow: 1;
}
</style>