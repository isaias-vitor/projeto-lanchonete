<template>
  <div class="home">

    <div id="banner" class="d-flex justify-content-start align-items-center mb-4">
      <h1 class="p-3 fw-bold">Make Your Burger</h1>
    </div>
     
    <h1>Monte o seu burger:</h1>

    <FormCliente/>
  </div>  
</template>

<script>

import FormCliente from '../components/FormCliente.vue'

export default{
  name: 'Home',
  components: {
    FormCliente
  }
}

</script>

<style scoped>
#banner{
  background-image: url('/public/img/burger.jpg');
  background-size: cover;
  background-position: 0 -250px;
  background-repeat: no-repeat;
  height: 500px;
}
#banner h1{
  color: #fff;
  background-color: #222;
}
</style>
