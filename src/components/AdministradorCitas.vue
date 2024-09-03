<script>
import FormCitaMedica from './FormCitaMedica.vue'
import CardPacientes from './CardPacientes.vue'

export default {
  name: 'AdministradorCitas',
  data() {
    return {
      pacientes: []
    }
  },
  components: { FormCitaMedica, CardPacientes },
  methods: {
    agregarPaciente(nuevoPaciente) {
      this.pacientes.push(nuevoPaciente)
    },
    eliminarCard(idx) {
      this.pacientes.splice(idx)
    }
  }
}
</script>
<template>
  <FormCitaMedica @submit-form="agregarPaciente" />
  <div v-show="pacientes.length == 0">
    <p :style="{ color: 'red', textAlign: 'center' }">No hay consultas registradas</p>
  </div>

  <div class="pacientes">
    <CardPacientes
      v-for="(paciente, idx) in pacientes"
      :key="idx"
      :paciente="paciente.paciente"
      :fecha="paciente.fecha"
      :hora="paciente.hora"
      :gravedad="paciente.gravedad"
      :motivo="paciente.motivo"
      @eliminar-card="eliminarCard(idx)"
    />
  </div>
</template>
<style scoped>
.pacientes {
  margin-top: 2.5rem;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
