<script>
export default {
  name: 'FormCitaMedica',
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      valueGravedad: '',
      gravedad: [
        { name: 'Baja', value: 'baja' },
        { name: 'Media', value: 'media' },
        { name: 'Alta', value: 'alta' }
      ],
      motivo: ''
    }
  },
  methods: {
    addPaciente() {
      this.$emit('submit-form', {
        paciente: this.paciente,
        hora: this.hora,
        fecha: this.fecha,
        gravedad: this.valueGravedad,
        motivo: this.motivo
      })
      /**Limpieza de valor inicial */
      this.paciente = ''
      this.hora = ''
      this.fecha = ''
      this.valueGravedad = ''
      this.motivo = ''
    },
    isFormValid() {
      return this.paciente && this.fecha && this.hora && this.gravedad && this.motivo
    }
  },
  emits: ['submit-form']
}
</script>
<template>
  <div class="container">
    <form class="form" @submit.prevent="addPaciente">
      <div class="boxForm">
        <div class="form-group">
          <label for="paciente" :style="{ color: paciente === '' ? 'red' : 'black' }"
            >Paciente</label
          >
          <input type="text" id="paciente" v-model="paciente" />
        </div>
        <div class="form-group">
          <label for="fecha" :style="{ color: fecha === '' ? 'red' : 'black' }">Fecha</label>
          <input type="date" id="fecha" v-model="fecha" />
        </div>
        <div class="form-group">
          <label for="hora" :style="{ color: hora === '' ? 'red' : 'black' }">Hora</label>
          <input type="time" id="hora" v-model="hora" />
        </div>
        <div class="form-group">
          <label for="gravedad" :style="{ color: gravedad === '' ? 'red' : 'black' }"
            >Gravedad</label
          >
          <select name="gravedad" id="gravedad" v-model="valueGravedad">
            <option v-for="(nivel, idx) in gravedad" :value="nivel.value" :key="idx">
              {{ nivel.name }}
            </option>
          </select>
        </div>
        <div class="form-group">
          <label for="motivo" :style="{ color: motivo === '' ? 'red' : 'black' }">Motivo</label>
          <input type="text" id="motivo" v-model="motivo" />
        </div>
      </div>
      <div class="button">
        <button type="submit" :disabled="!isFormValid()">Agregar</button>
      </div>
    </form>
  </div>
</template>
<style scoped>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 3rem;
  border: 1px solid #ccc;
  border-radius: 15px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

button {
  margin-top: 1.5rem;
}
.boxForm {
  display: flex;
  justify-content: space-around;
  gap: 1rem;
}
.form-group {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
