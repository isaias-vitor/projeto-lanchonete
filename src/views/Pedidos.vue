<template>
  <div class="pedidos">
    <h1 class="my-4">Gerenciamento de Pedidos</h1>
  </div>
  <TabelaPedidos/>
</template>

<script>
import TabelaPedidos from '@/components/TabelaPedidos.vue';

export default{
  name: 'Pedidos',
  components:{
    TabelaPedidos
  }
}
</script>