<template>
  <div class="box">
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
        />
      </div>
      <div class="column">
        <Temporizador/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Temporizador from './Temporizador.vue'
export default defineComponent({
  name: "FormularioTempo",
  components:{
    Temporizador
  }
  
});
</script>

<style scoped></style>
