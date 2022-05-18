<template>

  <div class="input-group w-auto">
    <select v-model="selected" @change="changeValue" class="custom-select p-2" id="inputGroupSelect02">
      <option value="All" selected>Seleziona un genere</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </div>

</template>

<script>
export default {
  name: 'SelectComp',

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