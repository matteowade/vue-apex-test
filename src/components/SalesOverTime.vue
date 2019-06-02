<template>
  <div>
    <h2>Units sold by year</h2>
    <apexchart v-if="series.length" type="area" width="800" :options="chartOptions" :series="series"></apexchart>
  </div>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'
import SalesData from '../sales-data.json'

export default {
  name: 'SalesOverTime',
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
          categories: ['2010', '2011', '2012', '2013', '2014', '2015', '2016', '2017'],
        },
        dataLabels: {
          enabled: true,
          offsetX: 0,
        },
        tooltip: {
          enabled: false
        }
      }
    }
  },
  methods: {
    unitsSold: function() {
      let values = []
      let yearSales = {'10':0, '11':0, '12':0, '13':0, '14':0, '15':0, '16':0, '17':0}

      for (let i = 0; i < this.salesData.length; i++) {
        
        let year = this.salesData[i]['Order Date'].slice(-2);
        let units = this.salesData[i]['Units Sold']
        
        switch(year) {
          case '10':
            yearSales['10'] = yearSales['10'] + units
            break;
          case '11':
            yearSales['11'] = yearSales['11'] + units
            break;
          case '12':
            yearSales['12'] = yearSales['12'] + units
            break;
          case '13':
            yearSales['13'] = yearSales['13'] + units
            break;
          case '14':
            yearSales['14'] = yearSales['14'] + units
            break;
          case '15':
            yearSales['15'] = yearSales['15'] + units
            break;
          case '16':
            yearSales['16'] = yearSales['16'] + units
            break;
          case '17':
            yearSales['17'] = yearSales['17'] + units
            break;
        }
      }
      console.dir(yearSales)
      Object.entries(yearSales).forEach(([key, value]) => {
        values.push(value)
      })
      
      return values
    },
  },
  mounted: function() {
    this.series = [{data: this.unitsSold()}]
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
