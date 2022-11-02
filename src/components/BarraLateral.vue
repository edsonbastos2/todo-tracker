<template>
    <header>
        <h1 class="logo">
            <img src="@/assets/iw.png" alt="">
            iwtraining
        </h1>
        <div class="modo-dark">
          <button v-if="!isMobile" class="btn-modo-dark" @click="modoDark">
            {{isActive ? 'Desativar dark' : 'Ativar dark'}}
          </button>
          <button v-else class="btn-modo-dark" @click="modoDark">
          </button>
        </div>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name:'BarraLateral',
    emits:['modoDark'],
    data() {
      return {
        isActive: false
      }
    },
    computed:{
      isMobile() {
        return screen.width <= 600
      }
    },
    methods: {
      modoDark() {
        this.isActive = !this.isActive
        this.$emit('modoDark', this.isActive)
      }
    }
})
</script>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1rem;
  background: #4158A6;
  height: 100vh;
}
.logo {
    display: flex;
    align-items: center;
    color:#fff;
  }

.btn-modo-dark {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  background-color: #4158A6;
  padding: 5px;
  color: #fff;
  font-weight: 700;
  border: 1px solid #fff;
  border-radius: 8px;
  cursor: pointer;
  width: 110px;
}

@media(max-width: 600px) {
  .btn-modo-dark {
    width: fit-content;
    border: none;
  }
}
.btn-modo-dark::before {
  content: '';
  width: 24px;
  height: 24px;
  display: block;
  margin: 0 auto;
  background-image: url('../assets/noturno.svg');
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