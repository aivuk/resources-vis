<script>

import { Bar, mixins } from 'vue-chartjs'
const { reactiveProp } = mixins

export default {
  extends: Bar,
  mixins: [reactiveProp],
  name: 'MyBar',
  props: ['options'],
  data () {
    return {
      datacollection: null
    }
  },
  mounted () {
    this.renderChart(this.chartData, {responsive: true, maintainAspectRatio: false})
  },
  watch: {
    chartData: function() {
      //this.renderChart(this.data, this.options);
      this.$data._chart.destroy()
      this.renderChart(this.chartData, {responsive: true, maintainAspectRatio: false})
    }
  }
}

</script>
