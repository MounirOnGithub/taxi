<template>
    <div class="reservation">
        <input v-model="name" type="text">
        <input v-model="phone" type="text">
        <input v-model="departure" type="text">
        <input v-model="destination" type="text">
    </div>
</template>

<script>
export default {
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
