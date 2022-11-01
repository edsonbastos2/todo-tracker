<template>
  <main class="columns is-gapless is-multiline" :class="{dark: dark}">
    <div class="column is-2">
      <BarraLateral @modoDark="modoDark" />
    </div>
    <div class="column is-10 conteudo">
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
        <Box v-if="!tarefas.length">
          Hoje você não esta produtivo :(
        </Box>
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
import Box from './components/Box.vue'

export default defineComponent({
  name: "App",
  components: {
    BarraLateral,
    Formulario,
    TarefaVue,
    Box
  },
  data() {
    return {
      tarefas: [] as Tarefa[],
      isAcitve: false,
      dark: false
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
    },
    modoDark($event: boolean) {
      this.dark = $event
      console.log($event)
    }
  },
});
</script>

<style>
.tarefa {
  padding: 1.25rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.dark {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
