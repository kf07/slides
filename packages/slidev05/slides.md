---
theme: apple-basic
layout: intro
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.
  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: Vue3
mdc: true
---

# Vueのハードルを下げたいVue　のいいところ

<style>
h1 {
  padding-top: 100px;
}
img {
text-align: right;
width:200px;
transform: rotate(10deg);
}
.img {
display: flex;
justify-content: flex-end;
}
</style>
---

## Vueってなに？？
- Vueは、**UIを作るためのJavaScriptフレームワーク**
- Webアプリケーションを、**効率よく構造的に**作るための仕組み
- よくある使い方
    - ボタンを押したら何かが変わる
    - 入力欄に文字を入れると表示が変わる
    - 状態によって表示が変わる　　...など
---
layout: default
---

## 🧱 そもそも、なぜフレームワークを使うの？

- 素のJavaScriptだけでもアプリはつくれるれるけど、**設計がバラバラになりやすい**
- フレームワークを使えば、基本的なルールが決まっているので設計の手助けになる
- 結果として、
    - **保守性が高くなる**
    - **メンバー間での理解が早い**
    - **迷いにくい開発体験**
    - **コードの書き方を統一できる**

> →実装に集中しやすい！
---
layout: default
---

## 学習コストが低い

- テンプレート構文が**HTMLに似ていてわかりやすい**
- データの表示やイベントもわかりやすい構文で書ける
- `v-for`, `v-if` など直感的に使える
- データとUIの表示が直感的

```vue
<template>
  <button @click="count++">+1</button>
  <p>{{ count }}</p>
  <p v-if="count > 0">countの値が1以上</p>
</template>

<script setup>
import { ref } from 'vue';
const count = ref(0);
</script>
```

---
layout: default
---

## 1つのファイルで完結する

- .vueファイルの中にHTML/JS/CSSが全部書ける
- コンポーネントごとに処理を分けて管理できる
- スタイルのスコープもつけられるので管理がしやすい

counter.vue
```vue
<script setup>
  import { ref } from 'vue';
  const count = ref(0);
</script>

<template>
  <button @click="count++" class="btn">+1</button>
  <p>{{ count }}</p>
</template>

<style scoped>
  .btn {
    background-color: blue;
  }
</style>
```

---
layout: default
---

## 素のJSより処理がわかりやすい
- 通常のJSだと　イベントリスナーの登録、DOM操作が必要
- VueならデータとUIが自動的に同期される
```html
HTML,JS
<input type="text" id="message" />
<p><span id="count">0</span>文字</p>
<script>
  const input = document.getElementById('message');
  const count = document.getElementById('count');
  input.addEventListener('input', () => {
    count.innerText = input.value.length;
  });
</script>
```


```vue
Vue
<script setup>
import { ref } from 'vue';
const message = ref('');
</script>

<template>
  <input v-model="message" />
  <p>{{ message.length }}文字</p>
</template>

```

---
layout: default
---


## まとめ
1. 学習コストが低い（構文が直感的）
2. 1ファイルで完結する（構造が見えやすい）
3. 素のJSより書きやすい（UIと状態が同期される）
---
layout: default
---



## ご清聴ありがとうございました！
