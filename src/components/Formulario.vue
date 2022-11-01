<template>
  <div class="box formulario">
    <div class="columns">
      <div
        class="column is-8"
        role="for"
        aria-label="Formulario para criação de uma nova tarefa"
      >
        <input
          class="input"
          type="text"
          placeholder="Qual tarefa você quer iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <Temporizador @aofinalizarTempo="finalizar"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from './Temporizador.vue'
export default defineComponent({
  name: "FormularioTempo",
  emits:['salvarEmTarefas'],
  components:{
    Temporizador
  },

  data() {
    return {
      descricao: '',
    }
  },

  methods: {
    finalizar($event:number) {
      this.$emit('salvarEmTarefas', {
        descricao: this.descricao,
        tempo: $event,
      })
      this.descricao = ''
    }
  }
  
});
</script>

<style>
.formulario {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
</style>
