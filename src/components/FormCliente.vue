<template>
    <div id="form-burger" class="d-flex justify-content-center mt-5">
        <form class="col-4" @submit="fazPedido">    
            <Message :msg="mensagemSucesso" v-show="mensagemSucesso"/>
            <div class="mb-4">
                <label for="nome" class="form-label">Nome do cliente:</label>
                <input type="text" name="nome" class="form-control" placeholder="Digite o nome" v-model="nomeCliente">
            </div>
            <div class="mb-4">
                <label for="pao" class="form-label">Escolha o pão:</label>
                <select name="pao" v-model="paoBurger" class="form-select">
                    <option value="" selected>Selecione um tipo de pão</option>
                    <option v-for="pao in opcoesPao" :value="pao.tipo" :key="pao.id">{{ pao.tipo }}</option>
                </select>
            </div>
            <div class="mb-4">
                <label for="carne" class="form-label">Escolha a carne:</label>
                <select name="carne" v-model="carneBurger" class="form-select">
                    <option value="" selected>Selecione um tipo de pão</option>
                    <option v-for="carne in opcoesCarne" :value="carne.tipo" :key="carne.id">{{ carne.tipo }}</option>
                </select>
            </div>
            <div class="mb-4">
                <label for="opcionais" class="form-label d-block">Opcionais:</label>
                <div v-for="opcional in opcoesOpcionais" :key="opcional.id" class="form-check form-check-inline">
                    <input class="form-check-input" :name="opcional.tipo" :id="opcional.tipo" type="checkbox" :value="opcional.tipo" v-model="opcionaisBuger">
                    <label class="form-check-label" :for="opcional.tipo">{{opcional.tipo}}</label>
                </div>
            </div>

            <div class="d-flex justify-content-center mb-4">
                <button id="confirmaPedido" type="submit" @click="truco" class="btn ps-5 pe-5">Criar meu Burger!</button>
            </div>
            
        </form>
    </div>
</template>


<script>

import Message from './Message.vue'

export default{
    name: 'FormCliente',
    data(){
        return {
            nomeCliente: '',
            paoBurger: '',
            carneBurger: '',
            opcionaisBuger: [],
            opcoesPao: '',
            opcoesCarne: '',
            opcoesOpcionais: [],
            mensagemSucesso:''
        }
    }, 
    methods: {
        async getIgredientes(){
            const requisicao = await fetch('http://localhost:3000/ingredientes');
            const data = await requisicao.json();

            this.opcoesPao = data.paes;
            this.opcoesCarne = data.carnes;
            this.opcoesOpcionais = data.opcionais;
            
        },
        async fazPedido(e){
            e.preventDefault();

            const data = {
                nome: this.nomeCliente,
                pao: this.pao,
                carne: this.carneBurger,
                opcionais: Array.from(this.opcionaisBuger),
                status: 'Solicitado'
            }

            // Transformadno o json em texto
            const dataJson = JSON.stringify(data);

            // Enviando dados via API
            const req = await fetch('http://localhost:3000/burgers', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: dataJson
            });

            // Obtendo resposta do envio dos dados
            const res = await req.json();

            //Modificando estados da mensagem de sucesso
            this.mensagemSucesso = `Pedido Nº ${res.id} realizado com sucesso!`
            setTimeout(() => this.mensagemSucesso = '', 3000)
            
            //Limpando campos para nova inserção
            this.limpaCampos()

        },
        limpaCampos(){
            this.nomeCliente = '',
            this.paoBurger = '',
            this.carneBurger = '',
            this.opcionaisBuger = ''
        }

    },
    mounted(){
        this.getIgredientes();
    },
    components:{
        Message
    }
}
</script>

<style scoped>

#form-burger label{
    border-left: 5px solid #FCBA03;
    padding: 6px;
}
.form-check-label{
    border-left: none !important;
    padding: initial !important;
}
#confirmaPedido{
    background-color: #222;
    color: #FCBA03;
}
#confirmaPedido:hover{
    background-color: #111;
    color: #FCBA03;
}

</style>