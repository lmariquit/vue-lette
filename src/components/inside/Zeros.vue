<template>
  <div class="zeros-container">
    <div class="zeros-indiv" @click="$emit('bet-click', 'zero')">0</div>
    <div class="zeros-indiv" @click="$emit('bet-click', 'doubleZero')">00</div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.zeros-container {
  display: flex;
  flex-direction: column;
}
.zeros-indiv {
  width: 300px;
  border: solid;
  border-width: 0.5px;
}
</style>
