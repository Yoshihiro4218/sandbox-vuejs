<template>
  <div id="app">
    <!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <p>{{message}}</p>
    <p>{{message2.morning}}</p>
    <p>{{message2.day.length}}</p>
    <p>{{bankList}}</p>
    <p>{{bankList[0]}}</p>
    <button v-on:click="countUp">Bank!</button>
    <p>{{bankList[num]}}</p>
    <button v-on:click="show=!show">BUTTON</button>
    <!--    <button v-on:click="computedMessage">BUTTON2</button>-->
    <transition>
      <p v-if="show">Pokemon!!</p>
    </transition>

  </div>
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'app',
    components: {
      HelloWorld
    },
    // アプリケーションで使用するデータ。オブジェクトや配列も可能。
    data() {
      return {
        message: 'Fukuoka!',
        show: true,
        // 内容が決まっていない場合でも初期値や空データとして定義しておく必要がある
        error: null,
        message2: {
          morning: 'おはよう！',
          day: 'こんにちは！'
        },
        bankList: ['福岡銀行', '親和銀行', '熊本銀行', '十八銀行'],
        num: 0
      }
    },
    // 算出プロパティ。dataと似たように扱うことの出来る、関数によって算出されたデータ
    computed: {
      computedMessage: function () {
        //  処理した結果をデータとして返す
        return this.message + '!!!!!(ﾆｯｺﾘ'
      }
    },
    //  ライフサイクルフック
    created() {
      //  このインスタンスの作成 & 初期化が終わったらすぐ
      this.message += ' + 最高! CREATED';
    },
    methods: {
      countUp() {
        if (this.num >= 3) {
          this.num = 0;
        } else {
          this.num++;
        }
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .v-enter-active, .v-leave-active {
    transition: opacity 1s;
  }

  .v-enter, v-leave-to {
    opacity: 0;
  }
</style>
