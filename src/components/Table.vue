<template>
  <div>
    <div>RESULT: {{this.result}}</div>
    <div>bet: {{this.bet}}</div>
    <div class="grid-container">
      <Zeros v-on:bet-click="addBetOutside"/>
      <Numbers v-bind:allNumbers="allNumbers" v-on:bet-click="addBetInside"/>
      <TwoToOne v-on:bet-click="addBetOutside"/>
      <Twelves v-on:bet-click="addBetOutside"/>
      <Double v-on:bet-click="addBetOutside"/>
    </div>
    <div @click="spin">SPIN</div>
    <div>
      <div>1st 12: {{this.firstTwelve}}</div>
      <div>2st 12: {{this.secondTwelve}}</div>
      <div>3st 12: {{this.thirdTwelve}}</div>
      <div>1 to 18: {{this.oneToEighteen}}</div>
      <div>19 to 36: {{this.nineteenToThirtysix}}</div>
      <div>EVEN: {{this.even}}</div>
      <div>ODD: {{this.odd}}</div>
      <div>RED: {{this.red}}</div>
      <div>BLACK: {{this.black}}</div>
      <div>2 to 1 (first): {{this.firstTwoToOne}}</div>
      <div>2 to 1 (second): {{this.secondTwoToOne}}</div>
      <div>2 to 1 (third): {{this.thirdTwoToOne}}</div>
    </div>
    <div v-for="column in this.allNumbers">
      <div v-for="number in column" v-bind:key="number.id">{{number.id}} : {{number.bet}}</div>
    </div>
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
      if (!this.result) {
        const winnings = this.zero * 36
        this.clearAllInside()
        this.zero = winnings
        return
      } else if (this.result === '00') {
        const winnings = this.zero * 36
        this.clearAllInside()
        this.doubleZero = winnings
        return
      }
      const columnNum = Math.ceil(this.result / 3) - 1
      const rowNum = (this.result - 1) % 3
      const winningNumObj = this.allNumbers[columnNum][rowNum]
      this.insidePayout(winningNumObj)
      this.outsidePayout(winningNumObj)
    },
    insidePayout(obj) {
      const winnings = obj.bet * 36
      this.clearAllInside()
      obj.bet = winnings
    },
    clearAllInside() {
      for (let column of this.allNumbers) {
        for (let number of column) {
          number.bet = 0
        }
      }
    },
    clearAllOutside() {
      this.red = 0
      this.black = 0
      this.even = 0
      this.odd = 0
      this.oneToEighteen = 0
      this.nineteenToThirtysix = 0
      this.firstTwelve = 0
      this.secondTwelve = 0
      this.thirdTwelve = 0
      this.firstTwoToOne = 0
      this.secondTwoToOne = 0
      this.thirdTwoToOne = 0
      this.zero = 0
      this.doubleZero = 0
    },
    outsidePayout(obj) {
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
    },
    checkOneToEighteen(obj) {
      if (obj.id < 19) {
        this.oneToEighteen *= 2
        this.nineteenToThirtysix = 0
      } else {
        this.nineteenToThirtysix *= 2
        this.oneToEighteen = 0
      }
    },
    checkEvenOdd(obj) {
      if (obj.id % 2) {
        this.odd *= 2
        this.even = 0
      } else {
        this.even *= 2
        this.odd = 0
      }
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
    },
    addBetInside(betNum) {
      const columnNum = Math.ceil(betNum / 3) - 1
      const rowNum = (betNum - 1) % 3
      this.allNumbers[columnNum][rowNum].bet =
        this.allNumbers[columnNum][rowNum].bet + this.bet
    },
    addBetOutside(betTarget) {
      this[betTarget] = this[betTarget] + this.bet
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
.grid-container {
  display: grid;
  grid-template-columns: 1fr 3fr 1fr;
  grid-template-rows: 1fr;
}
</style>
