Idea
====

- 囲み記号
  - ()
  - {}
  - []
  - <>
- 重心が真ん中
  - =
  - +
  - -
  - *
  - /
  - \
  - %
  - &
  - |
  - !
  - $
  - @
  - #
  - :
  - ;
- 重心が上
  - '
  - "
  - `
  - ^
  - ~
- 重心が下
  - .
  - ,
  - _


- 接辞 affix (operator|function)
  - 接頭辞 prefix
    - 0xFF
  - 接中辞 infix
    - a + b
  - 接尾辞 suffix, postfix(Swift)
    - 1.0r
  - 接周辞 circumfix
    - %Q|hoge|
- 拡張子
  - .pt
- Objective vs Functional
  - 全てがオブジェクトであり関数
  - 変数というかシニフィエと言うか
    - var and let
    - Swift
- 正格と非正格(Eager, Lazy)
  - dog.bark! #-> 評価される
  - dog.bark #-> 関数オブジェクトが返る
  - let and let!
- Optional型みたいなの入れたい
  - 変数に nil が入るのを許す
  - Swift
    - wrap and unwrap
    - http://qiita.com/cotrpepe/items/e30c7442733b93adf46a
    - unwrap って必要なのか？
  - Ceylon
  - CoffeeScript
    - チェインできる
      - dog?.bark
      - これはOptional”型”では無いかな……
- 人間に優しい型
  - Rational, Complex, BigNum がデフォルト
  - Float や Int32 や Bit などの内部表現を表すものは手動で宣言して使う
- 関数
  - 全ての関数を無名関数にしたい
    - bark = func v1, v2 do … end みたいな
    - JavaScript や Lua みたいにたまたま名前が付いてるみたいな書き方
  - 演算子はない
- 半角スペース必須にしようかな……
  - コードゴルフは諦めてもいい
- 前置・中置・後置の関数があるだけ
  - 一つの関数を使い回し
  - Haskell の中置は 100 `div` 50 だがダサい
  - リテラルもこの方式でやりたい
- 関数宣言はすべて配列引数とキーワード引数兼用
  - func f(foo, bar, baz)
  - f(a, baz: c) # fooにa、bazにcが入りbarだけ未定義の関数オブジェクトを返す
- 数学記号を意識する
  - Haskell
- Unicode文字列を関数名変数名に使える
  - ↑(タワー記号)とか
- インタプリタもコンパイルもどっちもしたい
  - ASTはS式にしたい
    - S式はインデント部分だけ拡張
  - Soft-Typing
    - ダックタイプで静的解析
  - インタプリタ
  - LuaJIT は速いらしい
  - コンパイル
    - tup が速いらしい
    - http://gittup.org/tup/index.html)
    - Go が速い
    - LLVM IR 使いたい
- 内部DSLに向いた記法
- 標準でDDD(ドメイン駆動設計)を援用したい
  - eval やりたくない
    - persec みたいなもんで何とかならんか
  - チェイン
    - Haskell の $、F# の |> みたいなやつ
    - sh のパイプいいけどビット演算子と被る
    - f :: a -> [Num, Str] のとき
      - f | g(%[0], %[1]) として返り値を渡せる
  - 下記シェルとの絡みで複数を表すときにカンマは必須じゃないようにしたい
    - 配列や引数などは慣習として付けるみたいな
    - cond みたいなの欲しい
    - if文に else は必須になるのかな？
      - 再代入を許すかどうか……
- fluently
  - メソッドチェイン、パイプ
- FRP
  - filter, map, reduce
- 暗黙的マッピング
  - okuji さんの言う単一のものだったら複数だったに自動で対応できるのでは？
  - Gura言語を参考
- do … end は { … } で代用できる？
  - {} は無名関数か？
  - 節をどうやって定義しよう？
    - rescue節とかpublic/protected/privateとか
    - 引数に複数ブロックを与えられるみたいなもん？
- パターンマッチは是非とも欲しい
- 入出力などの関数から外れる奴どうしよう
  - モナドか一意型か……
- 後置ifとか後置rescueみたいなのどうしたらいいんだ？
  - 関数と演算子を分けないと対応できないのか？
    - アノテーション
    - 関数やなんやらに属性付けたいときは<…>がええかもな。余ってるし。

```yaml
- memo
  - reference languages
    - haskell, ocaml, f#, elixir, erlang
    - clojure, scheme, clisp
    - ruby, lua, moonscript, coffee, js, perl, python, php
    - rust, go, c#, java, c, c++
  - evaluation
    - default lazy
      - haskell, concurrent clean
    - default eager
      - d, ocaml, ml, scala, scheme, ...
  - option-al type or value
    - chaining
      - coffee, swift
        - obj.m1?.m2?.m3
      - clojure
    - wrap and unwrap
  - closure
    - scope
      - ruby
        proc/Proc.new メソッドを抜ける            手続きオブジェクトを抜ける   例外が発生する
        lambda        手続きオブジェクトを抜ける  手続きオブジェクトを抜ける   手続きオブジェクトを抜ける
        block         メソッドを抜ける            手続きオブジェクトを抜ける   メソッドを抜ける
    - noname
      - lazy
        - coffee
          (x, y) ->
            ...
        - php
          function($x, $y) { ... }
      - eager
        - coffee
          do (x, y) ->
            ...
      - over scope
        - php
          function($x, $y) use(&val) { ... }
  - switch, case, match and so on
    - rust
      match n {
        n if n < 0 => ...
        0 => ...
        1 | 2 => ...
        n @ 3 => ...
        _ => ...
      }
    - elixir
      case n do
        0 -> ...
        _ -> ...
      end
  - recursive function
    - haskell
      - default
    - ocaml
      let rec f n = ...

```

## Functions


```
// function
fun concat x y { x ++ y }
fun concat x, y { x ++ y }
fun concat(x y) { x ++ y }
fun concat(x, y) { x ++ y }
fun concat(x,y){x++y}

fun concat x y
  x ++ y

fun concat x y {
  x ++ y
}

fun concat x y do
  x ++ y
end


// lambda
let concat = \ x y -> x ++ y
let concat = \ x y -> { x ++ y }
let concat = \ x -> \ y -> x ++ y
let concat = \(x y) -> x ++ y


let concat =
  \ x y ->
    x ++ y

let concat = \ x y -> {
  x ++ y
}

let concat = \ x y -> do
  x ++ y
end


// closure
let concat = { x y => x ++ y }
let concat = { x y => { x ++ y } }
let concat = { x => { y => x ++ y } }
let concat = { x, y => x ++ y }
let concat = {x,y=>x++y}

let concat =
  x y => x ++ y

let concat = {
  x y => x ++ y
}

let concat = do
  x y => x ++ y
end
```


do, with, where, in, then は全て等価とか？
シンボルは#がいいかも（Smalltalk風、というよりはTwitter風）
struct と 連想配列 は同じものとする？


## Match

```
// function
fun fact n
  0 => 1
  n => n * fact(n - 1)

fun fact n {
  0 => { 1 }
  n => { n * fact(n - 1) }
}

fun fact n do
  0 => 1
  n => n * fact(n - 1)
end


// lambda
let fact = \ n ->
  0 => 1
  n => n * fact(n - 1)

let fact = \ n -> {
  0 => 1
  n => n * fact(n - 1)
}

let fact = \ n -> do
  0 => 1
  n => n * fact(n - 1)
end



fun pluralize x
  0 => "no unit"
  1 => "a unit"
  n => "\(n) units"

fun unit x
  0 | 1 => "unit"
  _ => "units"
```


## chaining
```
let ary = [0, 1, 2, 3 ,4]

// closure
let ss = ary.map({ n => n ** 2 }).reduce(0 { sum n => sum + n })
let ss = ary.map{ n => n ** 2 }.reduce 0 { sum n => sum + n }

let ss = ary.map {
  n => n ** 2
}.reduce 0 {
  sum n => sum + n
}

let ss = ary.map do
  n => n ** 2
end.reduce 0 do
  sum n => sum + n
end


// lambda
let squares = ary.map(\ n -> n ** 2).reduce(0 \ sum n -> sum + n)
let squares = ary.map(\ n -> n ** 2).reduce(0, \ sum n -> sum + n)
let squares = ary.map(\ n -> { n ** 2 }).reduce(0, \ sum n -> { sum + n })

let ss =
  ary.map \ n ->
    n ** 2
  .reduce 0 \ sum n ->
    sum + n

let ss = ary.map \ n -> {
  n ** 2
}.reduce 0 \ sum n -> {
  sum + n
}

let ss = ary.map \ n -> do
  n ** 2
end.reduce 0 \ sum n -> do
  sum + n
end
```


