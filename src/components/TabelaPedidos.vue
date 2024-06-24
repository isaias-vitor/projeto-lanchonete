<template>
  <div class="p-5">
    <table class="table text-center">
        <thead>
            <tr>
                <th scope="col" class="text-center">#</th>
                <th scope="col" class="text-center">Cliente</th>
                <th scope="col" class="text-center">Pão</th>
                <th scope="col" class="text-center">Carne</th>
                <th scope="col" class="text-center">Opcionais</th>
                <th scope="col" class="text-center">Ações</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td scope="row">1</td>
                <td >Vitor</td>
                <td>Parmesão e orégano</td>
                <td>Maminha</td>
                <td>
                    <ul>
                        <li>Bacon</li>
                        <li>Cebola roxa</li>
                        <li>Cheddar</li>
                        <li>Tomate</li>
                    </ul>
                </td>
                <td>
                    <div class="d-flex justify-content-around">
                        <div class="col-5 d-inline-block">
                            <select class="form-select" name="" id="">
                                <option value="" select>Selecione</option>
                                <option value="concluido">Concluído</option>
                            </select>
                        </div>
                        <button class="btn cancela">CANCELAR</button>
                    </div>
                </td>
            </tr>
            
            
        </tbody>
        </table>
  </div>  
</template>

<script>
export default{
    name: 'TabelaPedidos',
}
</script>

<style scoped>
ul{
    padding: 0px;
}
td{
    vertical-align: middle;
}
.cancela{
    background-color: #222;
    color: #FCBA03;
}
.cancela:hover{
    background-color: #111;
    color: #FCBA03;
}

</style>