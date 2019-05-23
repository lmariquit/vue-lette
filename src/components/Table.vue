<template>
  <div>
    <Zeros v-on:bet-click="addBetOutside"/>
    <Numbers v-bind:allNumbers="allNumbers" v-on:bet-click="addBetInside"/>
    <Twelves v-on:bet-click="addBetOutside"/>
    <Double v-on:bet-click="addBetOutside"/>
    <TwoToOne v-on:bet-click="addBetOutside"/>
    <div @click="spin">SPIN</div>
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
    spin() {
      const spin = Math.floor(Math.random() * Math.floor(38))
      if (spin === 37) {
        this.result = '00'
      } else {
        this.result = spin
      }
      this.payout()
    },
    payout() {
      // eslint-disable-next-line
      console.log('SPIN SPIN SPIN, landed on ', this.result)
      if (!this.result || this.result === '00') {
        // 0 00 payout here
        // eslint-disable-next-line
        console.log('hit 0 or 00')
        return
      }
      const columnNum = Math.ceil(this.result / 3) - 1
      const rowNum = (this.result - 1) % 3
      const winningNumObj = this.allNumbers[columnNum][rowNum]
      // eslint-disable-next-line
      console.log('OBJ: ', winningNumObj)
      this.outsidePayout(winningNumObj)
      // Run Inside payout calc: outsidePayout(winningNumObj)
      // Run Outside payout calc: insidePayout(winningNumObj)
    },
    outsidePayout(obj) {
      //create clearing functions for all squares. Put them on an array. If obj meets criteria, remove from array. now run all functions in array
      this.checkRedBlack(obj)
      this.checkEvenOdd(obj)
      this.checkOneToEighteen(obj)
      this.checkTwelves(obj)
      this.checkTwoToOnes(obj)
      return obj
    },
    checkRedBlack(obj) {
      if (obj.color === 'red') {
        this.red *= 2
        this.black = 0
      } else {
        this.black *= 2
        this.red = 0
      }
      // eslint-disable-next-line
      console.log('red state: ', this.red)
      // eslint-disable-next-line
      console.log('black state: ', this.black)
    },
    checkOneToEighteen(obj) {
      if (obj.id < 19) {
        this.oneToEighteen *= 2
        this.nineteenToThirtysix = 0
      } else {
        this.nineteenToThirtysix *= 2
        this.oneToEighteen = 0
      }
      // eslint-disable-next-line
      console.log('oneToEighteen state: ', this.oneToEighteen)
      // eslint-disable-next-line
      console.log('nineteenToThirtysix state: ', this.nineteenToThirtysix)
    },
    checkEvenOdd(obj) {
      if (obj.id % 2) {
        this.odd *= 2
        this.even = 0
      } else {
        this.even *= 2
        this.odd = 0
      }
      // eslint-disable-next-line
      console.log('odd state: ', this.odd)
      // eslint-disable-next-line
      console.log('even state: ', this.even)
    },
    checkTwelves(obj) {
      if (obj.id < 13) {
        this.firstTwelve *= 3
        this.secondTwelve = 0
        this.thirdTwelve = 0
      } else if (obj.id < 25) {
        this.firstTwelve = 0
        this.secondTwelve *= 3
        this.thirdTwelve = 0
      } else {
        this.firstTwelve = 0
        this.secondTwelve = 0
        this.thirdTwelve *= 3
      }
      // eslint-disable-next-line
      console.log('firstTwelve state: ', this.firstTwelve)
      // eslint-disable-next-line
      console.log('secondTwelve state: ', this.secondTwelve)
      // eslint-disable-next-line
      console.log('thirdTwelve state: ', this.thirdTwelve)
    },
    checkTwoToOnes(obj) {
      // NOTE TO SELF --> REMEMBER TO DO FLEX DIRECTION COLUMN REVERSE THESE 2 TO 1 BOXES
      if ([1, 4, 7, 10, 13, 16, 19, 22, 25, 28, 31, 34].includes(obj.id)) {
        this.firstTwoToOne *= 3
        this.secondTwoToOne = 0
        this.thirdTwoToOne = 0
      } else if (
        [2, 5, 8, 11, 14, 17, 20, 23, 26, 29, 32, 35].includes(obj.id)
      ) {
        this.firstTwoToOne = 0
        this.secondTwoToOne *= 3
        this.thirdTwoToOne = 0
      } else {
        this.firstTwoToOne = 0
        this.secondTwoToOne = 0
        this.thirdTwoToOne *= 3
      }
      // eslint-disable-next-line
      console.log('firstTwoToOne state: ', this.firstTwoToOne)
      // eslint-disable-next-line
      console.log('secondTwoToOne state: ', this.secondTwoToOne)
      // eslint-disable-next-line
      console.log('thirdTwoToOne state: ', this.thirdTwoToOne)
    },
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
      result: '',
      bet: 10,
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
