<template>
  <section class="appointment-manager">
    <div class="form">
      <div>
        <label :style="{ color: patient ? 'black' : 'red' }">Paciente</label>
        <input type="text" v-model="patient" />
      </div>
      <div>
        <label :style="{ color: date ? 'black' : 'red' }">Fecha</label>
        <input type="date" v-model="date" />
      </div>
      <div>
        <label :style="{ color: hour ? 'black' : 'red' }">Hora</label>
        <input type="time" v-model="hour" />
      </div>
      <div>
        <label :style="{ color: severity ? 'black' : 'red' }">Gravedad</label>
        <select v-model="severity">
          <option value="">Seleccione</option>
          <option value="green">Baja</option>
          <option value="yellow">Media</option>
          <option value="red">Alta</option>
        </select>
      </div>
      <div>
        <label :style="{ color: reason ? 'black' : 'red' }">Motivo</label>
        <input type="text" v-model="reason" />
      </div>
    </div>
    <button @click="send">Agregar</button>
  </section>
  <section class="appointments-list">
    <div v-for="(appointment, i) in appointments" :key="appointment">
      <Appointment
        :patient="appointment.patient"
        :date="appointment.date"
        :hour="appointment.hour"
        :severity="appointment.severity"
        :reason="appointment.reason"
        @delete="appointments.splice(i, 1)"
      />
    </div>
  </section>
</template>

<script>
import Appointment from "./components/Appointment.vue";

export default {
  components: {
    Appointment,
  },
  data() {
    return {
      patient: "",
      date: "",
      hour: "",
      severity: "",
      reason: "",
      appointments: [],
    };
  },
  methods: {
    send() {
      if (!this.patient || !this.date || !this.hour || !this.severity || !this.reason) {
        alert("Todos los campos son obligatorios");
        return;
      }
      const appointment = {
        patient: this.patient,
        date: this.date,
        hour: this.hour,
        severity: this.severity,
        reason: this.reason,
      };
      this.appointments.push(appointment);
    },
  },
};
</script>

<style scoped>
.appointment-manager {
  width: max-content;
  margin: 50px auto;
  padding: 20px;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.form {
  display: flex;
  justify-content: center;
  gap: 20px;
  padding-bottom: 20px;
}
label {
  display: block;
  font-weight: bold;
}
.appointments-list {
  width: 100%;
  display: flex;
  justify-content: center;
  gap: 20px;
}
</style>
