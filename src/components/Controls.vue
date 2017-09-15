<template>
  <div>
    <button v-on:click="emit('AMPEL_RED')">AMPEL_RED</button>
    <button v-on:click="emit('AMPEL_GREEN')">AMPEL_GREEN</button>
    <button v-on:click="emit('AMPEL_TRANSITION_TO_GREEN')">AMPEL_TRANSITION_TO_GREEN</button>
    <button v-on:click="emit('AMPEL_TRANSITION_TO_RED')">AMPEL_TRANSITION_TO_RED</button>
  </div>
</template>

<script>
export default {
  name: 'controls',
  mounted: () => {
  },
  methods: {
    emit: function (message) {
      this.$emit('stateChanged', message)
    }
  },
  components: {
  }
}
</script>

<style>

</style>
