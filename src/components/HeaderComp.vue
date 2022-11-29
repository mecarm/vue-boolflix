<template>
  <header class="d-flex justify-content-end">
    <div class="input-group my-3 w-auto me-3">
      <input type="text" class="form-control" v-model="inputUtente" placeholder="Cerca un film" aria-describedby="button-addon2">
      <button @click="$emit('emitSearch', inputUtente)" class="btn btn-danger" type="button" id="button-addon2">Button</button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data(){
    return{
      inputUtente: ''
    }
  }
}
</script>

<style scoped lang="scss">

</style>
