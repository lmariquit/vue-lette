<template>
  <div>
    <Zeros v-on:bet-click="addBetOutside"/>
    <Numbers v-bind:allNumbers="allNumbers" v-on:bet-click="addBetInside"/>
    <Twelves v-on:bet-click="addBetOutside"/>
    <Double v-on:bet-click="addBetOutside"/>
    <TwoToOne v-on:bet-click="addBetOutside"/>
  </div>
</template>

<script>
import Zeros from './inside/Zeros.vue'
import Numbers from './inside/Numbers.vue'
import Twelves from './outside/Twelves.vue'
import Double from './outside/Double.vue'
import TwoToOne from './outside/TwoToOne.vue'

export default {
  name: 'Table',
  components: {
    Zeros,
    Numbers,
    Twelves,
    Double,
    TwoToOne
  },
  methods: {
    addBetInside(betNum) {
      const columnNum = Math.ceil(betNum / 3) - 1
      const rowNum = (betNum - 1) % 3
      // eslint-disable-next-line
      console.log(columnNum, rowNum, this.allNumbers[columnNum][rowNum])

      // eslint-disable-next-line
      console.log(
        'old ',
        betNum,
        this.allNumbers[columnNum][rowNum].id,
        this.allNumbers[columnNum][rowNum].bet
      )
      this.allNumbers[columnNum][rowNum].bet =
        this.allNumbers[columnNum][rowNum].bet + this.bet
      // eslint-disable-next-line
      console.log(
        'new ',
        betNum,
        this.allNumbers[columnNum][rowNum].id,
        this.allNumbers[columnNum][rowNum].bet
      )
    },
    addBetOutside(betTarget) {
      // eslint-disable-next-line
      console.log('old ', betTarget, this[betTarget])
      this[betTarget] = this[betTarget] + this.bet
      // eslint-disable-next-line
      console.log('new ', betTarget, this[betTarget])
    }
  },
  data() {
    return {
      bet: 20,
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
