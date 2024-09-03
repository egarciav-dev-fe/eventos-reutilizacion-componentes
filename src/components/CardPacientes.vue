<script>
export default {
  name: 'CardPacientes',
  props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo', 'idx'],
  methods: {
    eliminarCard() {
      this.$emit('eliminar-card', this.idx)
    }
  }
}
</script>
<template>
  <div class="container">
    <div
      class="card"
      :class="gravedad === 'alta' ? 'red' : gravedad === 'media' ? 'yellow' : 'green'"
    >
      <b>Paciente</b>
      <p>{{ paciente }}</p>
      <b>Fecha</b>
      <p>{{ fecha }}</p>
      <b>Hora</b>
      <p>{{ hora }}</p>
      <b>Motivo</b>
      <p>{{ motivo }}</p>
      <button @click="eliminarCard">Eliminar</button>
    </div>
  </div>
</template>
<style scoped>
.card {
  min-width: 10rem;
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
}

.yellow {
  background-color: rgb(247, 247, 129);
}
.green {
  background-color: rgb(140, 226, 140);
}
.red {
  background-color: rgb(238, 125, 125);
  color: #ffffff;
}
</style>
