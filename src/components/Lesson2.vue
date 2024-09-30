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
    <h3>Good or Bad はscriptタグ内に処理をまとめたよ！これはcomputedのおかげだよ！</h3>
    <p>{{ evalution }}</p>
    <p>{{ score }}</p>
    <button @click="score++">+1</button>
    <h2>----------</h2>
    <h3>ウォッチエフェクトです</h3>
    <p>{{ count }}</p>
    <button @click="count++">+1</button>
    <p>ウォッチエフェクトとウォッチの違いは明示的に監視したいデータを指定するか否かの違いです。</p>
    <h2>----------</h2>
    <div :class="{ white: isWhite, 'bl-bg': isBlBlack }">htmlとcssをv-bindさせるお！</div>
    <p :class="{ red: true, white: true }">
      クラス名にハイフンがつく場合、シングルクォーテーションで囲む
    </p>
    <button @click="toggleClass">ナイトモーーーーード！</button>
  </div>
</template>

<script setup>
import { computed, ref, watchEffect } from 'vue'

const score = ref(0)
const evalution = computed(() => {
  return score.value > 3 ? 'Good' : 'Bad'
})
const vueURL = ref('https://vue.js.org')
const count = ref(5)
const message = ref('<h2>Hello, Vue.js</h2>')
const userInput = ref('')

function countUp() {
  count.value *= 2
}

watchEffect(() => {
  console.log('watchEffect')
  console.log(count.value)
})

const isBlBlack = ref(true)
const isWhite = ref(true)
function toggleClass() {
  isBlBlack.value = !isBlBlack.value
  isWhite.value = !isWhite.value //clickイベント。クリックしたらisWhiteのvalueが更新(書き換えられる)
}
</script>

<style scoped>
h2,
h3,
p {
  margin: 0;
}

.bl-bg {
  background-color: black;
}
.white {
  color: white;
}
.red {
  background-color: red;
}
</style>
