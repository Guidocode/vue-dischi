<template>
  <div class="wrapper d-flex flex-column">

    <GlobalContentComp />

  </div>
</template>

<script>
import GlobalContentComp from './components/GlobalContentComp.vue';

export default {
  name: 'App',
  components: {
    GlobalContentComp
  }
}
</script>

<style lang="scss">
@import './assets/style/general';
@import './assets/style/vars';
</style>
