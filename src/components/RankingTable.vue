/* eslint-disable */
<template>
  <div>
    {{ participants }}
    <b-button variant="primary">Botón de Bootstrap Vue</b-button>
  </div>
</template>

<script>
export default {
  name: 'RankingTable',
  props: {
    participants: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
