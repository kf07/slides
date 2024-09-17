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

# CSSカスタムプロパティ（CSS変数）と@property
<style>
h1 {
  padding-top: 100px;
}
</style>
---

# CSSカスタムプロパティってなに？　
CSSで使える変数のこと
`--変数名：値`で宣言

```css
header {
  --themeColor: #00B5DE;
  background-color: var(--themeColor);
}
```

header内で宣言したCSSカスタムプロパティのため他では使えない
```css
footer {
  background-color: var(--themeColor);
}
```

継承されるため、宣言した要素内の要素では使用できる
```css
header {
  --themeColor: #00B5DE;
  background-color: var(--themeColor);
  p {
    background-color: var(--themeColor);
  }
}
```

---
layout: default
---

# 全体で使うには？
`:root`で宣言することでスコープがグローバルになり、どこからでも使うことができる

```css
:root {
  --themeColor: #00B5DE;
}

header {
  background-color: var(--themeColor);
}

footer {
  background-color: var(--themeColor);
}
```

---
layout: default
---


# Sassの変数との違いは？
- コンパイルせずに使用することができる
- 変数の値がSassは静的（コンパイル時に決定する）、CSSは動的

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
  --contentWidth: 980px;
}
@media (width <= 767px) {
  :root {
    --contentWidth: 600px;
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
    --themeColor: #00B5DE;
}
```
↓
```css
@property --themeColor {
    syntax: '<color>';
    inherits: false;
    initial-value: #00B5DE;
  }
```

syntax:　`'<color>'`,`'<length>'`, `'<number>'`, `'<percentage>'`などの型を指定することができて、不正な型が変数に代入された場合は初期値を適用する  
inherits:　継承するかどうか  
initial-value:　初期値

---
layout: default
---

# hoge
---
layout: default
---

<h2 class="title">ご清聴ありがとうございました！</h2>

<style>
.title {
--gradientColor1: #4158D0;
--gradientColor2: #C850C0;
--gradientColor3: #FFCC70;
 font-size: 32px;
 display: inline-block;
  background: linear-gradient(90deg, var(--gradientColor1), var(--gradientColor2) 30%, var(--gradientColor3));
  -webkit-background-clip: text;
-webkit-text-fill-color: transparent;
}
</style>