<template>
  <div>
    <div v-for="number in numbers" v-bind:key="number">{{number}}</div>
  </div>
</template>

<script>
export default {
  name: 'Column',
  props: ['numbers']
}
</script>

<style>
</style>
