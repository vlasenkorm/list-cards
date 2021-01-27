<template>
  <v-card color="gray" width="250px" height="350px">
    <v-card-text>
      <v-row justify="center" style="margin: 10px 0px;">{{ name }}</v-row>
    </v-card-text>
    <v-row justify="center">
      <v-col
        cols="10"
      >
        <ChartLine
        :chart-data="chartData"
        :options="options"
        style="height: 150px"
      />
      </v-col>
    </v-row>
  </v-card>
</template>

<script lang="ts">
import Vue from 'vue'
import ChartLine from './chart/chartLine.vue'

export default Vue.extend({
  name: 'CardTypeTwo',
  components: {
    ChartLine
  },
  props: ['name'],
  data: () => ({
    chartData: {
      labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
      datasets: [
        {
          label: 'Data',
          backgroundColor: ['rgba(1, 116, 188, 0)'],
          lineTension: 0,
          data: [40, 39, 10, 40, 39, 80, 40]
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      animation: {
        animateRotate: false
      },
      legend: {
        display: false
      },
      scales: {
        xAxes: [{
          gridLines: {
            display: false
          },
          ticks: {
            display: false
          }
        }],
        yAxes: [{
          gridLines: {
            display: false
          },
          ticks: {
            display: false
          }
        }]
      }
    }
  })
})
</script>

<style lang="scss" scoped>
.flex {
  flex-grow: 0;
}

.flex-empty {
  height: 0 !important;
  padding-top: 0 !important;
  padding-bottom: 0 !important;

  div {
    width: 150px;
  }
}
</style>
