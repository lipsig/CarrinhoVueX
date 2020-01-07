<template>
    <Painel titulo="Loja Virtual" verde>
        <div class="loja">
            <span>Adicionar</span>
            <input type="number" v-model.number="quantidade">
            <span>Produto(s) de <strong>R$</strong></span>
            <input type="number" v-model.number="preco">
            <button id="agora" @click="adicionar">Agora!</button>
        </div>
    </Painel>
</template>

<script>

import {mapActions} from 'vuex'

export default {
    data() {
        return {
            sequencia: 1,
            quantidade: 1,
            preco: 9.99,
        }
    },
    methods: {
        ...mapActions(['adicionarProduto']),
        adicionar() {
            const produto = {
                id: this.sequencia,
                nome: `Produto ${this.sequencia}`,
                quantidade: this.quantidade,
                preco: this.preco
            }
            this.sequencia++
            //adicionando ao estado central
            //this.$store.state.produtos.push(produto)
            this.adicionarProduto(  produto)
           
        }
    }
}
</script>

<style>
    .loja {
        display: flex;
        justify-content: center;
    }

    #agora{
        cursor: pointer;
    }


    .loja > * {
        margin: 0px 10px;
    }

    input {
        font-size: 2rem;
        width: 90px;
    }
</style>
