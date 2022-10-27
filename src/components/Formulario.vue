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
        <div class="is-flex is-align-items-center is-justify-content-space-between">
            <section>
                <strong>{{tempoDecorrido}}</strong>
            </section>
            <button class="button" @click="startTime">
                <span class="icon">
                    <i class="fas fa-play"></i>
                </span>
                <span>play</span>
            </button>
            <button class="button" @click="finalyTime">
                <span class="icon">
                    <i class="fas fa-stop"></i>
                </span>
                <span>stop</span>
            </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "FormularioTempo",
  data() {
    return {
        tempo:0
    }
  },
  computed: {
    tempoDecorrido():string {
        return new Date(this.tempo * 1000).toISOString().substr(11,8)
    }
  },
  methods:{
    startTime() {
        setInterval(() => {
            this.tempo += 1
        },1000)
    },
    finalyTime() {
        console.log('finalizou');
    }
  }
});
</script>

<style scoped></style>
