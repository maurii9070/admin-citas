<template>
     <p>Mascota: <span>{{cita.mascota}}</span> </p>
     <p>Dueño: <span>{{cita.propietario}}</span> </p>
     <p>Fecha: <span>{{cita.fecha}}</span> </p>
     <p>Hora: <span>{{cita.hora}}</span> </p>
     <p>Sintomas: <span>{{cita.sintomas}}</span> </p>

     <button @click="eliminarCita(cita.mascota)">Eliminar &times;</button>
</template>

<script>
export default {
     name: 'ListCitas',
     props: {
          cita: Object
     },
     methods: {
          eliminarCita(mascota) {
               this.$emit('eliminar-cita', this.citas.filter(cita => cita.mascota !== mascota))
          }
     }
}
</script>

<style>
</style>