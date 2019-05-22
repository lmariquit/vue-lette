<template>
  <div id="table">
    <div class="column" v-for="column in allNumbers">
      <div class="indiv-num" v-for="number in column" v-bind:key="number.id">{{number.id}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Inside',
  components: {},
  props: ['allNumbers']
}
</script>

<style>
#table {
  display: flex;
  flex-direction: row;
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
}
</style>
