<template>
  <div class="global-content">
    
    <!-- CONTENT TOP -->
    <div class="content-top d-flex justify-content-between align-items-center px-3">

      <div class="logo">
        <i class="fa-brands fa-spotify"></i>
      </div>


      <div class="select d-flex">

        <SelectComp @cambioGenere="selectedGenre" 
        :genres="arrayGenre"
        />

        <SelectAuthorsComp @cambioAutore="selectedAuthor" 
        :authors="arrayAuthors"
        />

      </div>
    
    </div>
    
    <!-- /CONTENT TOP -->



    <!-- CONTENT BOTTOM -->
    <!-- Logica errore -->
    <div v-if="!isError" class="h-100">
      <div v-if="!isLoading"
      class="gb-container container-cards p-5">

        <div class="container-fluid">
          <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5 d-flex">

            <CardComp 
            v-for="(coverItem, index) in getArrayCoversFiltered" :key="`coverItem-${index}`"
            :cover="coverItem"
            />

          </div>

        </div>
      </div>

      <!-- Caricamento fino a che isLoading diventa false -->
      <LoadingComp v-else />

    </div>
    
    <div v-else class="text-center my-5">{{errorMessage}}</div>
    <!-- /Logica errore -->
    <!-- CONTENT BOTTOM -->
    
  </div>
</template>

<script>
import axios from 'axios';
import SelectComp from './SelectComp.vue';
import CardComp from './CardComp.vue';
import LoadingComp from './LoadingComp.vue';
import SelectAuthorsComp from './SelectAuthorsComp.vue';
export default {
  name: "GlobalContentComp",

  components: {
    SelectComp,
    CardComp,
    LoadingComp,
    SelectAuthorsComp
},

  data(){
    return{
      baseUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
      arrayCovers: [],
      isLoading: true,
      errorMessage: '',
      isError: false,

      chosenGenre: '',
      chosenAuthor: '',

      arrayGenre: [],
      arrayAuthors: []

    }
  },

  methods:{
    getApi(){
      axios.get(this.baseUrl)
      .then(resp => {
        console.log('res', resp.data.response);
        this.arrayCovers = resp.data.response;
        this.isLoading = false;
        
        // Funzione array di generi
        this.getGenres();
        console.log(this.arrayGenre);

        // Funzione array di autori
        this.getAuthors();
        console.log(this.arrayAuthors);
      })
      .catch(error => {
        this.errorMessage = error;
        this.isError = true;
        console.log('ERRORE', this.errorMessage);
      })
    },

    selectedGenre(genereSelezionato){
      this.chosenGenre = genereSelezionato;
      console.log(genereSelezionato);
    },
    selectedAuthor(autoreSelezionato){
      this.chosenAuthor = autoreSelezionato;
      console.log(autoreSelezionato);
    },

    getGenres(){
      this.arrayCovers.forEach(coverItem =>{
        if(!this.arrayGenre.includes(coverItem.genre)) this.arrayGenre.push(coverItem.genre)
      })
    },
    getAuthors(){
      this.arrayCovers.forEach(coverItem =>{
        if(!this.arrayAuthors.includes(coverItem.author)) this.arrayAuthors.push(coverItem.author)
      })
    }

  },

  mounted(){
    this.getApi();

    console.log(this.genres);
  },

  computed:{
    getArrayCoversFiltered(){
      let arrayCoversFiltered = [];

      if(this.chosenGenre === 'All'){
        arrayCoversFiltered = this.arrayCovers;
      }else{
        arrayCoversFiltered = this.arrayCovers.filter(coverItem => {
          return coverItem.genre.toLowerCase().includes(this.chosenGenre.toLowerCase());
          
        })
      }

      if(this.chosenAuthor === 'All'){
        arrayCoversFiltered;
      }else{
        arrayCoversFiltered = arrayCoversFiltered.filter(coverItem => {
          return coverItem.author.toLowerCase().includes(this.chosenAuthor.toLowerCase());
          
        })
      }

      return arrayCoversFiltered;
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

.global-content{
  .content-top{
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

  background-color: #1E2D3B;
  flex-grow: 1;
  margin-top: 60px;
  overflow-y: scroll;
}
</style>