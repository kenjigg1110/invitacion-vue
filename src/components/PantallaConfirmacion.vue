<script setup>
defineProps({
  opcion: { type: Object, required: true },
  intentos: { type: Number, default: 0 },
})
</script>

<template>
  <section class="tarjeta">
    <h2>¡Es una cita! 🥰</h2>
    <p>Elegiste: <strong>{{ opcion.emoji }} {{ opcion.nombre }}</strong></p>
    <p v-if="intentos > 0">
      (Intentaste decir que no {{ intentos }} veces, pero no pudiste 😄)
    </p>
  </section>
</template>