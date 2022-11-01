<template>
    <Box>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao}}
            </div>
            <div class="column">
                <Cronometro :tempo="tarefa.tempo"/>
            </div>
        </div>
    </Box>
</template>

<script lang="ts">
import Tarefa from '@/interface/Tarefa';
import { defineComponent, PropType } from 'vue'
import Cronometro from './Cronometro.vue';
import Box from './Box.vue'

export default defineComponent({
   name:'TarefaTime',
   props: {
    tarefa: {
        type: Object as PropType<Tarefa>,
        required: true
    }
   },
   components:{
    Cronometro,
    Box
   }
})
</script>

<style scoped>
</style>