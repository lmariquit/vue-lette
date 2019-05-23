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
  /* display: grid; */
  /* grid-template-columns: repeat(12, 1fr); */
  display: flex;
  flex-direction: column-reverse;
  align-items: flex-start;
  color: white;
  font-weight: 700;
}
.twoToOne-indiv {
  display: flex;
  width: 33.3%;
  height: 50%;
  border: solid;
  border-width: 0.5px;
  background-color: green;
  justify-content: center;
  align-items: center;
}
</style>
