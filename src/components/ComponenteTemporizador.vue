<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">

        <ComponenteCronometro :tempoEmSegundos="tempoEmSegundos"/>
        <button class="button" @click="iniciar" :disabled="cronometroAtivo">
        <span class="icon">
            <i class="fas fa-play"></i>
        </span>
        <span>play</span>
        </button>

        <button class="button" @click="finalizar" :disabled="!cronometroAtivo">
        <span class="icon">
            <i class="fas fa-pause"></i>
        </span>
        <span>stop</span>

        </button>

    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import ComponenteCronometro from './ComponenteCronometro.vue';

    export default defineComponent({
        name: 'ComponenteTemporizador',
        emits: ['tempoFinalizado'],
        data () {
            return {
                tempoEmSegundos: 0,
                cronometro: 0,
                cronometroAtivo: false
            }
        },
        components: {
            ComponenteCronometro
        },
        methods: {
            iniciar () {
                this.cronometroAtivo = true;
                this.cronometro = setInterval(() => {
                    this.tempoEmSegundos++;
                }, 1000);
            }, 
            finalizar () {
                this.cronometroAtivo = false;
                clearInterval(this.cronometro);
                this.$emit('tempoFinalizado', this.tempoEmSegundos);
                this.tempoEmSegundos = 0;
            }
        }
    });

</script>