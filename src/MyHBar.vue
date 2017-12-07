<script>

import { HorizontalBar, mixins } from 'vue-chartjs'
const { reactiveProp } = mixins

export default {
  extends: HorizontalBar,
  mixins: [reactiveProp],
  name: 'MyHBar',
  props: ['options'],
  data () {
    return {
      datacollection: null
    }
  },
  mounted () {
    this.renderChart(this.chartData, this.options)
  },
  watch: {
    chartData: function() {
      //this.renderChart(this.data, this.options);
      this.$data._chart.destroy()
      this.renderChart(this.chartData, this.options)
    }
  }
}

</script>
