<template>

  <div class="input-group w-auto">
    <select @change="$emit('changeOption', optionSelected)" class="custom-select p-2" id="inputGroupSelect02">
      <option value="0" selected>Seleziona un genere</option>
      <option value="1">Rock</option>
      <option value="2">Pop</option>
      <option value="3">Jazz</option>
      <option value="4">Metal</option>
    </select>
  </div>

</template>

<script>
export default {
  name: 'SelectComp',

  data(){
    return{
      
    }
  },

  methods:{
    
  }
}
</script>

<style lang="scss" scoped>

</style>