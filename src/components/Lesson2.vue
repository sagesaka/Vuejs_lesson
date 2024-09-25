<template>
  <div>
    <h3>{{ count < 10 ? 'Yes' : 'No' }}</h3>
    { { count < 10 ? 'Yes' : 'No' } }
    <p>波括弧内では単一式のみかけます。if文は書けません。</p>
    <h2>----------</h2>
    <h3>{{ count }}</h3>
    <p v-text="count"></p>
    <p>v-textは真似するよ！</p>
    <h2>----------</h2>
    <div v-html="message"></div>
    <p>
      v-htmlは引数に与えられたhtmlタグを認識して表示させるよ！
      inputタグも認識するから、悪意あるユーザーいたずらされちゃうから、ユーザーから受け取る情報は使わないよ！
    </p>
    <h2>----------</h2>
    <a :href="vueURL">ドキュメントです</a>
    <p>v-bind:属性とすることで、縛る紐づけすることができるよ！</p>
    <p>コロンのみで省略可能！:a href=""とか:id=""とかとか！</p>
    <p>
      v-bindは属性値にたいして有効 boolean型のfalseやundefinedをv-bindすると属性値を無効化するよ！
    </p>
    <h2>----------</h2>
    <div>
      <button @click="count++">button</button>
      {{ count }}
      <p>処理を直接かくことをインラインハンドラ</p>
    </div>
    <div>
      <button @click="countUp">2倍するよ</button>
      {{ count }}
      <p>メソッドを呼び出して処理を起こすことをメソッドハンドラ</p>
    </div>
    <h2>----------</h2>
    <input type="text" v-model="userInput" />
    <h3>右に表示されます:{{ userInput }}</h3>
    <p>v-modelでフォームに入力されたデータを取得！</p>
    <h2>----------</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const vueURL = ref('https://vue.js.org')
const count = ref(5)
const message = ref('<h2>Hello, Vue.js</h2>')
const userInput = ref('')

function countUp() {
  count.value *= 2
}
</script>

<style scoped>
h2,
h3,
p {
  margin: 0;
}
</style>
