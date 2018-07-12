<template>
    <div class="reservation">
        <reservation-form></reservation-form>
    </div>
</template>

<script>
import ReservationForm from '@/forms/ReservationForm'

export default {
  components: {
    'reservation-form': ReservationForm
  },
  name: 'Reservation'
}
</script>
