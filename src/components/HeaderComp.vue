<template>
  <header>
    <div class="d-flex justify-content-between p-3 align-items-center">
      <h1 class="text-danger ps-3">NETFLIX</h1>
      <div class="input-group w-auto p-3">
        <input @keyup.enter="$emit('emitSearch', inputUtente)" type="text" class="form-control" placeholder="Titolo, film, serie" aria-label="Recipient's username"
          aria-describedby="button-addon2" v-model="inputUtente">
        <button @click="$emit('emitSearch', inputUtente)" class="btn btn-danger" type="button" id="button-addon2">Cerca</button>
      </div>
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
  header{
    height: 10%;
  }
</style>
