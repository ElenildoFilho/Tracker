<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <slot> 
            
        </slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';


export default defineComponent ({
    name: 'ComponenteBox',
    data() {
        return {
            estilos: {
                backgroundColor: '#faf0ca',
                color: '#000000'
            }
        }
    },
    
})
</script>