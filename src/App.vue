<template>
  <Imports/>
  <NavBar :logo="logo"/>
  <router-view/>
  <Footer/>
</template>


<script>
import Imports from './components/Imports.vue';
import Footer from './components/Footer.vue'
import NavBar from './components/NavBar.vue'


export default{
  components:{
    NavBar,
    Imports,
    Footer
  },
  data(){
    return{
      logo: 'img/logo.png'
    }
  }
}
</script>

<style>

*{
  text-decoration: none !important;
}

h1{
  text-align: center;
}

</style>
