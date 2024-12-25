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
title: 配列について
mdc: true
---

# いい感じに配列操作できるようになろう!
<style>
h1 {
  padding-top: 100px;
}
</style>
---

## 今日伝えたいこと

```javascript
const content = [
  {
    id: 1,
    title: '配列の破壊的メソッドはなるべく使わない'
  },
  {
    id: 2,
    title: '適切な配列メソッドを使おう',
  },
  {
    id: 3,
    title: 'よく使う配列の処理色々',
  }
]
```

<style>
h2 {
margin-bottom: 30px;
}
code {
font-size: 16px;
}

</style>
---
layout: default
---

# 破壊的メソッドはなるべく使わない

---
layout: default
---

## 破壊的メソッドってなあに?

配列そのものを変更してしまうメソッド

破壊的メソッドに該当するもの  
push(配列の末尾に追加)、pop(配列の末尾を削除)、unshift(配列の最初に追加)... など

実際の挙動
```javascript
const array = [1, 2, 3, 4, 5];
array.push(6); //配列の末尾に6を追加
console.log(array) //[1, 2, 3, 4, 5, 6]
array.pop() //配列の末尾を削除
console.log(array) //[1, 2, 3, 4, 5]
```
pushなどの破壊的メソッドは、元々の配列自体を変更してしまって、配列が現在どういう状態なのかわかりづらくなってしまう、、  

→**バグや副作用の原因となり得る**

---
layout: default
---

## じゃあ配列の操作をしたいときはどうしたら？🤔

配列操作のときは直接操作せずに、追加、削除などの操作をした新しい配列をつくる

元々の配列の保持しつつ、操作をした配列を別につくることで、配列の状態がわかりやすくなる


---
layout: default
---

配列への追加は配列を展開するスプレッド構文(...)を使用  
スプレッド構文は配列を展開できる構文「...array」

配列の末尾に追加(pushの代わり)
```javascript
const array1 = [1, 2, 3, 4, 5];
const array2 = [...array1, 6];
console.log(array2); //[1, 2, 3, 4, 5, 6]
console.log(array1); //[1, 2, 3, 4, 5] 元々の配列が保持される
```

配列の最初に追加(unshiftの代わり)
```javascript
const array1 = [1, 2, 3, 4, 5];
const array2 = [6, ...array1];
console.log(array2); //[6, 1, 2, 3, 4, 5]
console.log(array1); //[1, 2, 3, 4, 5] 元々の配列が保持される
```

配列の末尾を削除(popの代わり)
```javascript
const array1 = [1, 2, 3, 4, 5];
const array2 = array1.filter((_, index) => index !== array1.length - 1); //配列の最後以外を返す = 配列の末尾を削除
console.log(array2); //[1, 2, 3, 4];
console.log(array1); //[1, 2, 3, 4, 5] 元々の配列が保持される
```
---
layout: default
---


他の破壊的メソッド(splice,sort)なども非破壊メソッドで実装できます

sort(破壊的メソッド)
```javascript 
const array = [10,1,0,3,9];
array.sort((a, b) => a - b);
console.log(array); //[0, 1, 3, 9, 10]
```

toSorted(非破壊メソッド)
```javascript
const array1 = [10,1,0,3,9];
const array2 = array1.toSorted((a, b) => a - b);
console.log(array2) //[0, 1, 3, 9, 10]
console.log(array1) //[10, 1, 0, 3, 9]
```

破壊的メソッドを使わないで実装するように意識してみよう

---
layout: default
---

# 適切な配列構文を使おう
配列に対してfor of(forEach)を使うときは、他に適した配列構文がないかを考える

---
layout: default
---
```javascript
const array = [
	{
		id: 1,
		name: 'アイテム1',
		price: 1000,
	},
	{
		id: 2,
		name: 'アイテム2',
		price: 2000,
	},
	{
		id: 3,
		name: 'アイテム3',
		price: 3000,
	},
]
```


---
layout: default
---

特定の要素を探して変数に入れる処理
```javascript
let target;
for (const item of array) {
	if (item.price === 3000) {
		target = item;
		break;
	}
}
console.log(target) //{id: 3, name: 'アイテム3', price: 3000}
```

for ofを使用せずにfindを使用して実装  
findは配列の中から特定の要素を探すメソッド
```javascript
const target = array.find((item) => {
  return item.price === 3000;
})

console.log(target) //{id: 3, name: 'アイテム3', price: 3000}
```

適切な配列処理をすることで  
**何をしている処理なのかが配列メソッドを見たらある程度わかるので可読性が上がる**



---
layout: default
---

# よく使う配列の処理色々まとめ
find  
配列から条件に一致する最初の要素を返す
```javascript
const array = [1, 2, 3, 5, 9, 12, 17];
const result = array.find((num) => {
  return num >= 10
})
console.log(result) //12
```

filter  
配列から条件に一致する要素のみの配列を返す
```javascript
const array1 = [1, 2, 3, 5, 9, 12, 17];
const array2 = array1.filter((num) => {
	return num >= 10
})
console.log(array2) //[12, 17]
```

---
layout: default
---


map  
配列の全ての要素に対してある処理を行った配列を返す
```javascript
const array1 = [1, 2, 3, 5, 9, 12, 17];
const array2 = array1.map((num) => {
	return num * 2;
})
console.log(array2) //[2, 4, 6, 10, 18, 24, 34]
```
---
layout: default
---

every  
配列の全ての要素が条件に一致するときtrue, それ以外はfalse
```javascript
const array = [1, 2, 3, 5, 10, 12, 17];
const result = array.every((num) => {
	return num >= 10;
})
console.log(result) //10以上じゃない要素があるためfalse
```

some  
配列の要素の内、1つでも条件に一致するときtrue, それ以外はfalse
```javascript
const array = [1, 2, 3, 5, 10, 12, 17];
const result = array.some((num) => {
	return num >= 10;
})
console.log(result) //10以上の要素が1つ以上あるのでtrue
```

---
layout: default
---

## ご清聴ありがとうございました！
