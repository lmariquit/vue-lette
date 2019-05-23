<template>
  <div class="double-container">
    <div class="double-indiv" @click="$emit('bet-click', 'oneToEighteen')">1 to 18</div>
    <div class="double-indiv" @click="$emit('bet-click', 'even')">EVEN</div>
    <div class="double-indiv" @click="$emit('bet-click', 'red')">RED</div>
    <div class="double-indiv" @click="$emit('bet-click', 'black')">BLACK</div>
    <div class="double-indiv" @click="$emit('bet-click', 'odd')">ODD</div>
    <div class="double-indiv" @click="$emit('bet-click', 'nineteenToThirtysix')">19 to 36</div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.double-container {
  grid-row: 3/3;
  grid-column: 2/2;
  display: flex;
  flex-direction: row;
  color: white;
  font-weight: 700;
}
.double-indiv {
  width: 33.3%;
  border: solid;
  border-width: 0.5px;
  background-color: green;
}
</style>
