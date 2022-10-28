<template>
    <header>
        <h1 class="logo">
            <img src="@/assets/iw.png" alt="">
            iwtraining
        </h1>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name:'BarraLateral',
    setup () {
        

        return {}
    }
})
</script>

<style scoped>
header {
  padding: 1rem;
  background: #4158A6;
  height: 100vh;
}
.logo {
    display: flex;
    align-items: center;
    color:#fff;
  }
@media only screen and (max-width: 768px) {
  header {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2.5rem;
    height: auto;
  }
}
</style>