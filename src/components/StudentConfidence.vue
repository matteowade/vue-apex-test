<template>
  <div>
    <h2>Change in confidence of students who participated in Junior Giants</h2>
    <apexchart v-if="series.length" type="bar" height="400" :options="chartOptions" :series="series"></apexchart>
  </div>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'
import ParentSurvey from '../parent-survey-data.json'

export default {
  name: 'StudentConfidence',
  components: {
    'apexchart': VueApexCharts
  },
  data: function() {
    return {
      parentSurvey: ParentSurvey,
      series: [],
      chartOptions: {
        plotOptions: {
          bar: {
            horizontal: false,
          }
        },
        xaxis: {
          categories: [
            'Significant negative change',
            'Negative change',
            'No change',
            'Positive change',
            'Significant positive change'
          ],
        },
        dataLabels: {
          enabled: true,
          offsetX: 0,
        },
        tooltip: {
          enabled: false
        },
        colors:['#7ddcb8'],
      }
    }
  },
  methods: {
    confidenceTotals: function() {
      let confidence = []
      let significantNegativeChangeTotal = 0;
      let negativeChangeTotal = 0;
      let noChange = 0;
      let positiveChange = 0;
      let significantPositiveChangeTotal = 0;

      for (let i = 0; i < this.parentSurvey.length; i++) {
        switch(this.parentSurvey[i]['Confidence']) {
          case 'Significant negative change':
            significantNegativeChangeTotal++
            break;
          case 'Negative change':
            negativeChangeTotal++
            break;
          case 'No change':
            noChange++
            break;
          case 'Positive change':
            positiveChange++
            break;
          case 'Significant positive change':
            significantPositiveChangeTotal++
            break;
        }
      }
      confidence.push(
        significantNegativeChangeTotal,
        negativeChangeTotal,
        noChange,positiveChange,
        significantPositiveChangeTotal
      )
      return confidence
    }
  },
  mounted: function() {
    this.series = [{data: this.confidenceTotals()}]
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../main.scss';
</style>
