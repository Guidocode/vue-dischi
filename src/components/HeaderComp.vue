<template>
  <header class="d-flex justify-content-between align-items-center px-3">

    <div class="logo">
      <i class="fa-brands fa-spotify"></i>
    </div>

    <div class="input-group w-auto">
      <select class="custom-select p-2" id="inputGroupSelect02">
        <option selected>Seleziona un genere</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
    </div>
    
  </header>
</template>

<script>
export default {
  name: 'HeaderComp'
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

header{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 60px;
  background-color: $primary-color;
  font-size: .9rem;

  .logo{
    font-size: 35px;
    color: #35BD59;
  }
}
</style>