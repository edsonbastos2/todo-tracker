<template>
  <section>
    <strong class="cronometro">{{ tempoDecorrido }}</strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CronometroTime",
  props: {
    tempo: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    tempoDecorrido(): string {
      return new Date(this.tempo * 1000).toISOString().substr(11, 8);
    },
  },
});
</script>

<style scoped>
.cronometro {
  color: #000;
}
</style>
