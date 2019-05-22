<template>
  <div>
    <Numbers v-bind:allNumbers="allNumbers"/>
    <Twelves/>
  </div>
</template>

<script>
import Numbers from './inside/Numbers.vue'
import Twelves from './outside/Twelves.vue'
export default {
  name: 'Table',
  components: {
    Numbers,
    Twelves
  },
  data() {
    return {
      red: 0,
      black: 0,
      even: 0,
      odd: 0,
      oneToEighteen: 0,
      nineteenToThirtysix: 0,
      firstTwelve: 0,
      secondTwelve: 0,
      thirdTwelve: 0,
      firstTwoToOne: 0,
      secondTwoToOne: 0,
      thirdTwoToOne: 0,
      zero: 0,
      doubleZero: 0,
      allNumbers: [
        [
          {
            id: 1,
            color: 'red',
            bet: 0
          },
          {
            id: 2,
            color: 'black',
            bet: 0
          },
          {
            id: 3,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 4,
            color: 'black',
            bet: 0
          },
          {
            id: 5,
            color: 'red',
            bet: 0
          },
          {
            id: 6,
            color: 'black',
            bet: 0
          }
        ],
        [
          {
            id: 7,
            color: 'red',
            bet: 0
          },
          {
            id: 8,
            color: 'black',
            bet: 0
          },
          {
            id: 9,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 10,
            color: 'black',
            bet: 0
          },
          {
            id: 11,
            color: 'black',
            bet: 0
          },
          {
            id: 12,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 13,
            color: 'black',
            bet: 0
          },
          {
            id: 14,
            color: 'red',
            bet: 0
          },
          {
            id: 15,
            color: 'black',
            bet: 0
          }
        ],
        [
          {
            id: 16,
            color: 'red',
            bet: 0
          },
          {
            id: 17,
            color: 'black',
            bet: 0
          },
          {
            id: 18,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 19,
            color: 'red',
            bet: 0
          },
          {
            id: 20,
            color: 'black',
            bet: 0
          },
          {
            id: 21,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 22,
            color: 'black',
            bet: 0
          },
          {
            id: 23,
            color: 'red',
            bet: 0
          },
          {
            id: 24,
            color: 'black',
            bet: 0
          }
        ],
        [
          {
            id: 25,
            color: 'red',
            bet: 0
          },
          {
            id: 26,
            color: 'black',
            bet: 0
          },
          {
            id: 27,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 28,
            color: 'black',
            bet: 0
          },
          {
            id: 29,
            color: 'black',
            bet: 0
          },
          {
            id: 30,
            color: 'red',
            bet: 0
          }
        ],
        [
          {
            id: 31,
            color: 'black',
            bet: 0
          },
          {
            id: 32,
            color: 'red',
            bet: 0
          },
          {
            id: 33,
            color: 'black',
            bet: 0
          }
        ],
        [
          {
            id: 34,
            color: 'red',
            bet: 0
          },
          {
            id: 35,
            color: 'black',
            bet: 0
          },
          {
            id: 36,
            color: 'red',
            bet: 0
          }
        ]
      ]
    }
  }
}
</script>

<style>
</style>
