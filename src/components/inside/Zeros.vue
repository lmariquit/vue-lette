<template>
  <div class="zeros-container">
    <div id="zero" class="zeros-indiv" @click="$emit('bet-click', 'zero')">0</div>
    <div id="double-zero" class="zeros-indiv" @click="$emit('bet-click', 'doubleZero')">00</div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.zeros-container {
  /* display: grid; */
  /* grid-template-columns: repeat(12, 1fr); */
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  color: white;
  font-weight: 700;
}
.zeros-indiv {
  display: flex;
  width: 33.3%;
  height: 50%;
  border: solid;
  border-width: 0.5px;
  /* grid-column: 12/12; */
  background-color: green;
  justify-content: center;
  align-items: center;
}
</style>
