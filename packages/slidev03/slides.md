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
title: CSSカスタムプロパティと@property
mdc: true
---

# CSSカスタムプロパティの@propertyについて
<style>
h1 {
  padding-top: 100px;
}
</style>
---

# CSSカスタムプロパティってなに？　
CSSで使える変数のことで、 何回も使用する値を変数にすることで管理がしやすくなる  
`--変数名：値`で宣言して`var(--変数名)`で使用する

```css
header {
  --theme-color: #00B5DE;
  background-color: var(--theme-color);
}
```

要素内で変数宣言したCSSカスタムプロパティは他では使えない
```scss
footer {
  background-color: var(--theme-color); //使用不可
}
```

---
layout: default
---

# 全体で使うには？
`:root`で宣言することでスコープがグローバルになり、どこからでも使うことができる

```css
:root {
  --theme-color: #00B5DE;
}

header {
  background-color: var(--theme-color);
}

footer {
  background-color: var(--theme-color);
}
```

---
layout: default
---


# Sassの変数との違いは？
- コンパイルせずに使用することができる
- 変数の値がSassは静的（コンパイル時に決定する）、CSSは動的

Sass
```scss
$theme-color: #00B5DE;
header {
  background-color: $theme-color;
}
```
↓コンパイル
```scss
header {
  background-color: #00B5DE; //CSSに変換された時点で固定になる
}
```

---
layout: default
---

# CSSカスタムプロパティが動的なことでできること

---
layout: default
---

## メディアクエリで変数の値を切り替える
変数の値を画面サイズなどによって切り替えることができる
```css
:root {
  --content-width: 980px;
}
@media (width <= 767px) {
  :root {
    --content-width: 600px;
  }
}
```

```css
:root {
  --text-color: #333;
  --bg-color: #FFF;
}
/*ダークモード用の変数*/
@media (prefers-color-scheme: dark) {　
  :root {
    --text-color: #FFF;
    --bg-color: #333;
}
```

---
layout: default
---

## JSで変数の値を書き換える

JSで変数にアクセスすることができるので書き換えたり取得したりできる

```javascript
document.documentElement.style.setProperty('--bg-color', '#000');
```

---
layout: default
---

# CSSカスタムプロパティの@propetyとは
最近全ブラウザで使用することができるようになったCSSカスタムプロパティの型を設定できる構文

```css
:root {
    --theme-color: #00B5DE;
}
```
↓
```css
@property --theme-color {
    syntax: '<color>';
    inherits: false;
    initial-value: #00B5DE;
  }
```


syntax:　
`'<color>'`,`'<length>'`, `'<number>'`, `'<percentage>'`などの型を指定することができて、不正な型が変数に代入された場合は初期値を適用する
`'block | none'`のように特定の値を指定することもできる
inherits:　継承するかどうか  
initial-value:　初期値

---
layout: default
---

CSSカスタムプロパティの型安全
```scss
:root {
  --theme-color: #00B5DE;
}

.box {
  --theme-color: 120px;
  background-color: var(--theme-color); //120pxが使用されスタイルが当たらなくなってしまう
}
```
```scss
@property --theme-color {
    syntax: '<color>';
    inherits: false;
    initial-value: #00B5DE;
}

.box {
  --theme-color: 120px;
  background-color: var(--theme-color); //初期値の#00B5DEが適用される
}
```
---
layout: default
---

## CSS変数の継承

 CSS変数の値を変更したとき、その変更後の値を子要素にも引き継ぐがどうかの設定ができる

```scss
@property --text-color {
    syntax: '<color>';
    inherits: true;
    initial-value: red;
}

.text1 {
  --textColor: blue;
  color: var(--text-color);
  .text2 {
      color: var(--text-color); //inheritsがtrueの場合はblue、falseの場合は初期値のredが適応される
  }
}
```
---
layout: default
---

## 型を指定することで値の変化をアニメーションさせることができる
https://codepen.io/kan_f/pen/RwzzJVv

---
layout: default
---

<h2 class="title">ご清聴ありがとうございました！</h2>

<style>
.title {
--gradient-color1: #4158D0;
--gradient-color2: #C850C0;
--gradient-color3: #FFCC70;
 font-size: 32px;
 display: inline-block;
  background: linear-gradient(90deg, var(--gradient-color1), var(--gradient-color2) 30%, var(--gradient-color3));
  -webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}
</style>