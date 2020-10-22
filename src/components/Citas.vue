<template>
     <div>
          <h2 class="titulo">{{titulo}}</h2>
          <transition-group name="fade">
               <div
                    class="cita-container list-item"
                    v-for="cita in citas"
                    :key="cita.mascota"
               >

                    <p>Mascota: <span>{{cita.mascota}}</span> </p>
                    <p>Dueño: <span>{{cita.propietario}}</span> </p>
                    <p>Fecha: <span>{{cita.fecha}}</span> </p>
                    <p>Hora: <span>{{cita.hora}}</span> </p>
                    <p>Sintomas: <span>{{cita.sintomas}}</span> </p>

                    <button @click="eliminarCita(cita.mascota)">Eliminar &times;</button>

               </div>
          </transition-group>
     </div>
</template>

<script>
export default {
     name: 'Citas',
     props: {
          titulo: String,
          citas: Array
     },
     methods: {
          eliminarCita(mascota) {
               this.$emit('eliminar-cita', this.citas.filter(cita => cita.mascota !== mascota))
          }
     }
}
</script>

<style scoped>
.titulo {
     text-align: center;
     font-size: 40px;
     margin-bottom: 2rem;
}
.cita-container {
     background-color: #fff;
     color: #000;
     margin-top: 1rem;
     width: 90%;
     padding: 1em;
     border-radius: 8px;
}

.cita-container p {
     padding: 4px;
     font-weight: bold;
}

p span {
     font-weight: normal;
}

button {
     font-family: sans-serif;
     width: 100%;
     font-size: 13px;
     margin-top: 1rem;
     padding: 0.5em 0;
     border: none;
     background-color: #c10059;
     color: #fff;
     font-weight: bold;
     border-radius: 6px;
}

/* vue transition */
.fade-enter-active,
.fade-leave-active {
     transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
     opacity: 0;
}
</style>