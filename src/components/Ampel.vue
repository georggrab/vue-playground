<template>
  <div class="ampel">
    <ampel-element :active="redElementActive" color="#c0392b"></ampel-element>
    <ampel-element :active="yellowElementActive" color="#f1c40f"></ampel-element>
    <ampel-element :active="greenElementActive" color="#2ecc71"></ampel-element>
  </div>
</template>

<script>
import AmpelElement from './AmpelElement'
import Vue from 'vue'

let ampelState = {
  redElementActive: null,
  yellowElementActive: null,
  greenElementActive: null
}

export default {
  name: 'ampel',
  props: ['nextState'],
  mounted: function () {
    this.stateMachine(this.$props.nextState)
  },
  data: function () {
    return ampelState
  },
  methods: {
    stateMachine: function (nextState) {
      if (this.$props.nextState === 'AMPEL_RED') {
        Vue.set(ampelState, 'redElementActive', true)
        Vue.set(ampelState, 'yellowElementActive', false)
        Vue.set(ampelState, 'greenElementActive', false)
      } else if (this.$props.nextState === 'AMPEL_GREEN') {
        Vue.set(ampelState, 'redElementActive', false)
        Vue.set(ampelState, 'yellowElementActive', false)
        Vue.set(ampelState, 'greenElementActive', true)
      } else if (this.$props.nextState === 'AMPEL_TRANSITION_TO_GREEN') {
        Vue.set(ampelState, 'redElementActive', false)
        Vue.set(ampelState, 'yellowElementActive', true)
        Vue.set(ampelState, 'greenElementActive', false)
      } else if (this.$props.nextState === 'AMPEL_TRANSITION_TO_RED') {
        Vue.set(ampelState, 'redElementActive', false)
        Vue.set(ampelState, 'yellowElementActive', true)
        Vue.set(ampelState, 'greenElementActive', true)
      }
    }
  },
  watch: {
    nextState: function (newVal, oldVal) {
      this.stateMachine(newVal)
    }
  },
  components: {
    AmpelElement
  }
}
</script>

<style>
.ampel{
    width: 500px;
    height:800px;
    border: 1px solid black;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
}
</style>
