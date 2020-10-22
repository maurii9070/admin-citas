<template>
     <form
          class="form"
          @submit.prevent="agregarCita"
     >

          <legend>CREAR CITA</legend>

          <transition name="fade">
               <p
                    v-if="error"
                    class="alert-error"
               >todos los campos son obligatorios.</p>
          </transition>

          <label>Nombre Mascota</label>
          <input
               type="text"
               placeholder="Nombre Mascota"
               v-model="nombreMascota"
          >

          <label>Nombre Dueño</label>
          <input
               type="text"
               placeholder="Nombre Dueño"
               v-model="nombreDuenio"
          >

          <label>Fecha</label>
          <input
               type="date"
               v-model="fecha"
          >

          <label>Hora</label>
          <input
               type="time"
               v-model="hora"
          >

          <label>Sintomas</label>
          <textarea
               name=""
               id=""
               rows="5"
               v-model="sintomas"
          ></textarea>

          <button type="submit">AGREGAR CITA</button>

     </form>
</template>

<script>
export default {
     name: 'Formulario',
     data() {
          return {
               nombreMascota: '',
               nombreDuenio: '',
               fecha: '',
               hora: '',
               sintomas: '',
               error: false
          }
     },
     methods: {
          agregarCita() {
               if (this.nombreMascota.trim() === '' || this.nombreDuenio.trim() === '' || this.fecha.trim() === '' || this.hora.trim() === '' || this.sintomas.trim() === '') {
                    this.error = true;
               } else {
                    this.error = false;
                    this.$emit('obtener-citas', {
                         mascota: this.nombreMascota,
                         propietario: this.nombreDuenio,
                         fecha: this.fecha,
                         hora: this.hora,
                         sintomas: this.sintomas
                    })
               }

          }
     }
}
</script>

<style scoped>
.form {
     display: flex;
     flex-direction: column;
     width: 90%;
}

legend {
     text-align: center;
     font-size: 40px;
     margin-bottom: 2rem;
}

label {
     margin-top: 1rem;
     font-weight: bold;
}

input {
     border-radius: 6px;
     border-width: 1px;
     padding: 10px 8px;
     outline: none;
     margin-top: 5px;
}

textarea {
     padding: 8px;
}

button {
     font-family: sans-serif;
     font-size: 14px;
     margin-top: 1rem;
     padding: 1em 0;
     border: none;
     background-color: #0bf;
     color: #fff;
     font-weight: bold;
     border-radius: 6px;
     outline: none;
}

button:hover {
     background-color: #1cf;
     transition: background-color 0.2s ease-in;
}

.alert-error {
     font-size: 20px;
     font-family: "Staatliches", cursive;
     text-align: center;
     background: rgba(255, 255, 255, 0.7);
     color: #f00;
     font-weight: bold;
     text-transform: uppercase;
     padding: 0.8em 0;
     border-radius: 4px;
}

/* vue transition */
.fade-enter-active,
.fade-leave-active {
     transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
     opacity: 0;
}
</style>