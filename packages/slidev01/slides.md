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
title: 明日から使えるCSS
mdc: true
---

# 明日から使えるCSS
<style>
h1 {
  padding-top: 100px;
}
</style>
---

# aspect-ratio
アスペクト比を指定できるCSS

要素を16/9の比率で固定したいとき
```css
.kv {
  padding-top: 56.25%;
}
```
↓

```css
.kv {
  aspect-ratio: 16 / 9;
}
```

---
layout: default
---

正方形(正円)をつくるとき
```css
.box {
  width: 100px;
  height: 100px;
}
```
↓
```css
.box {
  width: 100px;
  aspect-ratio: 1 / 1;
}
```
---
layout: default
---

# inset
top, right, bottom, leftの一括指定

全て0
```css
.box {
  inset: 0;
}
```

topとbottomが10px、rightとleftが0
```css
.box {
  inset: 10px 0;
}

```

top:10,right:20,bottom:30,left:0
```css
.box {
  inset: 10px 20px 30px 0;
}
```
---
layout: default
---

# is, where
複数のセレクタを1つにまとめられる擬似クラス
```html
<div class="parent">
    <div class="child1">子要素1</div>
    <div class="child2">子要素2</div>
</div>
```
```scss
.parent .child1,
.parent .child2 {

}
```
↓
```css
.parent :is(.child1, .child2) {

}
.parent :where(.child1, .child2) {

}
```

---
layout: default
---

# is, whereの違い
違いは詳細度

whereを使った場合はwhere()の部分は詳細度に含まれない
```scss
.parent :is(.child1, .child2) { //詳細度0,2,0
}
.parent :where(.child1, .child2) { //詳細度0,1,0
}
```

isは()の中の詳細度が強い方に引っ張られるので注意
```scss
.parent :is(.child1, #child2) { //詳細度1,1,0
}
```


---
layout: default
---

# nth-childのof構文
nth-childのフィルター
```html
<div class="section">
    <h2>タイトル</h2>
    <p>子要素1</p>
    <p>子要素2</p>
</div>
```
1番目のpにスタイルを当てたいとき、これだと1番目の要素h2にスタイルが当たってしまう
```scss
.section :nth-child(1) {
}
```
↓
```scss
.section :nth-child(1 of p) {
}
```
クラス名での指定もできる(.textがついてる要素の中で1番目)
```css
.section :nth-child(1 of .text) {
}
```

---
layout: default
---

# marginの論理プロパティ
インライン方向のmargin指定 margin-inline  
ブロック方向のmargin指定 margin-block

よくある左右中央寄せ
```scss
.block {
  width: fit-content;
  margin: 0 auto; //またはmargin: auto;
}
```
↓
```css
.block {
  width: fit-content;
  margin-inline: auto;
}
```
---
layout: default
---

# place-items
align-itemsとjustify-itemsの一括指定(flex,gridアイテムの位置指定のプロパティ)

一括指定
```css
  place-items: center;
```

align-items: center, justify-items: start
```css
place-items: center start;
```

---
layout: default
---

要素の上下左右中央寄せ

```html
<div class="wrap">
    <div>子要素</div>
</div>
```

```css
 .wrap {
    display: grid;
    place-items: center;
  }
```

---
layout: default
---

# メディアクエリの書き方
画面幅の範囲を指定するメディアクエリを以前より簡潔に書くことができる
```css
@media (max-width: 767px) {
}
```
↓
```css
@media (width <= 767px) {
}
```

こんな書き方もできます
```css
@media (400px <= width <= 700px) {
}
```

---
layout: default
---

# transformの個別指定
transformのプロパティを個別にかけるようになった
```css
transform: translateX(50%) rotate(30deg) scale(1.2);
```
↓
```css
translate: 50% 0;
rotate: 30deg;
scale: 1.2;
```

---
layout: default
---

# サブグリッド
本来のgridでは直下の要素しかグリッドとならずグリッド内の子要素には影響がないが、  
subgridを使うと親グリッドとその子要素のグリッドを連携させることができる
```html
<div class="grid-wrap">
  <div class="grid-item"><h2>タイトル</h2><p>テキスト</p></div>
  <div class="grid-item"><h2>タイトル</h2><p>テキスト</p></div>
  <div class="grid-item"><h2>タイトル</h2><p>テキスト</p></div>
</div>
```

```scss
.grid-wrap {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}

.grid-item { //サブグリッドの指定
    display: grid;
    grid-template-rows: subgrid;
    grid-row: span 3;
    row-gap: 10px;
}
```

---
layout: default
---


# 紹介しきれなかったもの
- コンテナクエリ
- accent-color
- View Transitions API
- color-mix
- scroll-snap  
  ...など

---
layout: default
---

<h2 class="title">ご清聴ありがとうございました！</h2>

<style>
.title {
 font-size: 32px;
 display: inline-block;
  background: linear-gradient(90deg, #4158D0, #C850C0 30%, #FFCC70);
  background: -webkit-linear-gradient(0deg, #4158D0, #C850C0 30%, #FFCC70);
  -webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}
</style>