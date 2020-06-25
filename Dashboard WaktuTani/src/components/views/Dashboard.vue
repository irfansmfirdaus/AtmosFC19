<template>
  <!-- Main content -->
  <section class="content">
    <!-- GitHub hint -->
    <div class="row">
      <div class="col-xs-12">
        <alert :dismissible="true"
               type="success"
               :iconClasses="['fa', 'fa-check']"
               title="WAKTUTANI is open source! - (COMPETITION PERIOD)">
          <span>Click Icon for Waktutani github.</span>
          <a href="https://github.com/" target="_blank">
            <i class="fa fa-github fa-2x"></i>
          </a>
        </alert>
      </div>

      <!-- Info boxes -->
      <h4 style="font-weight: bold; margin-left: 14px;">WILAYAH KEKURANGAN BERAS</h4>
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-aqua"
                  :icon-classes="['warning']"
                  text="KABUPATEN SUKABUMI"
                  number="-11.200 TON"></info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-red"
                  :icon-classes="[]"
                  text="KABUPATEN PANGANDARAN"
                  number="-10.410 TON"></info-box>
      </div>
      <!-- /.col -->

      <!-- fix for small devices only -->
      <div class="clearfix visible-sm-block"></div>
      
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-green"
                  :icon-classes="[]"
                  text="KOTA SUBANG"
                  number="-9.800 TON"></info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-yellow"
                  :icon-classes="['1']"
                  text="KOTA TASIKMALAYA"
                  number="-7.233 TON"></info-box>
      </div>
      <!-- /.col -->
    </div>
    <!-- /.row -->

    <div class="col-xs-12">
      <div class="box">
        <div class="box-header with-border">
          <h3 class="box-title"></h3>
          <div class="box-body">
            <div class="col-sm-6 col-xs-12">
              <p class="text-center">
                <strong>Jumlah Kebutuhan VS Jumlah Produksi Provinsi jawa Barat</strong>
              </p>
              <canvas id="trafficBar" ></canvas>
            </div>
            <hr class="visible-xs-block">
            <div class="col-sm-6 col-xs-12">
              <p class="text-center">
                <strong>Jumlah Kebutuhan/Permintaan per Komoditas Bulan Juni 2020</strong>
              </p>
              <canvas id="languagePie"></canvas>
            </div>
          </div>
        </div>
        <div class="text-center">
          <small><b>Pro Tip</b> Don't forget to vote for WAKTUTANI!</small>
        </div>
      </div>
    </div>
    <!-- /.row -->

    <!-- Main row -->
    <div class="row">
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-yellow"
                          :icon-classes="['ion', 'ion-ios-pricetag-outline']"
                          text=""
                          number="Informasi Kalender Tanam di Kotamu"
                          :progress="50"
                          description="Rencanakan dengan hati - hati"></process-info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-green"
                          :icon-classes="['ion', 'ion-ios-heart-outline']"
                          text=""
                          number="Gabung Komunitas Rekan Seprofesi Disini"
                          :progress="20"
                          description="Hadapi kendala bersama"></process-info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-red"
                          :icon-classes="['ion', 'ion-ios-cloud-download-outline']"
                          text=""
                          number="Perhatikan Statistik Komoditas Per Kab/Kot Disini"
                          :progress="70"
                          description="Cek permintaan dan kebutuhan"></process-info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-aqua"
                          :icon-classes="['ion', 'ion-ios-chatbubble-outline']"
                          text=""
                          number="Konsultasi Seputar Pertanian Disini"
                          :progress="40"
                          description="Finding Solution on your problem"></process-info-box>
      </div>
      <!-- /.col -->
    </div>
    <!-- /.row -->
  </section>
  <!-- /.content -->
</template>

<script>
import Chart from 'chart.js'
import Alert from '../widgets/Alert'
import InfoBox from '../widgets/InfoBox'
import ProcessInfoBox from '../widgets/ProcessInfoBox'

export default {
  name: 'Dashboard',
  components: {
    Alert,
    InfoBox,
    ProcessInfoBox
  },
  data () {
    return {
      generateRandomNumbers (numbers, max, min) {
        var a = []
        for (var i = 0; i < numbers; i++) {
          a.push(Math.floor(Math.random() * (max - min + 1)) + max)
        }
        return a
      }
    }
  },
  computed: {
    coPilotNumbers () {
      return this.generateRandomNumbers(12, 1000000, 10000)
    },
    personalNumbers () {
      return this.generateRandomNumbers(12, 1000000, 10000)
    },
    isMobile () {
      return (window.innerWidth <= 800 && window.innerHeight <= 600)
    }
  },
  mounted () {
    this.$nextTick(() => {
      var ctx = document.getElementById('trafficBar').getContext('2d')
      var config = {
        type: 'line',
        data: {
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [{
            label: 'Jumlah Produksi',
            fill: false,
            borderColor: '#284184',
            pointBackgroundColor: '#284184',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: this.coPilotNumbers
          }, {
            label: 'Jumlah Kebutuhan',
            borderColor: '#4BC0C0',
            pointBackgroundColor: '#4BC0C0',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: this.personalNumbers
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          },
          tooltips: {
            mode: 'label',
            xPadding: 10,
            yPadding: 10,
            bodySpacing: 10
          }
        }
      }

      new Chart(ctx, config) // eslint-disable-line no-new

      var pieChartCanvas = document.getElementById('languagePie').getContext('2d')
      var pieConfig = {
        type: 'pie',
        data: {
          labels: ['Kabupaten Sukabumi', 'Kabupaten Pangandaran', 'Kota Subang'],
          datasets: [{
            data: [56.6, 37.7, 4.1],
            backgroundColor: ['#00a65a', '#f39c12', '#00c0ef'],
            hoverBackgroundColor: ['#00a65a', '#f39c12', '#00c0ef']
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          }
        }
      }

      new Chart(pieChartCanvas, pieConfig) // eslint-disable-line no-new
    })
  }
}
</script>
<style>
.info-box {
  cursor: pointer;
}
.info-box-content {
  text-align: center;
  vertical-align: middle;
  display: inherit;
}
.fullCanvas {
  width: 100%;
}
</style>
