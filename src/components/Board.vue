<template>
  <div>
    <div v-for="column in board">
      <Column v-bind:numbers="column"/>
    </div>
  </div>
</template>

<script>
import Column from './Column.vue'
export default {
  name: 'Board',
  components: {
    Column
  },
  data() {
    return {
      board: [[1, 2, 3], [4, 5, 6]]
    }
  }
}
</script>

<style>
</style>
