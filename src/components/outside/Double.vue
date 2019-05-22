<template>
  <div class="double-container">
    <div class="double-indiv">1 to 18</div>
    <div class="double-indiv">EVEN</div>
    <div class="double-indiv">RED</div>
    <div class="double-indiv">BLACK</div>
    <div class="double-indiv">ODD</div>
    <div class="double-indiv">19 to 36</div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.double-container {
  display: flex;
  flex-direction: row;
}
.double-indiv {
  width: 300px;
  border: solid;
  border-width: 0.5px;
}
</style>
