<template>
    <div class="reservation">
        <input v-model="name" type="text">
        <input v-model="phone" type="text">
        <input v-model="departure" type="text">
        <input v-model="destination" type="text">
        <reservation-form></reservation-form>
    </div>
</template>

<script>
import ReservationForm from '@/forms/ReservationForm'

export default {
  components: {
    'reservation-form': ReservationForm
  },
  name: 'Reservation',
  data () {
    return {
      name: '',
      phone: '',
      departure: '',
      destination: '',
      reservationDate: null,
      creationDate: null
    }
  }
}
</script>
