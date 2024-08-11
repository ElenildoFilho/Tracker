<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': modoEscuro }">
    <div class="column is-one-quarter">
      <BarraLateral @alterarTema="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <UserFormulario @SalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <ComponenteTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <ComponenteBox v-if="listaEstaVazia">
          Star your first task by filling the form above.
        </ComponenteBox>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import UserFormulario from './components/UserFormulario.vue';
import ComponenteTarefa from './components/ComponenteTarefa.vue';
import ITarefa from './interfaces/ITarefa';
import ComponenteBox from './components/ComponenteBox.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    UserFormulario,
    ComponenteTarefa,
    ComponenteBox

  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuro: false
    }
  },
  computed: {
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    },
    trocarTema(modoEscuro: boolean) {
      this.modoEscuro = modoEscuro;
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;

}

.main {
  --bg-main: #ffffff;
  --text-main: #000000;
}

main.dark-mode {
  --bg-main: hsl(221, 14%, 9%);
  --text-main: #797979;
}

.conteudo {
  background-color: var(--bg-main);
  color: var(text-main);
}
</style>
