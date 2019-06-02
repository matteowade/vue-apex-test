<template>
  <div>
    <h2>Units Sold by Region</h2>
    <apexchart v-if="series.length" type="pie" width="800" :options="chartOptions" :series="series"></apexchart>
  </div>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'
import SalesData from '../sales-by-region-data.json'

const moneyFormatter = new Intl.NumberFormat('en-US', {
  style: 'currency',
  currency: 'USD',
  minimumFractionDigits: 1
})

export default {
  name: 'RegionUnitSales',
  components: {
    'apexchart': VueApexCharts
  },
  data: function() {
    return {
      salesData: SalesData,
      series: [],
      chartOptions: {
        labels: [],
        dataLabels: {
          enabled: false,
          offsetX: 0,
        },
        tooltip: {
          enabled: true
        }
      }
    }
  },
  methods: {
    region: function() {
      return Object.keys(this.salesData)
    },
    salesTotals: function() {
      let values = []

      Object.entries(this.salesData).forEach(([key, value]) => {
        let soldSum = 0
        for (let i = 0; i < value.length; i++) {
          soldSum += value[i]['units-sold']
        }
        values.push(Number(soldSum))
      })
      return values
    }
  },
  mounted: function() {
    this.series = this.salesTotals()
    this.chartOptions.labels = this.region()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
