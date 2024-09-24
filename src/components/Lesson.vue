<script setup>
import { ref, reactive } from 'vue'
const title = 'Vue.js Lesson'
let price = ref(9.99)

function increment() {
  price.value += 1
  console.log(price)
}

// リアクティブな値の宣言はオブジェクトでも可
const info = ref({
  students: 1000,
  rating: 5
})

const instructor = reactive({
  name: 'Sagesaka',
  age: 25
})

const instructor_info = reactive({
  name: 'Sagesaka',
  sns: {
    twitter: 'sageru'
  }
})
console.log(instructor.age)
console.log(info.value.students)
</script>

<template>
  <h1>title: {{ title }}</h1>
  <h2>price: ${{ price }}</h2>
  <h2>Students: {{ info.students }}</h2>
  <h2>Instructor: {{ instructor.name }}({{ instructor.age }})</h2>
  <h2>Twitter: {{ instructor_info.sns.twitter }}</h2>
  <button @click="increment">ボタン</button>
</template>

<!--<template>タグ内はrefオブジェクトを認識してくれるので、{{}}内には.valueをつけない
  <script>タグ内には.valueをつける！-->
