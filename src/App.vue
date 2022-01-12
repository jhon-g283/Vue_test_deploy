<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p>tomate</p>
  <ComandooComponent test_props=" 日曜洋画劇場！！"></ComandooComponent>
  <!-- コンポーネントとProps-->
  <HelloWorlds msg_p="Hello Vue 3 in CodeSandbox!" />
</template>

<script>
import HelloWorldVue2 from "./components/HelloWorld.vue";
import Comandoo from "./components/comand.vue";

// インポートした後に上の<template>タグないでPropsを渡してエクスポート

// HelloWorld.Vueでエクスポートされたコンポーネントをimportにより使用できるようにする
// components{}でHelloWorldsというコンポーネントを宣言（作成？）
// コロンはすでに宣言やインポートされたコンポーネントをそのコンポーネント（名前）として使用できるようにする

export default {
  name: "App",
  components: {
    HelloWorlds: HelloWorldVue2,
    // ここでインポートしたComandooファイルコンポーネントをComandooComponentコンポーネントとして使用する
    ComandooComponent: Comandoo,
  },
};
</script>

<style>
#appc {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
