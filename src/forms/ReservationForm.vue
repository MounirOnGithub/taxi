<template>
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <date-picker v-model="date" :config="config"></date-picker>
        </div>
      </div>
    </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import datePicker from 'vue-bootstrap-datetimepicker'
import 'eonasdan-bootstrap-datetimepicker/build/css/bootstrap-datetimepicker.css'

export default {
  name: 'ReservationForm',
  components: {
    datePicker
  },
  data () {
    return {
      date: new Date(),
      config: {
        format: 'DD/MM/YYYY HH:mm',
        useCurrent: false
      }
    }
  }
}
</script>
