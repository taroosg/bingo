# vanilla JS bingo

## DEMO

[https://taroosg.github.io/bingo/](https://taroosg.github.io/bingo/)

## 雑な方針の解説

適当にランダムな数の入った配列を作り，5\*5 の 2 次元配列の形にする．
下の例は数字が適当．

```js
const data = [
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
  [11, 12, 13, 14, 15],
  [16, 17, 18, 19, 20],
  [21, 22, 23, 24, 25],
];
```

どこがクリックされたか判定するための配列をつくっておく．
リーチやビンゴの管理はこちらで行う．
（クリックしたマスに対応する部分を true にする）

```js
const result = [
  [false, false, false, false, false],
  [false, false, false, false, false],
  [false, false, false, false, false],
  [false, false, false, false, false],
  [false, false, false, false, false],
];
```

がんばって表示用の配列を画面に表示する．

```html
<tr>
  <td id="0_0">1</td>
  <td id="0_1">2</td>
  <td id="0_2">3</td>
  <td id="0_3">4</td>
  <td id="0_4">5</td>
</tr>
```

みたいな感じにした（id の付け方が大事かも）．

クリックしたら該当する<td>から id を取り出し，結果表の対応する部分を true にする．
例えば`<td id="0_3">3</td>`をクリックしたら結果表を下のように更新する．

```js
[
  [false, false, true, false, false],
  [false, false, false, false, false],
  [false, false, false, false, false],
  [false, false, false, false, false],
  [false, false, false, false, false],
];
```

更新したら縦横斜めで全部 true になっている部分があるかどうかチェックする．

クリックするたびに上記チェックを行い，ビンゴになってたらアラート！
