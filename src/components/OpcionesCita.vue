<script setup>
defineProps({
  opciones: { type: Array, required: true },
})
defineEmits(['elegir'])
</script>

<template>
  <section class="tarjeta">
    <h2>¡Qué bien! 🎉 ¿Qué se te antoja?</h2>
    <div class="lista">
      <button
        v-for="opcion in opciones"
        :key="opcion.id"
        class="opcion"
        @click="$emit('elegir', opcion)"
      >
        {{ opcion.emoji }} {{ opcion.nombre }}
      </button>
    </div>
  </section>
</template>

<style scoped>
.lista {
  display: grid;
  gap: 0.8rem;
  margin-top: 1.5rem;
}
.opcion {
  background: #fff0f5;
  border: 2px solid #e63970;
  color: #e63970;
}
.opcion:hover {
  background: #e63970;
  color: white;
}
</style>