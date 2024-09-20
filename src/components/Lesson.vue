<script setup>
import { ref } from 'vue'
const title = 'Vue.js Lesson'
let price = ref(9.99)

function increment() {
  price.value += 1
  console.log(price)
}
</script>

<template>
  <h1>title: {{ title }}</h1>
  <h2>price: ${{ price }}</h2>

  <button @click="increment">ボタン</button>
</template>

<!--<template>タグ内はrefオブジェクトを認識してくれるので、{{}}内には.valueをつけない
  <script>タグ内には.valueをつける！-->
