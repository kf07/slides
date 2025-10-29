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
title: 自分がいなくなっても動くコードを書くということ
mdc: true
---

# 自分がいなくなっても<br>動くコードを書くということ
<div class="img">
<img src="/balloon.png" alt="javascript" class="img2" />
<img src="/penguin.png" alt="" class="img1" />
</div>

<style>
h1 {
  padding-top: 100px;
}
.img1 {
text-align: right;
width:200px;
transform: rotate(10deg);
}
.img2 {
display: block;
text-align: right;
width: 400px;
}
.img {
display: flex;
justify-content: flex-end;
}
</style>
---

## 参画時の話
- 今まで一人、または少人数で開発することが多かった
- チームの設計思想等で自分のやり方と違っていた部分があった
- レビューでコードの設計や命名、責務分けの考え方など「チームで開発する」ということを学ぶ日々

---
layout: default
---

## チーム開発の難しさ
- メンバーの入れ替わりを何度も経験
- 自分が書いたコードを他の人が引き継ぐ場面もあれば、 逆に離任した人も含めて自分以外のコードを読み解くことも多かった
- コードが「他の人にやさしい」設計かどうかで、 チーム全体のスピードが全然違うと実感した

---
layout: default
---

## 「触るのが怖い」機能

- 動いてはいるけど複雑で、意図がわからない
- 既存機能に追加実装を重ねるたびにさらに複雑に  
  → 結果的に誰も手を入れたくないコードになってしまう



---
layout: default
---


# 意識するようになった3つのこと

1️⃣ コードを書くということは、意思を伝えるということ  
2️⃣ なぜそう書いたのかを残す   
3️⃣ 続けられるコード

---
layout: default
---


## コードを書くということは、意思を伝えるということ

- コードは動くだけじゃなく、開発者の考え方を伝える手段
- 命名・関数の分け方など、すべてが次の開発者やメンバーへのメッセージになる
- 「自分だけがわかる」ではなく、「読んだ人が理解できる」ことを意識

---
layout: default
---

## なぜそう書いたのかを残す
- コードだけでは伝わらない背景を、必要に応じてPR説明やコメントで補う
- 「なぜこうしたのか」「こういう書き方をなぜ避けたのか」 それを1行でも書いておくと、次の人の判断材料になる
  → 意図を残すことで、スムーズな改善、修正につながる

---
layout: default
---

## 続けられるコード
- コードは今後もずっと引き継がれていくチームの財産
- いま書いているコードが今後も何年もそのコードが使われていくことを意識する  
  → ほかの人が見たとき、将来の自分が見たときに意図がわかる設計になっているか
- 「チーム全体で育てていけるコード」になっているかを意識する

---
layout: default
---

## まとめ
- 意図が伝わるコードは、時間が経ってもチームを助ける
- 自分がいなくなっても伝わるコードを書くことが、 チームを強くすることにつながる
- その積み重ねが、チームの文化をつくっていく

---
layout: default
---

## 最後に
- このチームでたくさんレビューしてもらって、 コードの設計や意図を考える習慣がついて、技術的にも成長できた。
- バグの修正なども大変で辛かったけど成長に大きく繋がった
