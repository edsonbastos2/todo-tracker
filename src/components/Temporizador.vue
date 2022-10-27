<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempo="tempo" />
    <button class="button" @click="startTime" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalyTime" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";

export default defineComponent({
  name: "TemporizadorTime",
  components: {
    Cronometro,
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
    },
  },
});
</script>

<style scoped></style>
