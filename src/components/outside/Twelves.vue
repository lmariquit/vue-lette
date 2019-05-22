<template>
  <div class="twelves-container">
    <div class="twelves-indiv">1st 12</div>
    <div class="twelves-indiv">2nd 12</div>
    <div class="twelves-indiv">3rd 12</div>
  </div>
</template>

<script>
export default {
  name: 'Twelves'
}
</script>

<style>
.twelves-container {
  display: flex;
  flex-direction: row;
}
.twelves-indiv {
  width: 300px;
  border: solid;
  border-width: 0.5px;
}
</style>
