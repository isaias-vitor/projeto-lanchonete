<template>
    <div id="nav" class="d-flex justify-content-between p-2 align-items-center">
        <div id="logo" class="col-6">
            <router-link to="/"><img :src="logo" alt="" width="100%"></router-link>
        </div>
        <div id="menu" class="">
            <router-link to="/"><button class="btn">Home</button></router-link>
            <router-link to="/pedidos"><button class="btn">Pedidos</button></router-link>
        </div>
    </div>
</template>

<script>
export default{
    name: 'NavBar',
    props: ['logo']
}
</script>

<style scoped>

#nav{
    background-color: #222;
    border-bottom: 4px solid #111;
}
#logo img{
    width: 40px;
    height: 40px;;
}
#menu button{
    padding: 5px;
    color: #fff;
}

</style>