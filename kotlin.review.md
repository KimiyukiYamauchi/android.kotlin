<!-- TOC -->

# 目次

- [文字列の結合について理解度を高める](#文字列の結合について理解度を高める)
  - [Cap02-01.kt](#cap02-01kt)
- [変数宣言と型について理解度を高める](#変数宣言と型について理解度を高める)
  - [Cap02-02.kt](#cap02-02kt)
- [変数宣言と型(方推論)について理解を高める](#変数宣言と型方推論について理解を高める)
  - [Cap02-03.kt](#cap02-03kt)
- [変数宣言の仕方について理解度を高める](#変数宣言の仕方について理解度を高める)
  - [Cap03-01.kt](#cap03-01kt)
- [関数とラムダ式について理解度を高める](#関数とラムダ式について理解度を高める)
  - [Cap03-02.kt](#cap03-02kt)
- [高階関数について理解度を高める](#高階関数について理解度を高める)
  - [Cap03-03.kt](#cap03-03kt)
- [論理演算子の理解度を高める](#論理演算子の理解度を高める)
  - [Cap04-01.kt](#cap04-01kt)
- [if式の理解度を高める](#if式の理解度を高める)
  - [Cap04-02.kt](#cap04-02kt)
- [Listの理解度を高める1](#listの理解度を高める1)
  - [Cap04-03.kt](#cap04-03kt)
- [Listの理解度を高める2](#listの理解度を高める2)
  - [Cap04-04.kt](#cap04-04kt)
- [try-finallyの復習](#try-finallyの復習)
  - [Cap05-01.kt](#cap05-01kt)
- [null許容型とletの理解度を高める](#null許容型とletの理解度を高める)
  - [Cap05-02.kt](#cap05-02kt)
- [リストとforループの復習1](#リストとforループの復習1)
  - [Cap05-03.kt](#cap05-03kt)
- [リストとforループの復習2](#リストとforループの復習2)
  - [Cap05-04.kt](#cap05-04kt)
- [リストとmapの理解度を高める](#リストとmapの理解度を高める)
  - [Cap05-05.kt](#cap05-05kt)
- [enum classについて理解度を高める](#enum-classについて理解度を高める)
  - [Cap06-01.kt](#cap06-01kt)
- [when式について理解度を高める](#when式について理解度を高める)
  - [Cap06-02.kt](#cap06-02kt)
- [companion objectについて理解度を高める](#companion-objectについて理解度を高める)
  - [Cap07-01.kt](#cap07-01kt)
- [可変長引数について理解度を高める](#可変長引数について理解度を高める)
  - [Cap07-02.kt](#cap07-02kt)
- [引数なしのwhenについて理解度を高める](#引数なしのwhenについて理解度を高める)
  - [Cap07-03.kt](#cap07-03kt)

<!-- /TOC -->

## 文字列の結合について理解度を高める

### Cap02-01.kt

```kotlin
fun main() {
    // varは再代入できる変数
    var name = "Android"

    // 文字列は＋演算子で結合することができる
    println("Hello " + name + "!") // printlnは改行のある出力

    // $変数名で変数の値を文字列に埋め込む
    println("Hello $name!")

    // varなので再代入できる
    name = "Kotlin"
    println("Hello $name!")
}
```

## 変数宣言と型について理解度を高める

### Cap02-02.kt

```kotlin
// 明示的に型を指定した例
fun main() {
    // 整数型
    val intValue : Int = 123456789 // 数値リテラル（整数）は何も付けなければInt型になる
    val longValue : Long = 1234567890123L // 数値の末尾にLを付けるとLong型になる

    // 浮動小数点型
    val floatValue : Float = 3.14f // 数値の末尾にfを付けるとfloat型になる
    val doubleValue : Double = 3.1415926535 // 小数点を含む数値は何もつけなければDouble型になる

    // 文字列型
    val stringValue : String = "Hello Kotlin" // ダブルクォートで囲んだ文字列はString

    // 論理型
    val booleanValue : Boolean = true // trueまたはfalseを取る論理型

    // データを出力
    println("intValue: $intValue")
    println("longValue: $longValue")
    println("floatValue: $floatValue")
    println("doubleValue: $doubleValue")
    println("stringValue: $stringValue")
    println("booleanValue: $booleanValue")
}
```

## 変数宣言と型(方推論)について理解を高める

### Cap02-03.kt

```kotlin
// 明示的に型を指定しない例(方推論を使う)
fun main() {
    // 整数型(型指定なし)
    val intValue = 123456789 // Intとして推論される
    val longValue = 1234567890123L // Longとして推論される

    // 浮動小数点型
    val floatValue = 3.14f // Floatとして推論される
    val doubleValue = 3.1415926535 // Doubleとして推論される

    // 文字列型
    val stringValue = "Hello Kotlin" // Stringとして推論される

    // 論理型
    val booleanValue = true // Booleanとして推論される

    // データを出力
    println("intValue: $intValue")
    println("longValue: $longValue")
    println("floatValue: $floatValue")
    println("doubleValue: $doubleValue")
    println("stringValue: $stringValue")
    println("booleanValue: $booleanValue")
}

```

## 変数宣言の仕方について理解度を高める

### Cap03-01.kt

```kotlin
// valとvarの違い
fun main() {
    // 文字列変数「str1」をvalで宣言し、初期値「abc」を設定する
    val str1 = "abc"
    // str1の値を出力する
    println(str1)
    // str1の文字列の長さを出力する
    println(str1.length)
    // str1に「xyz」を代入しようとする(エラーになる)
    str1 = "xyz" // コンパイルエラーになることを確認したら、この行をコメントアウトする
    // 文字列変数「str2」をvalで宣言し、初期値「def」を設定する
    var str2 = "def"
    // str2に「xyz」を代入し、出力する
    str2 = "xyz"
    println(str2)

}
```

## 関数とラムダ式について理解度を高める

### Cap03-02.kt

```kotlin
fun main() {
   fun main() {
  // ❶ 引数も戻り値もない関数を定義して実行する
  fun lambda0() {
    println("lambda0")
  }
  lambda0()

  // ❷ ❶と同じ処理をラムダ式で表現する（型を明示したラムダ）
  val lambda1: () -> Unit = {
    println("lambda1")
  }
  lambda1()

  // ❸ ❶❷と同じ処理をラムダ式で表現する（型推論）
  val lambda2 = {
    println("lambda2")
  }
  lambda2()

  // ❹ 引数（文字列）を持つ関数を定義し、"○○さん、こんにちは" と表示する
  fun greet0(name: String) {
    println(name + " さん、こんにちは")
  }
  greet0("みな")

  // ❺ ❹をラムダ式（型推論）で書き換える
  val greet1 = { name: String ->
    println("$name さん、こんにちは")
  }
  greet1("みな")

  // ❻ 割り算をして結果を返す関数を定義する
  fun divide(arg1: Int, arg2: Int): Int {
    return arg1 / arg2
  }

  // ❼ divideを呼び出す
  println(divide(10, 2))

  // ❽ divideを名前付き引数で呼び出し、引数の順序を入れ替える
  println(divide(arg2 = 2, arg1 = 10))
}

```

## 高階関数について理解度を高める

### Cap03-03.kt

```kotlin
fun main() {
    // ① 引数としてラムダ式を受け取る関数を定義(高階関数の基本形)
    fun func01 (param: () -> Unit) {
        param()
    }

    // ② 名前付き引数を使って呼び出す
    func01 (param = {println("② 名前付き引数として呼び出す")})

    // ③ 名前付き引数を使わずに呼び出す(通常の位置引数形)
    func01 ({println("③ 名前付き引数を使わずに呼び出す")})

    // ④ トレーリングラムダ式(最後の引数がラムダ式なら●カッコの外に書ける)
    func01 () {println("④ トレーリングラムダ式(Composableでよく使う)")}

    // ⑤ 引数がラムダ1つだけの場合は()も省略できる
    func01 {println("⑤ トレーリングラムダ式 + ()省略形")}

    // ⑥ 通常の引数とラムダを受け取る関数を定義(高階関数の応用)
    fun func02 (param1: String, param2: (arg: String) -> Unit) {
        param2(param1)
    }

    // ⑦ 引数付きラムダのトレーリング形式(ComposableのTextFieldなどでよくある形)
    func02 ("トレーリングラムダ") { arg ->
        println("⑦ 引数付きラムダ式： $arg")
    }
}
```

## 論理演算子の理解度を高める
### Cap04-01.kt

```kotlin
fun main() {
  var a = 3 // あとで値を変えるためにvarで宣言
  val b = 3
  val c = 3
  val and1 = (a == b) && (b == c)
  val or1 = (a == b) || (b == c)
  println("a変更前 and = ${and1}")
  println("a変更前 or  = ${or1}")

  a = 2 // varで宣言した変数aの値を変更する

  val and2 = (a == b) && (b == c)
  val or2 = (a == b) || (b == c)
  println("a変更後 and = ${and2}")
  println("a変更後 or  = ${or2}")
}

```

## if式の理解度を高める
### Cap04-02.kt

```kotlin
fun main() {
  val number1 = 4
  // ifは式なので、条件に応じた値を返せます
  val message1 = if (number1 % 2 == 0) "偶数" else "奇数"
  println("number1は${message1}")

  val number2 = 7
  val message2 = if (number2 % 2 == 0) "偶数" else "奇数"
  println("number2は${message2}")
}

```

## Listの理解度を高める1
### Cap04-03.kt

```kotlin
fun main() {
  // listOfでリストを作成。インデックスは0から始まる
  val gengou = listOf("昭和", "平成", "令和")
  println("0番目の要素は${gengou[0]}")
  println("2番目の要素は${gengou[2]}")
}

```

## Listの理解度を高める2
### Cap04-04.kt

```kotlin
fun main() {
  val items = mutableListOf("A", "B", "C")
  println("出力1回目：${items}")
  items.add("D")
  println("出力2回目：${items}")
  items.removeAt(1)
  println("出力3回目：${items}")
}

```

## try-finallyの復習
### Cap05-01.kt


```kotlin
fun main() {
  var flag = false // 最初はfalse

  fun sample1() {
    try {
      flag = true
      println("処理中...")
      return // ここで関数を抜ける
    } finally {
      flag = false
      println("後片付け処理を実行") // 必ず実行される
    }
  }

  sample1()
  println("処理後のflag = $flag") // falseに戻っている
}

```

## null許容型とletの理解度を高める
### Cap05-02.kt

```kotlin
fun main() {
  val a: Int? = 5
  val b: Int? = null

  // これはコンパイルエラーになる
  //val c = a * b
  println("開始")

  // letやifでnullチェックをする
  a?.let {
    println("aは${it * 2}")
  }

  b?.let {
    println("bは${it * 2}") // bの値はnullなのでこの行は実行されない
  }

  println("終了")
}

```

## リストとforループの復習1
### Cap05-03.kt

```kotlin
fun main() {
  // listOfで数値のリストを作る（不変リスト）
  val numbers = listOf(1, 2, 3, 4, 5, 6)

  println("開始")
  // for文でリストの要素を順に取り出す
  for (n in numbers) {
    // もしnが2で割り切れるなら偶数
    if (n % 2 == 0) {
      println("偶数: $n")
    }
  }
  println("終了")
}

```

## リストとforループの復習2
### Cap05-04.kt

```kotlin
fun main() {
  val fruits = listOf("林檎", "梨", "柿")

  println("開始 forEach")

  // forEachで要素を順に取り出す
  fruits.forEach { fruit ->
    println("フルーツ: $fruit")
  }

  println("開始 forEachIndexed")

  // forEachIndexedで要素をインデックス付きで順に取り出す
  fruits.forEachIndexed { index, fruit ->
    println("フルーツ$index: $fruit")
  }

  println("終了")
}

```

## リストとmapの理解度を高める
### Cap05-05.kt

```kotlin
fun main() {
  val numbers = listOf(1, 2, 3)

  println("開始")

  // mapで各要素を2倍にした新しいリストを作る
  val numbers2 = numbers.map { it * 2 }

  println("元のリスト: $numbers")
  println("mapで処理したリスト: $numbers2")

  println("終了")
}

```

## enum classについて理解度を高める
### Cap06-01.kt

```kotlin
// 一般的なenum classの使い方
enum class TrafficSignal { // 信号機
  RED,    // 赤
  YELLOW, // 黄
  BLUE    // 青
}

// プロパティ(message)を持つenum class
enum class TrafficSignalMsg(val message: String) {
  RED("止まれ"),
  YELLOW("注意して進め"),
  BLUE("進め")
}

fun main() {
  // 値を表示する（通常のenum）
  val signal1 = TrafficSignal.RED
  println(signal1.name)  // → "RED"
  val signal2 = TrafficSignal.YELLOW
  println(signal2)       // → "YELLOW"（nameと同じ）

  println("---")

  // 値を表示する（属性付きenum）
  val signal11 = TrafficSignalMsg.RED
  println(signal11.message) // → "止まれ"
  val signal12 = TrafficSignalMsg.YELLOW
  println(signal12)         // → "？？？”（.message）を付けていない
  val signal13 = TrafficSignalMsg.BLUE
  println(signal13.message) // → "？？？"
}

```

## when式について理解度を高める

### Cap06-02.kt

```kotlin
enum class TrafficSignal2 { // 信号機
  RED,    // 赤
  YELLOW, // 黄
  BLUE    // 青
}

fun main() {
  // if文で分岐した例
  val signal1 = TrafficSignal2.YELLOW
  if (signal1 == TrafficSignal2.RED) {
    println("$signal1 は止まれ")
  } else if (signal1 == TrafficSignal2.YELLOW) {
    println("$signal1 は止まれ")
  } else if (signal1 == TrafficSignal2.BLUE) {
    println("$signal1 は進んでも良い")
  }

  val signal2 = TrafficSignal2.RED
  when (signal2) {
    TrafficSignal2.RED, TrafficSignal2.YELLOW -> {
      println("$signal2 は止まれ")
    }
    TrafficSignal2.BLUE -> {
      println("$signal2 は進んでも良い")
    }
  }
}

```

## companion objectについて理解度を高める

### Cap07-01.kt

```kotlin
// コンパニオンオブジェクトの例
class Ticket1 {
  companion object {
    const val PREFIX = "TK-"
    fun code(id: Int): String = PREFIX + id
  }
}

// 一般的な例
class Ticket2 {
  val prefix = "TK-"
  fun code(id: Int): String = prefix + id
}

fun main() {
  // クラス名で直接呼び出し
  println("コンパニオンオブジェクト")
  println(Ticket1.code(123))

  // 一般的な例
  println("インスタンス")
  println(Ticket2().code(456))
}

```

## 可変長引数について理解度を高める

### Cap07-02.kt

```kotlin
// 可変長引数(vararg)の例
fun joinTitles(vararg titles: String): String =
  "[" + titles.joinToString(" / ")  + "]"

fun main() {
  // 文字列を渡す
  println(joinTitles("A", "B", "C")) // [A / B / C]

  // 引数なしで呼び出す
  println(joinTitles()) // []

  // 配列を渡す（スプレッド演算子 * を使用）
  val xy = arrayOf("X", "Y")
  println(joinTitles(*xy)) // [X / Y]
}

```

## 引数なしのwhenについて理解度を高める

### Cap07-03.kt

```kotlin
fun describe(a: Int, b: Int): String = when {
  a >= b -> "a greater or equal"
  a == b -> "equal"
  else -> "a less than"
}

fun main() {
  println(describe(a = 5, b = 3)) // a greater or equal ?
  println(describe(a = 3, b = 3)) // equal?
  println(describe(a = 2, b = 4)) // a less than
}
```