<template>
  <div id="app">
    <!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <p ref="firstMessage">{{message}}</p>
    <p>{{message2.morning}}</p>
    <p>{{message2.day.length}}</p>
    <p>{{bankList}}</p>
    <p>{{bankList[0]}}</p>
    <button @click="countUp">Bank!</button>
    <p>{{bankList[num]}}</p>
    <button v-on:click="show=!show">BUTTON</button>
    <!--    <button v-on:click="computedMessage">BUTTON2</button>-->
    <transition>
      <p v-if="show">Pokemon!!</p>
    </transition>

    <p>{{message.length >= 10 ? '10文字以上' : "10文字未満"}}</p>
    <p>{{Math.random()}}</p>

    <input type="text" :value="message">

    <pre>{{$data}}</pre>

    <p :class="{child: isChild, 'is-active': isActive }"></p>
    <p v-bind:class="[isActive ? 'active' : 'normal', 'other']"></p>
    <p v-bind:class="classObject"></p>
    <img v-bind="attributes">

    <svg xml:base="http://www.w3.org/2003/03/wsdl" version="1.1">
      <circle v-bind:r="radius" cx="100" cy="75" fill="lightpink"/>
    </svg>
    <input type="range" min="0" max="100" v-model="radius">

    <ul>
      <li v-for="(bank, index) in banks" v-bind:key="bank.id">
        ID: {{bank.id}} NAME: {{bank.name}} ASSET: {{bank.asset}}兆円 || {{index}}
        <span v-if="bank.asset > 10">つよい！</span>
        <button @click="removeBank(index)">削除</button>
      </li>
    </ul>

    NAME:<input v-model="bankName">
    ASSET:<input v-model="bankAsset">
    <button @click="addBank">追加!</button>
    <br>
    <br>

    <button @click="doClicked">くぅ疲</button>
    <button @click.right="doClicked">くぅ疲右クリック</button>
    <a href="https://google.com" @click.prevent="doClicked">くぅ疲prevent</a>
    <button @click.capture="doClicked">くぅ疲capture</button>
    <input @keydown.esc="doClicked" value="くぅ疲escape">
    <p v-if="clicked">くぅ～疲れましたｗこれにて2019年終了ですｗｗ</p>

    <br>
    <br>

    <input v-model="message3">
    <br>
    <textarea v-model="message3"></textarea>
    <p>{{message3}}</p>
    <br>
    <input type="checkbox" v-model="checkBox">チェックボックス: {{checkBox}}
    <br>
    <input type="checkbox" v-model="bankList2" value="福岡銀行">福岡銀行
    <input type="checkbox" v-model="bankList2" value="熊本銀行">熊本銀行
    <input type="checkbox" v-model="bankList2" value="親和銀行">親和銀行
    <p>{{bankList2}}</p>
    <br>
    <input type="text" v-model.number="price">{{price}}

    <div id="bottom"></div>
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
        num: 0,
        isChild: true,
        isActive: true,
        classObject: {
          fukuoka: true,
          kumamoto: true,
          nagasaki: true,
          tokyo: false
        },
        attributes: {
          id: 1,
          alt: 'alt',
          src: 'https://www.fukuoka-fg.com/en/files/items/11195/Image/brand_img_02.jpg',
          width: '300px',
          height: '150px;'
        },
        radius: 50,
        banks: [
          {id: 1, name: '福岡銀行', asset: 16},
          {id: 2, name: '熊本銀行', asset: 1},
          {id: 3, name: '親和銀行', asset: 3},
          {id: 4, name: '十八銀行', asset: 3}
        ],
        bankName: "",
        bankAsset: "",
        clicked: false,
        message3: "Kadono",
        checkBox: true,
        bankList2: ["福岡銀行"],
        price: 177
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
    mounted() {
      console.log(this.$refs.firstMessage)
    },
    methods: {
      countUp() {
        if (this.num >= 3) {
          this.num = 0;
        } else {
          this.num++;
        }
      },
      addBank() {
        let max = this.banks.reduce(function (a, b) {
          return a > b.id ? a : b.id
        }, 0);
        this.banks.push({
          id: max + 1,
          name: this.bankName,
          asset: this.bankAsset
        })
      },
      removeBank(index) {
        this.banks.splice(index, 1);
      },
      doClicked() {
        this.clicked = this.clicked === false;
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

  #bottom {
    margin-top: 300px;
  }

  .v-enter-active, .v-leave-active {
    transition: opacity 1s;
  }

  .v-enter, v-leave-to {
    opacity: 0;
  }
</style>
