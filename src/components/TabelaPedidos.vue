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
                <tr v-for="burger in burgers" :key="burger.id">
                    <td scope="row"> {{ burger.id }}</td>
                    <td>{{ burger.nome }}</td>
                    <td> - </td>
                    <td>{{burger.carne}}</td>
                    <td>
                        <ul>
                            <li v-for="(opcionais, index) in burger.opcionais" :key="index">{{opcionais}}</li>
                        </ul>
                    </td>
                    <td>
                        <div class="d-flex justify-content-evenly">
                            <div class="d-inline-block">
                                <select class="form-select" name="" id="">
                                    <option value="" select>Selecione o status do hamburger</option>
                                    <option value="concluido">Concluído</option>
                                </select>
                            </div>
                            <button class="btn cancela">Cancelar</button>
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
    data(){
        return{
            burgers: null,
            burger_id: null,
            status_burger: null,
        }
    },
    methods: {
        async getBurgers(){
            const req = await fetch('http://localhost:3000/burgers');
            const data = await req.json();
            this.burgers = data;
        }
    },
    mounted(){
        this.getBurgers();
    }
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