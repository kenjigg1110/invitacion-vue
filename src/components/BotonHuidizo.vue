<script setup>
import { ref } from 'vue'

const emit = defineEmits(['intento'])
const posicion = ref(null) // null = todavía en su lugar original

function escapar() {
  const ancho = 100
  const alto = 50
  posicion.value = {
    x: Math.random() * (window.innerWidth - ancho),
    y: Math.random() * (window.innerHeight - alto),
  }
  emit('intento')
}
</script>

<template>
  <button
    class="no"
    :class="{ huyendo: posicion }"
    :style="posicion ? { left: posicion.x + 'px', top: posicion.y + 'px' } : {}"
    @mouseenter="escapar"
    @touchstart.prevent="escapar"
    @click.prevent="escapar"
  >
    No
  </button>
</template>

<style scoped>
.no {
  background: #ddd;
  color: #333;
}
.huyendo {
  position: fixed;
  transition: left 0.25s, top 0.25s;
}
</style>