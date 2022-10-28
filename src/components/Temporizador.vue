<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempo="tempo" />
    <ButtomVue @click="startTime" :disabled="cronometroRodando" icon="play" text="play"/>
    <ButtomVue @click="finalyTime" :disabled="!cronometroRodando" icon="stop" text="stop"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";
import ButtomVue from "./Buttom.vue";

export default defineComponent({
  name: "TemporizadorTime",
  emits:['aofinalizarTempo'],
  components: {
    Cronometro,
    ButtomVue
  },
  data() {
    return {
      tempo: 0,
      cronometro: 0,
      cronometroRodando: false
    };
  },
  methods: {
    startTime() {
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempo += 1;
      }, 1000);
    },
    finalyTime() {
      this.cronometroRodando = false
      clearInterval(this.cronometro);
      this.$emit('aofinalizarTempo', this.tempo)
      this.tempo = 0
    },
  },
});
</script>

<style scoped></style>
