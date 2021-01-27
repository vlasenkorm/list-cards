<template>
  <v-card color="gray" width="250px" height="350px">
    <v-card-text>
      <v-row justify="center" style="margin: 10px 0px;">{{ name }}</v-row>
    </v-card-text>
    <v-row justify="center">
      <ChartDoughnut
        :chart-data="chartData"
        :options="options"
        style="height: 150px"
      />
    </v-row>
  </v-card>
</template>

<script lang="ts">
import Vue from 'vue'
import ChartDoughnut from './chart/chartDoughnut.vue'

export default Vue.extend({
  name: 'CardTypeOne',
  components: {
    ChartDoughnut
  },
  props: ['name'],
  data: () => ({
    chartData: {
      labels: ['testData1', 'testData2', 'testData3'],
      datasets: [
        {
          backgroundColor: [
            'rgba(1, 116, 188, 0.50)',
            'rgba(1, 16, 18, 0.50)',
            'rgba(1, 216, 88, 0.50)'
          ],
          data: [1, 2, 3]
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      cutoutPercentage: 80,
      animation: {
        animateRotate: false
      },
      legend: {
        display: false
      },
      events: ['mousemove'],
      onHover: function (evt: object) {
        console.log('evt', evt)
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
