<template>
  <div class="box formulario">
  <div class="columns">
    <div
      class="column is-8"
      role="form"
      aria-label="formulario para criar task"
    >
      <input 
      type="text" 
      class="input" 
      placeholder="Create a New Task"
      v-model="descricao"
       />
    </div>

    <div class="column">
      <ComponenteTemporizador @tempoFinalizado="finalizarTarefa"/>
    </div>
  </div>
</div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import ComponenteTemporizador from './ComponenteTemporizador.vue';

export default defineComponent({
  name: 'UserFormulario',
  emits: ['SalvarTarefa'],
  components: {
    ComponenteTemporizador
  },
  data () {
    return {
      descricao: ''
    }
  },
  methods: {
    finalizarTarefa (tempoEmSegundos: number) : void {
      this.$emit('SalvarTarefa', {
        duracao: tempoEmSegundos,
        descricao: this.descricao
      })
      this.descricao = ''
    }
  }
});

</script>

<style>
.formulario {
  color: var(--text-main);
  background-color: var(--bg-main);
}
</style>
