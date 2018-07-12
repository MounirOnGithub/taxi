<template>
    <div class="container">
      <div class="row">
        <p v-if="formErrors">
          The form is not valid, you should correct this errors for submitting :
          <ul v-if="formErrors.length">
            <li v-for="error in formErrors">
              {{ error }}
            </li>
          </ul>
        </p>
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

const emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
const phoneRegex = /^(?:(?:\+|00)33[\s.-]{0,3}(?:\(0\)[\s.-]{0,3})?|0)[1-9](?:(?:[\s.-]?\d{2}){4}|\d{2}(?:[\s.-]?\d{3}){2})$/

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
      },
      formErrors: []
    }
  },
  methods: {
    submitReservation: function () {
      isFormValid = this.validateForm()
      if (!isFormValid) {
        console.log('The form is not valid')
        return
      }
    },
    validateForm: function () {
      // Is name !empty & under 30 characters
      if (this.name === '' || this.name.length > 30) {
        this.formErrors.push('Name should be under 30 characters and not empty')
        return false
      }
      // Is phone field a phone number
      if (this.phone === '') {
        if (!phoneRegex.test(this.phone)) {
          this.formErrors.push('Phone number is not valid')
          return false
        }
      }
      // Is departure found in Google Maps API
      if (this.departure === '') {
        this.formErrors.push('Departure not found')
        return false
      }
      // Is destination found in Google Maps API
      if (this.destination === '') {
        this.formErrors.push('Destination not found')
        return false
      }
      // Is the date of reservation is in the past     
      let now = new Date();
      now.setHours(0,0,0,0);
      if (this.date < now) {
        this.formErrors.push('The reservation date should not be in the past')
        return false
      }
      return true
    }
  }
}
</script>
