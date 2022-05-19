<template>

  <div class="input-group w-auto mx-3">
    <select v-model="selected" @change="changeAuthor" class="custom-select p-2" id="inputGroupSelect02">
      <option value="All" selected>Seleziona un autore</option>
      
      <option
      v-for="(author, index) in authors" :key="`author-${index}`"
      :value="author">{{author}}</option>
      
    </select>
  </div>

</template>

<script>
export default {
  name: 'SelectAuthorsComp',

  props:{
    authors: Array
  },

  data(){
    return{
      selected: 'All'
    }
  },

  methods:{
    changeAuthor(){
      this.$emit('cambioAutore', this.selected)
      // console.log(this.selected);
    }
  }
}
</script>

<style lang="scss" scoped>

</style>