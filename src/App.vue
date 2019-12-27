<template>
  <div id="app">
    <!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <p>{{message}}</p>
    <button v-on:click="show=!show">BUTTON</button>
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
        show: true
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
    mounted() {
      //  このインスタンスの作成 & 初期化が終わったらすぐ
      this.message += '最高!CREATED';
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
