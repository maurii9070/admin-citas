<template>

     <h1>ADMINISTRADOR DE PACIENTES</h1>
     <div class="container">
          <Formulario
               @obtener-citas="obtenerCitas"
               class="formulario"
          />
          <Citas
               :citas="citas"
               :titulo="titulo"
               @eliminar-cita="actualizarCita"
               class="citas"
          />
     </div>
</template>

<script>

import Formulario from './components/Formulario.vue';
import Citas from './components/Citas.vue';

export default {
     name: 'App',
     components: {
          Formulario,
          Citas
     },
     data() {
          return {
               citas: []
          }
     },
     methods: {
          obtenerCitas(payload) {
               this.citas = [...this.citas, payload];
          },
          actualizarCita(payload) {
               this.citas = payload;
          }
     },
     computed: {
          titulo() {
               return this.citas.length > 0 ? 'ADMINISTRA TUS CITAS' : 'NO HAY CITAS'
          },

     }
}
</script>

<style>
* {
     padding: 0;
     margin: 0;
     box-sizing: border-box;
     font-family: sans-serif;
}
body {
     background: rgb(0, 109, 166);
     background: linear-gradient(
          90deg,
          rgba(0, 109, 166, 1) 0%,
          rgba(189, 0, 143, 1) 100%
     );
     color: #fff;
}

h1,
h2,
legend {
     text-align: center;
     font-size: 50px;
     font-family: "Staatliches", cursive;
}

.container {
     width: 70%;
     margin: 7rem auto;
     display: grid;
     grid-template-columns: 1fr 1fr;
}
</style>
