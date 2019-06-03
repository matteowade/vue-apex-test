<template>
  <div class="metric-row">
    <metricDisplay :metric="averageGPA" title="Average GPA" trend="up" color="#7ddcb8"></metricDisplay>
    <metricDisplay :metric="averageSAT" title="Average SAT Score" trend="up" color="#6aeafc"></metricDisplay>
    <metricDisplay :metric="averageAttendance" title="Average Attendance" trend="down" color="#ee6662"></metricDisplay>
  </div>
</template>

<script>
import StudentData from '../student-data.json'
import MetricDisplay from './MetricDisplay.vue'

export default {
  name: 'StudentMetrics',
  components: {
    metricDisplay: MetricDisplay
  },
  data: function() {
    return {
      studentData: StudentData
    }
  },
  computed: {
    averageGPA: function() {
      let gpas = 0
      for (let i = 0; i < this.studentData.length; i++) {
        gpas = gpas + this.studentData[i]['GPA']
      }
      return (gpas/this.studentData.length).toFixed(2)
    },
    averageSAT: function () {
      let sats = 0
      for (let i = 0; i < this.studentData.length; i++) {
        sats = sats + this.studentData[i]['TOTAL']
      }
      return Math.round(sats/this.studentData.length)
    },
    averageAttendance: function () {
      let attendance = 0
      for (let i = 0; i < this.studentData.length; i++) {
        attendance = attendance + parseFloat(this.studentData[i]['Attendance Pct'].slice(0, -1));
      }
      return `${Math.round(attendance/this.studentData.length)}%`
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import '../main.scss';
  
  .metric-row {
    display: flex;
    flex-direction: row;
    margin-bottom: 15px;
  }
</style>
