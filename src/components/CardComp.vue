<template>
  
  <div class="col mb-4">
    <div class="gb-card text-center p-2">
      <img class="w-100 mb-3" :src="cover.poster" :alt="cover.title">
      <div class="title-song">{{cover.title}}</div>
      <div class="author-song">{{cover.author}}</div>
      <div class="date-song">{{cover.year}}</div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'CardComp',

  props:{
    cover: Object
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

.gb-card{
  background-color: $primary-color;
  min-height: 300px;
  font-size: .8rem;
  
  .title-song{
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .author-song,
  .date-song{
    color: lighten($primary-color, 20%);
  }
  
}
</style>