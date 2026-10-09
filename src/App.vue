<script setup>
import { ref, computed } from 'vue'
import BotonHuidizo from './components/BotonHuidizo.vue'
import OpcionesCita from './components/OpcionesCita.vue'
import PantallaConfirmacion from './components/PantallaConfirmacion.vue'

// Estado de la aplicación
const pantalla = ref('pregunta') // 'pregunta' | 'opciones' | 'confirmacion'
const opcionElegida = ref(null)
const intentos = ref(0)

const opciones = [
  { id: 1, nombre: 'Alitas de pollo', emoji: '🍗' },
  { id: 2, nombre: 'Miche', emoji: '🍺' },
  { id: 3, nombre: 'Chaska', emoji: '🥤' },
  { id: 4, nombre: 'Café', emoji: '☕' },
]

// Se recalcula solo cuando cambia "intentos"
const mensajeIntentos = computed(() =>
  intentos.value === 0
    ? ''
    : `Intentos de decir que no: ${intentos.value} 😏`
)

function elegirOpcion(opcion) {
  opcionElegida.value = opcion
  pantalla.value = 'confirmacion'
}
</script>

<template>
  <main class="contenedor">
    <section v-if="pantalla === 'pregunta'" class="tarjeta">
      <h1>¿Quieres salir conmigo? 💌</h1>
      <div class="botones">
        <button class="si" @click="pantalla = 'opciones'">Sí</button>
        <BotonHuidizo @intento="intentos++" />
      </div>
      <p class="contador">{{ mensajeIntentos }}</p>
    </section>

    <OpcionesCita
      v-else-if="pantalla === 'opciones'"
      :opciones="opciones"
      @elegir="elegirOpcion"
    />

    <PantallaConfirmacion
      v-else
      :opcion="opcionElegida"
      :intentos="intentos"
    />
  </main>
</template>

<style>
body {
  margin: 0;
  font-family: system-ui, sans-serif;
  background: linear-gradient(135deg, #ffd1dc, #ffb3c6);
}
.contenedor {
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 1rem;
}
.tarjeta {
  background: white;
  padding: 2rem 3rem;
  border-radius: 1.5rem;
  text-align: center;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}
.botones {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  align-items: center;
  margin-top: 1.5rem;
}
button {
  font-size: 1.1rem;
  padding: 0.7rem 1.8rem;
  border: none;
  border-radius: 0.8rem;
  cursor: pointer;
}
.si {
  background: #e63970;
  color: white;
}
.contador {
  margin-top: 1rem;
  color: #888;
  min-height: 1.5rem;
}
</style>
