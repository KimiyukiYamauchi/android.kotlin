## 第１章 Kotlin の基本

### 1.1 変数と定数

#### 変数の宣言

変数を使用するには、宣言が必要。変数の宣言には var キーワードを使用。

```kotlin
var age: Int = 25
var name: String = "Jone"
var height: Double = 175.5
```

変数の方を明示的に指定することもできるが、初期値から型を推論できるので、型の指定を省略することができる。

```kotlin
var count = 0 // Int型として推論される
var message = "Hello, World!" // String型として推論される
```

#### 定数の宣言

定数は、val キーワードを使用して宣言。定数は、一度値を割り当てると変更できない。

```kotlin
val PI: Double = 3.13159
val MAX_SIZE: Int = 100
```

### 1.2 データ型と Null 安全性

#### 基本的なデータ型

- 整数型: Byte, Short, Long
- 浮動小数点数型: Float, Double
- 文字型: Char
- 真偽値型: Boolean

Java のプリミティブ型に対応。すべてオブジェクトとして扱われる。

#### Null 安全性

デフォルトではすべての型が NonNullable。Null を代入可能にするには、型の末尾に?をつける。

```kotlin
val name: String = "John" // NonNullable
val nullableName: String? = null // Nullable
```

Nullable な変数を使用する際には、特別な表記を使用

```kotlin
val length = nullableName?.length // 安全呼び出し
val upperCaseName = nullableName?.toUpperCase() ?: "UNKNOWN" // エルビス演算子(?:)
val nonNullName = nullableName!! // 強制アンラップ(非推奨)
```

### 1.3 演算子とスマートキャスト

#### 算術演算子

Kotlin の算術演算子は、Java とほぼ同じ。

```kotlin
val a = 10
val b = 3
val sum = a + b // 13
val difference = a - b // 7
val product = a * b // 30
val quotient = a / b // 3
val remainder = a % b // 1
```

演算子をオーバーロードすることもできる。

#### 比較演算子

Kotlin の比較演算子は、Java とほぼ同じ。

```kotlin
val a = 5
val b = 3
val isEqual = a == b // false
val isNotEqual = a != b // true
val isGreater = a > b // true
```

==演算子は参照の比較ではなく、 **値** の比較。参照の比較は===演算子。

#### 論理演算子

Kotlin の比較演算子は、Java と同じ。

```kotlin
val x = true
val y = false
val and = x && y // false
val or = x || y // true
val not = !x // false
```

#### スマートキャスト

スマートキャストは、型チェックとその後の自動的な型変換を組み合わせた機能。

```kotlin
fun printLength(obj: Any) {
  if (obj is String) { // 型チェック
    print(obj.length)  // objは自動的にString型として扱われる(スマートキャスト)
  }
}
```

### 1.4 制御構文

#### if 式

if 式の結果を変数に代入することができる。

```kotlin
val a = 5
val b = 3
val max = if (a > b) a else b
println(max)  // max = 5

val message = if (a > b) {
  "aはbより大きい"
} else {
  "aはbより小さいか等しい"
}
print(message)  // message = "aはbより大きい"
```

#### when 式

Java の switch 文より柔軟な条件分岐が可能。

```kotlin
val x = 2
when (x) {
  1 -> println("xは1")
  2 -> println("xは2")
  else -> {
    println("xは1でも2でもない")
  }
}

val y = 10
when {
  y < 0 -> println("yは負の数")
  y in 1..10 -> println("yは1以上10以下")
  else -> println("yは11以上")
}
```

#### for 文

Java の拡張 for 文に相当。

```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
for (number in numbers) {
  println(number)
}

for (i in 1..5) {
  println(i)
}

for (i in 5 downTo 1) {
  println(i)
}

for (i in 1..10 step 2) {
  println(i)
}
```

#### while 文とdo-while文

Javaとほぼ同じ。

```kotlin
var i = 0
while (i < 5) {
  println(i)
  i++
}

var j = 0
do {
  println(j)
  j++
} while (j < 5)
```

#### ラベル付きbreak・continue

```kotlin
// breakの例
outerLoop@ for (i in 1..3) {
  innerLoop@ for (j in 1..3) {
    if (i == 2 && j == 2) {
      break@outerLoop
    }
    println("break例 - i: $i, j: $j")
  }
}

// continueの例
outerLoop@ for (i in 1..3) {
  innerLoop@ for (j in 1..3) {
    if (i == 2 && j == 2) {
      continue@outerLoop
    }
    println("continue例 - i: $i, j: $j")
  }
}
```

#### サンプルコード: 簡単な計算機アプリ

```kotlin

// CalculatorApp.kt

private fun printMenu() {
    println("1. 足し算")
    println("2. 引き算")
    println("3. 掛け算")
    println("4. 割り算")
    println("5. 終了")
}

private fun readInt(prompt: String): Int? {
    print(prompt)
    return readLine()?.trim()?.toIntOrNull()
}

private fun calculate(choice: Int, num1: Int, num2: Int): Int? {
    return when (choice) {
        1 -> num1 + num2
        2 -> num1 - num2
        3 -> num1 * num2
        4 -> {
            if (num2 == 0) null else num1 / num2
        }
        else -> null
    }
}

fun main() {
    println("簡単な計算機アプリへようこそ！")

    while (true) {
        printMenu()
        val choice = readInt("実行したい操作の番号を入力してください: ")

        if (choice == null || choice !in 1..5) {
            println("無効な選択肢です。1から5までの数字を入力してください")
            continue
        }

        if (choice == 5) {
            println("アプリを終了します。")
            break
        }

        val num1 = readInt("1つ目の数字を入力してください: ")
        if (num1 == null) {
            println("無効な入力です。数字を入力してください。")
            continue
        }

        val num2 = readInt("2つ目の数字を入力してください: ")
        if (num2 == null) {
            println("無効な入力です。数字を入力してください。")
            continue
        }

        val result = calculate(choice, num1, num2)
        if (result == null) {
            println("0で割ることはできません。")
            continue
        }

        println("結果: $result")
        println()
    }
}
```
