<template>
  <div id="table">
    <div class="column" v-for="column in inside">
      <div class="indiv-num" v-for="number in column" v-bind:key="number.id">{{number.id}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Inside',
  components: {},
  data() {
    return {
      inside: [
        [
          {
            id: 1,
            color: red,
            bet: 0
          },
          {
            id: 2,
            color: black,
            bet: 0
          },
          {
            id: 3,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 4,
            color: black,
            bet: 0
          },
          {
            id: 5,
            color: red,
            bet: 0
          },
          {
            id: 6,
            color: black,
            bet: 0
          }
        ],
        [
          {
            id: 7,
            color: red,
            bet: 0
          },
          {
            id: 8,
            color: black,
            bet: 0
          },
          {
            id: 9,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 10,
            color: black,
            bet: 0
          },
          {
            id: 11,
            color: black,
            bet: 0
          },
          {
            id: 12,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 13,
            color: black,
            bet: 0
          },
          {
            id: 14,
            color: red,
            bet: 0
          },
          {
            id: 15,
            color: black,
            bet: 0
          }
        ],
        [
          {
            id: 16,
            color: red,
            bet: 0
          },
          {
            id: 17,
            color: black,
            bet: 0
          },
          {
            id: 18,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 19,
            color: red,
            bet: 0
          },
          {
            id: 20,
            color: black,
            bet: 0
          },
          {
            id: 21,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 22,
            color: black,
            bet: 0
          },
          {
            id: 23,
            color: red,
            bet: 0
          },
          {
            id: 24,
            color: black,
            bet: 0
          }
        ],
        [
          {
            id: 25,
            color: red,
            bet: 0
          },
          {
            id: 26,
            color: black,
            bet: 0
          },
          {
            id: 27,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 28,
            color: black,
            bet: 0
          },
          {
            id: 29,
            color: black,
            bet: 0
          },
          {
            id: 30,
            color: red,
            bet: 0
          }
        ],
        [
          {
            id: 31,
            color: black,
            bet: 0
          },
          {
            id: 32,
            color: red,
            bet: 0
          },
          {
            id: 33,
            color: black,
            bet: 0
          }
        ],
        [
          {
            id: 34,
            color: red,
            bet: 0
          },
          {
            id: 35,
            color: black,
            bet: 0
          },
          {
            id: 36,
            color: red,
            bet: 0
          }
        ]
      ]
    }
  }
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
