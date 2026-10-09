# Invitación a una cita

Aplicación web hecha con **Vue 3** y **Vite** para la materia de Programación para internet. Es una invitación interactiva: la persona decide si quiere salir contigo, pero el botón "No" escapa del cursor cada vez que intenta alcanzarlo.

**Aplicación en producción:** https://invitacion-vue.vercel.app/

## Descripción y propósito

El propósito del proyecto es practicar los conceptos fundamentales de Vue.js en una aplicación sencilla pero completa, y desplegarla en un entorno de producción en la nube.

Flujo de la aplicación:

1. **Pregunta:** "¿Quieres salir conmigo?" con los botones "Sí" y "No". El botón "No" se mueve a una posición aleatoria cuando el cursor (o el dedo, en celular) intenta acercarse, y un contador muestra cuántos intentos se han hecho.
2. **Opciones:** si se elige "Sí", aparecen las opciones de cita (alitas de pollo, miche, chaska y café).
3. **Confirmación:** se muestra la opción elegida y el número de intentos de decir que no.

## Conceptos de Vue aplicados

- **Reactividad:** `ref()` para guardar la pantalla actual, la opción elegida, los intentos y la posición del botón; `computed()` para generar el mensaje del contador.
- **Componentes:** la interfaz se divide en componentes reutilizables y se une en `App.vue`.
- **Manejo de eventos:** `@click`, `@mouseenter` y `@touchstart` para las interacciones.
- **Estado:** el estado vive en `App.vue` y se comparte con los componentes hijos mediante `props` y `emit`.
- **Renderizado condicional y de listas:** `v-if` / `v-else-if` para cambiar de pantalla y `v-for` para mostrar las opciones.

## Tecnologías

- [Vue 3](https://vuejs.org/) (Composition API con `<script setup>`)
- [Vite](https://vite.dev/)
- [Vercel](https://vercel.com/) para el despliegue

## Estructura del proyecto

```
invitacion-vue/
├── public/
├── src/
│   ├── components/
│   │   ├── BotonHuidizo.vue         # Botón "No" que escapa del cursor
│   │   ├── OpcionesCita.vue         # Lista de opciones de cita
│   │   └── PantallaConfirmacion.vue # Mensaje final
│   ├── App.vue                      # Componente raíz y estado general
│   └── main.js                      # Punto de entrada
├── index.html
├── package.json
└── vite.config.js
```

## Ejecutar el proyecto localmente

Requisitos: tener instalado [Node.js](https://nodejs.org/) y Git.

1. Clonar el repositorio:

```bash
   git clone https://github.com/kenjigg1110/invitacion-vue.git
   cd invitacion-vue
```

2. Instalar las dependencias:

```bash
   npm install
```

3. Iniciar el servidor de desarrollo:

```bash
   npm run dev
```

4. Abrir en el navegador la dirección que aparece en la terminal (normalmente `http://localhost:5173`).

### Generar la versión de producción

```bash
npm run build
```

Los archivos finales se generan en la carpeta `dist/`.

## Despliegue

La aplicación está desplegada en **Vercel**, conectada a este repositorio de GitHub. Cada vez que se hace un push a la rama `main`, Vercel construye y publica la nueva versión automáticamente.

## Autor

Kenji ([@kenjigg1110](https://github.com/kenjigg1110))
