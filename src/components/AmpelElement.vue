<template>
  <div 
    :style="{'background-color': color}"
    :class="[active ? 'ampel-active' : 'ampel-inactive']"
    class="ampel-element">
  </div>
</template>

<script>
export default {
  name: 'ampel-element',
  props: ['color', 'active'],
  mounted: () => {
  },
  components: {
  }
}
</script>

<style>
.ampel-element{
    width:100%;
    transition: opacity .5s ease;
    flex: 1;
}

.ampel-active {
    opacity: 1;
}

.ampel-inactive {
    opacity: 0.2;
}

</style>
