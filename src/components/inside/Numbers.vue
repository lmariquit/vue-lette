<template>
  <div id="table">
    <div class="column" v-for="column in allNumbers">
      <div
        class="indiv-num"
        v-for="number in column"
        v-bind:class="number.color"
        v-bind:key="number.id"
        @click="$emit('bet-click', number.id)"
      >{{number.id}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Numbers',
  components: {},
  props: ['allNumbers']
}
</script>

<style>
#table {
  display: flex;
  flex-direction: row;
  color: white;
  font-weight: 700;
}

.column {
  display: flex;
  flex-direction: column-reverse;
}

.indiv-num {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
  border: solid;
  border-width: 0.5px;
}

.black {
  background-color: black;
}

.red {
  background-color: red;
}
</style>
