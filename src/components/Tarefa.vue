<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao}}
            </div>
            <div class="column">
                <Cronometro :tempo="tarefa.tempo"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Tarefa from '@/interface/Tarefa';
import { defineComponent, PropType } from 'vue'
import Cronometro from './Cronometro.vue';
export default defineComponent({
   name:'TarefaTime',
   props: {
    tarefa: {
        type: Object as PropType<Tarefa>,
        required: true
    }
   },
   components:{
    Cronometro
   }
})
</script>

<style scoped>
.box {
    background-color: #faf0ca;
}
</style>