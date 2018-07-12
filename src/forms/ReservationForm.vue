<template>
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <input v-model="name" type="text" placeholder="Name">
          <input v-model="phone" type="text" placeholder="Phone">
          <input v-model="departure" type="text" placeholder="Departure">
          <input v-model="destination" type="text" placeholder="Destination">
          <date-picker v-model="date" :config="config"></date-picker>

          <button v-on:click="submitReservation" class="btn">Reserve</button>
        </div>
      </div>
    </div>
</template>

<script>
import datePicker from 'vue-bootstrap-datetimepicker'
import 'eonasdan-bootstrap-datetimepicker/build/css/bootstrap-datetimepicker.css'

export default {
  name: 'ReservationForm',
  components: {
    datePicker
  },
  data () {
    return {
      name: '',
      phone: '',
      departure: '',
      destination: '',
      reservationDate: null,
      creationDate: null,
      date: new Date(),
      config: {
        format: 'DD/MM/YYYY HH:mm',
        useCurrent: false
      }
    }
  },
  methods: {
    submitReservation: function () {
      this.validateForm()
    },
    validateForm: function () {}
  }
}
</script>
