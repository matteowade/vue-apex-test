<template>
  <div>
    <h2>Profit by Region</h2>
    <apexchart v-if="series.length" type="bar" height="480" :options="chartOptions" :series="series"></apexchart>
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
  name: 'RegionProfit',
  components: {
    'apexchart': VueApexCharts
  },
  data: function() {
    return {
      salesData: SalesData,
      series: [],
      chartOptions: {
        plotOptions: {
          bar: {
            horizontal: true,
          }
        },
        xaxis: {
          categories: [],
          labels: {
            formatter: function (val) {
              return moneyFormatter.format(val)
            }
          }
        },
        dataLabels: {
          enabled: true,
          formatter: function(val) {
            return moneyFormatter.format(val)
          },
          offsetX: 0,
        },
        tooltip: {
          enabled: false
        },
        colors:['#7ea0f8'],
      }
    }
  },
  methods: {
    region: function() {
      return Object.keys(this.salesData)
    },
    profitTotals: function() {
      let values = []

      Object.entries(this.salesData).forEach(([key, value]) => {
        let profitSum = 0
        for (let i = 0; i < value.length; i++) {
          profitSum += value[i]['total-profit']
        }
        values.push(Number(profitSum))
      })
      return values
    }
  },
  mounted: function() {
    this.series = [{data: this.profitTotals()}]
    this.chartOptions.xaxis.categories = this.region()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../main.scss';
</style>
