<template>
  <div id="app">
    <ampel :nextState="state"></ampel>
    <controls v-on:stateChanged="processStateChange" />
  </div>
</template>

<script>
import Ampel from './components/Ampel'
import Controls from './components/Controls'

export default {
  name: 'app',
  data: function () {
    return {
      state: 'AMPEL_RED'
    }
  },
  methods: {
    processStateChange: function (newState) {
      this.$data.state = newState
    }
  },
  components: {
    Ampel, Controls
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
