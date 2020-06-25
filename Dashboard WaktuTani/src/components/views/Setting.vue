<template>
  <div>
    <h1 class="text-center">Planting Calendar</h1>
    <section class="content">
      <div class="row">
        <div class="col-md-12">
          
          <div class="card-group">
            <div style="margin-left: 18%;" class="card">
              <img class="card-img-top" style="max-height: 800px;" src="../../assets/TGL1.jpg" alt="Card image cap">
              <div class="card-body">
              </div>
            </div>
          </div>

          <h1 class="text-center"  style="margin-top: 45px;">Planting Calendar</h1>
          <h4 class="text-center">Plan your farm carefully</h4>

          <div class="row">
            <div class="col-md-12">
              <!-- MAP & BOX PANE -->
              <div class="box box-success" style="display: flex; flex-wrap: wrap; justify-content: space-around; padding-top: 25px; padding-bottom: 25px;">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/bdg_kab.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Tasikmalaya.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/West Bandung.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Bekasi City.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Bogor.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Sumedang.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Karawang.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Majalengka.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Kuningan.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Cimahi City.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Cimahi City.jpg" alt="Card image cap">
                  <img class="card-img-top" style="max-height: 470px;" src="../../assets/Cirebon.jpg" alt="Card image cap">
              </div>
              <link rel="stylesheet" href="/static/js/plugins/jvectormap/jquery-jvectormap-2.0.3.css" >
            </div>
          </div>

        </div>
      </div>
    </section>
  </div>
</template>
<script>
require('moment')
import datepicker from 'vue-date-picker'

export default {
  name: 'Settings',
  components: { datepicker },
  computed: {
    datetime () {
      return new Date()
    }
  },
  methods: {
    clearInput (vueModel) {
      vueModel = ''
    }
  }
}
</script>

<style>
.datetime-picker input {
  height: 4em !important;
}
</style>
