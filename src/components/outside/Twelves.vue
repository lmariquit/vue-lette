<template>
  <div class="twelves-container">
    <div class="twelves-indiv" @click="$emit('bet-click', 'firstTwelve')">1st 12</div>
    <div class="twelves-indiv" @click="$emit('bet-click', 'secondTwelve')">2nd 12</div>
    <div class="twelves-indiv" @click="$emit('bet-click', 'thirdTwelve')">3rd 12</div>
  </div>
</template>

<script>
export default {
  name: 'Twelves'
}
</script>

<style>
.twelves-container {
  grid-column: 2/2;
  display: flex;
  flex-direction: row;
  color: white;
  font-weight: 700;
}
.twelves-indiv {
  width: 33.3%;
  border: solid;
  border-width: 0.5px;
  background-color: green;
}
</style>
