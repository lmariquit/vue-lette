<template>
  <div class="twoToOne-container">
    <div class="twoToOne-indiv" @click="$emit('bet-click', 'firstTwoToOne')">2 to 1</div>
    <div class="twoToOne-indiv" @click="$emit('bet-click', 'secondTwoToOne')">2 to 1</div>
    <div class="twoToOne-indiv" @click="$emit('bet-click', 'thirdTwoToOne')">2 to 1</div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.twoToOne-container {
  display: flex;
  flex-direction: column;
}
.twoToOne-indiv {
  width: 300px;
  border: solid;
  border-width: 0.5px;
}
</style>
