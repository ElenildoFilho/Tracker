<template>
    <ComponenteBox>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'No description'}}
            </div>
            <div class="column">
                <strong class="display">
                <ComponenteCronometro :tempoEmSegundos="tarefa.duracao"/>
                </strong>
            </div>

        </div>
    </ComponenteBox>
</template>

<script lang="ts">

import { defineComponent, PropType } from 'vue';
import ComponenteCronometro from './ComponenteCronometro.vue';
import ITarefa from '../interfaces/ITarefa';
import ComponenteBox from './ComponenteBox.vue';

export default defineComponent({
    name: 'ComponenteTarefa',
    components: {
        ComponenteCronometro,
        ComponenteBox
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});


</script>

<style scoped>
    .display {
        color: #000000 !important
    }
</style>
