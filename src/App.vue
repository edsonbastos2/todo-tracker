<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-2">
      <BarraLateral />
    </div>
    <div class="column is-10">
      <Formulario @salvarEmTarefas="salvaNaLista" />
      <div class="tarefa">
        <div v-if="isAcitve" class="notification is-danger">
          <button class="delete" @click="close"></button>
          A tarefa precisa de uma descrição!
        </div>
        <TarefaVue
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BarraLateral from "@/components/BarraLateral.vue";
import Formulario from "@/components/Formulario.vue";
import TarefaVue from "./components/Tarefa.vue";
import Tarefa from "./interface/Tarefa";
export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Formulario,
    TarefaVue,
  },
  data() {
    return {
      tarefas: [] as Tarefa[],
      isAcitve: false
    };
  },
  methods: {
    salvaNaLista(tarefa: Tarefa) {
      if(!tarefa.descricao) {
        this.isAcitve = true
        setTimeout(() => this.isAcitve = false, 5000)
        return
      }

      this.tarefas.push(tarefa);
    },

    close() {
      this.isAcitve = false
    }
  },
});
</script>

<style scoped>
.tarefa {
  padding: 1.25rem;
}
</style>
