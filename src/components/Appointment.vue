<template>
  <div class="patient" :style="{ backgroundColor: severity }">
    <b>Paciente</b>
    <p>{{ patient }}</p>
    <b>Fecha</b>
    <p>{{ date }}</p>
    <b>Hora</b>
    <p>{{ hour }}</p>
    <b>Motivo</b>
    <p>{{ reason }}</p>
    <button @click="$emit('delete')">Eliminar</button>
  </div>
</template>

<script>
export default {
  props: ["patient", "date", "hour", "severity", "reason"],
};
</script>

<style scoped>
.patient {
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
  width: 150px;
  text-align: center;
}
p {
  text-wrap: wrap;
}
</style>
