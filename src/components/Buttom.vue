<template>
    <button class="button" @click="handleClick" :disabled="disabled">
      <span class="icon">
        <i :class="`fas fa-${icon}`"></i>
      </span>
      <span>{{text}}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name:'ButtomTime',
    emits:['click'],
    props: {
        disabled: {
            type: Boolean,
            default: false
        },
        icon: {
            type: String,
            required: true
        },
        text: {
            type: String,
            required: true
        }
    },
    methods:{
        handleClick() {
            this.$emit('click')
        }
    }
})
</script>

<style scoped>

</style>