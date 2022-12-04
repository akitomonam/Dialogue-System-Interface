<template>
  <!-- <img alt="Vue logo" src="./assets/lab_logo.png" class="header-logo"> -->
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HelloWorld from './components/ChatBot.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<!--
このコードは、Vue.js アプリケーションのエントリポイントとなる App.vue ファイルです。
<template> セクションには、Vue コンポーネントの HTML テンプレートが記述されています。ここでは、<img> タグと、カスタムコンポーネント HelloWorld を使用しています。
<script> セクションには、Vue コンポーネントのロジックが記述されています。ここでは、HelloWorld コンポーネントをインポートし、App コンポーネントで使用するために登録しています。
<style> セクションには、Vue コンポーネントのスタイルが記述されています。ここでは、HTML 要素の #app にスタイルを適用しています。
-->
