<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>

        <button class="button" @click="alterarTema">{{textoBotao}}</button>
    </header>
</template>

<script lang="ts">

    import { defineComponent } from 'vue'

    export default defineComponent({
        name: 'BarraLateral',
        emits: ['alterarTema'],
        data() {
            return {
                modoEscuro: false
            }
        },
        computed: {
            textoBotao() {
                if (this.modoEscuro) {
                    return 'Light Mode';
                } 
                return 'Dark Mode';
            }
        },
        methods: {
            alterarTema() {
                this.modoEscuro = !this.modoEscuro;
                this.$emit('alterarTema', this.modoEscuro);
            }
        }
    });

</script>

<style scoped>

    header {
        padding: 1rem;
        background: #0d3b66;
        width: 100%;
        height: 100vh;
        text-align: center;
    }

    @media only screed and (max-width: 768px) {
        header {
            padding: 2.5rem;
            height: auto;

        }
    }

</style>

