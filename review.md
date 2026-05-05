<!-- TOC -->

# 目次

- [文字列の結合について理解度を高める](#文字列の結合について理解度を高める)
  - [Cap02-01.kt](#cap02-01kt)
- [変数宣言と型について理解度を高める](#変数宣言と型について理解度を高める)
  - [Cap02-02.kt](#cap02-02kt)
- [変数宣言と型(方推論)について理解を高める](#変数宣言と型方推論について理解を高める)
  - [Cap02-03.kt](#cap02-03kt)

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
