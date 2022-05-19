<template>
  
  <div class="col mb-4">
    <div class="gb-card text-center p-2">
      <div class="cover-image">
        <img class="w-100" :src="cover.poster" :alt="cover.title">
        <!-- Layover e animazione -->
        <div class="layover">
          <div class="play-hover d-flex justify-content-center align-items-center h-100">
            <i class="fa-regular fa-circle-play"></i>
          </div>
        </div>
        <!-- /Layover e animazione -->
      </div>
      <div class="title-song mt-3">{{cover.title}}</div>
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
  height: 100%;
  font-size: .8rem;
  transition: all .2s;
  border-radius: 5px;
  cursor: pointer;
  &:hover{
    transform: scale(1.05);
    background-color: lighten($primary-color, 70%);
  }
  &:hover .title-song{
    color: #1E2D3B; 
  }
  &:hover .cover-image .layover{
    display: block;
  }

  .cover-image{
    position: relative;

    .layover{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, .5);
      color: white;
      display: none;
    }

    .play-hover{
      font-size: 2.5rem;
      animation-name: play;
      animation-duration: 1.5s;
      animation-timing-function: ease-in-out;
      animation-iteration-count: infinite;

      @keyframes play{
        0%{transform: scale(1)}
        50%{transform: scale(1.2)}
      }
    }
  }

  .title-song{
    text-transform: uppercase;
    margin-bottom: 20px;
    font-weight: 600;
  }

  .author-song,
  .date-song{
    color: lighten($primary-color, 20%);
  }
  
}
</style>