<template>
  <div class="column">
    <div v-for="number in numbers" v-bind:key="number.id">{{number.id}}</div>
  </div>
</template>

<script>
export default {
  name: 'Column',
  props: ['numbers']
}
</script>

<style>
.column {
  display: flex;
  flex-direction: column-reverse;
}
</style>
