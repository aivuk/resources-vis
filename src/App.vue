<template>
  <div id="app">
    AlleSchulen im Vergleich:
    <ul>
      <li :class="{active: selectedName == 'strom'}" @click="selectDataset('strom')">Strom</li>
      <li :class="{active: selectedName == 'heizung'}" @click="selectDataset('heizung')">Heizung</li>
      <li :class="{active: selectedName == 'wasser'}" @click="selectDataset('wasser')">Wasser</li>
    </ul>
    <p>
    </p>
    <MyBar :chartData="selectedDataset"></MyBar>
  </div>
</template>

<script>

import MyBar from './MyBar.vue'

export default {
  name: 'app',
  components: { MyBar },
  data () {
    return {
      datasets: {
        'strom': {
          labels: ['2013', '2014', '2015'],
          datasets: [
            {
              label: 'Grafschafter Gymnasium',
              backgroundColor: '#3980dc',
              data: [90.5, 83.1, 93.9]
            },
            {
              label: 'Gymnasium Adolfinum',
              backgroundColor: '#27e1b9',
              data: [328.8, 305.4, 301.6]
            },
            {
              label: 'Gymnasium Filder Benden',
              backgroundColor: '#fb9f08',
              data: [190.3, 168.2, 174.1]
            },
            {
              label: 'Gymnasium Rheinkamp',
              backgroundColor: '#ff5647',
              data: [180.4, 170.1, 207.8]
            }
          ]
        },
        'heizung': {
          labels: ['2013', '2014', '2015'],
          datasets: [
            {
              label: 'Grafschafter Gymnasium',
              backgroundColor: '#3980dc',
              data: [401.3, 308.7, 335.4]
            },
            {
              label: 'Gymnasium Adolfinum',
              backgroundColor: '#27e1b9',
              data: [1187.6, 738.5, 686.7]
            },
            {
              label: 'Gymnasium Filder Benden',
              backgroundColor: '#fb9f08',
              data: [1074, 765.1, 900]
            },
            {
              label: 'Gymnasium Rheinkamp',
              backgroundColor: '#ff5647',
              data: [425.1, 377.5, 392]
            }
          ]
        },
        'wasser': {
          labels: ['2013', '2014', '2015'],
          datasets: [
            {
              label: 'Grafschafter Gymnasium',
              backgroundColor: '#3980dc',
              data: [864.6, 1568.9, 1551.9]
            },
            {
              label: 'Gymnasium Adolfinum',
              backgroundColor: '#27e1b9',
              data: [3138, 2557.3, 4649.2]
            },
            {
              label: 'Gymnasium Filder Benden',
              backgroundColor: '#fb9f08',
              data: [1967.8, 1925, 1776.9]
            },
            {
              label: 'Gymnasium Rheinkamp',
              backgroundColor: '#ff5647',
              data: [1840.2, 2146.2, 2367.3]
            }
          ]
        }
      },
      selectedDataset: null,
      selectedName: ''
    }
  },
  mounted () {
    this.selectDataset('strom')
  },
  methods: {
    selectDataset(datasetName) {
      this.selectedName = datasetName
      this.$set(this, 'selectedDataset', this.datasets[datasetName])
      console.log(this.selectedDataset)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
  cursor: pointer;
  &.active {
    font-weight: bold;
  }
  &:hover {
    text-decoration: underline;
  }
}

a {
  color: #42b983;

}
</style>
