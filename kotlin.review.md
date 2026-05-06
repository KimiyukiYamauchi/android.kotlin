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
    // ① 引数も戻り値もない関数を定義して実行する
    fun lambda0 () {
        println("lambda0")
    }
    lambda0()

    // ② ①と同じ処理をラムダ式で表現する(型を明示したラムダ)
    val lambda1: () -> Unit = {
        println("lambda1")
    }
    lambda1()

    // ③ ①②と同じ処理をラムダ式で表現する(型推論)
    val lambda2 = {
        println("lambda2")
    }
    lambda2()

    // ④ 引数(文字列)を持つ関数を定義し、"○○さん、こんにちは"と表示する
    fun greet0 (name: String) {
        println("name" + " さん、こんにちは")
    }
    greet0("みな")

    // ⑤ ④をラムダ式(型推論)で書き換える
    val greet1 = { name: String ->
        println("name" + " さん、こんにちは")
    }

    // ⑥ 割り算をして結果を返す関数を定義する
    fun divide (arg1: Int, arg2: Int): Int {
        return arg1 / arg2
    }

    // ⑦ divideを呼び出す
    println(divide(10, 2))

    // ⑧ divideを名前付き引数で呼び出し、引数の順序を入れ替える
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
