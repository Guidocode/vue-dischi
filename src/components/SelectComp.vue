<template>

  <div class="input-group w-auto">
    <select v-model="selected" @change="changeValue" class="custom-select p-2" id="inputGroupSelect02">
      <option value="All" selected>Seleziona un genere</option>
      
      <option
      v-for="(genre, index) in genres" :key="`genre-${index}`"
       :value="genre">{{genre}}</option>
      
    </select>

    <!-- 
      <option 
      v-for="(genre, index) in genres" :key="`genre-${index}`"
      :value="genre">{{genre}}</option> 
    -->
  </div>

</template>

<script>
export default {
  name: 'SelectComp',

  props:{
    genres: Array
  },

  data(){
    return{
      selected: 'All'
    }
  },

  methods:{
    changeValue(){
      this.$emit('cambioValore', this.selected)
      // console.log(this.selected);
    }
  }
}
</script>

<style lang="scss" scoped>

</style>