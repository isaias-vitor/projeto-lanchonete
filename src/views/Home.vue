<template>
  <div class="home">
    <div id="banner" class="d-flex justify-content-start align-items-center">
      <h1 class="p-3 fw-bold">Make Your Burger</h1>
    </div>
    <h1>HOME</h1>
  </div>
</template>

<script>  

export default{
  name: 'Home',
}

</script>

<style>
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
