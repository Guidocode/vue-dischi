<template>
  <main>

    <div v-if="!isLoading"
    class="gb-container container-cards p-5">

      <div class="container-fluid">
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5 d-flex">

          <CardComp 
          v-for="(coverItem, index) in arrayCovers" :key="`coverItem-${index}`"
          :cover="coverItem"
          />

        </div>

      </div>
    </div>

    <LoadingComp v-else />

  </main>
</template>

<script>
import axios from 'axios';
import CardComp from './CardComp.vue';
import LoadingComp from './LoadingComp.vue';
export default {
  name: "MainComp",

  components: {
    CardComp,
    LoadingComp
},

  data(){
    return{
      baseUrl: 'https://flynn.boolean.careers/exercises/api/array/music',

      arrayCovers: [],
      isLoading: true
    }
  },

  methods:{
    getApi(){
      axios.get(this.baseUrl)
      .then(resp => {
        console.log('res', resp.data.response);
        this.arrayCovers = resp.data.response;
        this.isLoading = false;
      })
    }
  },

  mounted(){
    this.getApi();
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

main{
  background-color: #1E2D3B;
  flex-grow: 1;
  margin-top: 60px;
  overflow-y: scroll;
}
</style>