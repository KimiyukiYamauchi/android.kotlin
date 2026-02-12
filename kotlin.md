<!-- TOC -->

# 目次

- [第１章 Kotlin の基本](#第１章-kotlin-の基本)
  - [1.1 変数と定数](#11-変数と定数)
  - [1.2 データ型と Null 安全性](#12-データ型と-null-安全性)
  - [1.3 演算子とスマートキャスト](#13-演算子とスマートキャスト)
  - [1.4 制御構文](#14-制御構文)
  - [1.5 サンプルコード: 簡単な計算機アプリ](#15-サンプルコード-簡単な計算機アプリ)
- [第２章 関数とクラス](#第２章-関数とクラス)
  - [2.1 関数の定義と呼び出し](#21-関数の定義と呼び出し)
  - [2.2 クラスとオブジェクト](#22-クラスとオブジェクト)
  - [2.3 プロパティとゲッター・セッター](#23-プロパティとゲッターセッター)
  - [2.4 データクラスとオブジェクトの比較](#24-データクラスとオブジェクトの比較)
  - [2.5 サンプルコード: 動物シミュレーション](#25-サンプルコード-動物シミュレーション)
- [第３章 Kotlinの特徴的な機能](#第３章-kotlinの特徴的な機能)
  - [3.1 配列とリスト](#31-配列とリスト)
  - [3.2 セットとマップ](#32-セットとマップ)
  - [3.3 ラムダ式と高階関数](#33-ラムダ式と高階関数)
  - [3.4 コレクションの操作とスコープ関数](#34-コレクションの操作とスコープ関数)
  - [3.5 サンプルコード: タスク管理アプリケーション](#35-サンプルコード-タスク管理アプリケーション)
- [第４章 Null完全性と例外処理](#第４章-null完全性と例外処理)
  - [4.1 Null安全性とNullableタイプ](#41-null安全性とnullableタイプ)

<!-- /TOC -->

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

### 1.5 サンプルコード: 簡単な計算機アプリ

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

## 第２章 関数とクラス

### 2.1 関数の定義と呼び出し

#### 関数の定義

```kotlin
// 引数と戻り値を持つ関数
fun add(a: Int, b: Int): Int {
    return a + b
}

// 引数を持たず、戻り値もない関数
fun printHello() {
    println("Hello, World!")
}
```

#### 関数の呼び出し

```kotlin
val result = add(3, 5)
println(result) // 8

printHello() // "Hello, World!"
```

#### デフォルト引数

```kotlin
fun greet(name: String = "Guest") {
    println("Hello $name!")
}

greet("Alice") // "Hello, Alice!"
greet() // "Hello, Guest!"
```

#### 名前付き引数

```kotlin
fun introduce(name: String, age: Int) {
    println("My name is $name, and I am $age years old.")
}

introduce(age = 25, name = "Bob") // "My name is Bob, and I am 25 years old."
```

#### 拡張関数

```kotlin
fun String.reverse(): String {
  return this.reversed()
}

val str = "Hello, World!"
println(str.reverse()) // "!dlroW ,olleH"
```

### 2.2 クラスとオブジェクト

#### クラスの定義

```kotlin
class Person {
    var name: String = ""
    var age: Int = 0

    fun introduce() {
        println("My name is $name, and I am $age years old.")
    }
}
```

#### オブジェクトの作成

```kotlin
val person = Person()
person.name = "Alice"
person.age = 12
person.introduce() // "My name is Alice, and I am 12 years old."
```

#### プライマリコンストラクタ

```kotlin
class Person(var name: String, var age: Int) {
    fun introduce() {
        println("My name is $name, and I am $age years old.")
    }
}

fun main() {
    val person = Person("Bob", 30)
    person.introduce() // "My name is Bob, and I am 30 years old."
}
```

#### initブロック

```kotlin
class Person(var name: String, var age: Int) {
    init {
        println("Creating a new Person object with $name and age $age")
    }
    fun introduce() {
        println("My name is $name, and I am $age years old.")
    }
}

fun main() {
    val person = Person("Smith", 40) // "Creating a new Person object with Smith and age 40"
    person.introduce() // "My name is Smith, and I am 40 years old."
}
```

#### セカンダリコンストラクタ

```kotlin
class Person(var name: String, var age: Int) {
   constructor(name: String) : this(name, 0)

    fun introduce() {
        println("My name is $name, and I am $age years old.")
    }
}

fun main() {
    val person1 = Person("Smith", 40) // "Creating a new Person object with Smith and age 40"
    val person2 = Person("Taro")

    person1.introduce() // "My name is Smith, and I am 40 years old."
    person2.introduce() // "My name is Taro, and I am 0 years old."
}
```

### 2.3 プロパティとゲッター・セッター

#### プロパティの定義

```kotlin
class Person() {
   var name: String = ""
    val birthYear: Int = 1990
}
```

#### ゲッターとセッター

```kotlin
class Person() {
   var name: String = ""
       get() = field.uppercase()
       set(value) {
           field = value.trim()
       }
}

fun main() {
    val person = Person()
    person.name = "   Alice    "
    println(person.name) // "ALICE"
}
```

#### バッキングフィールド

```kotlin
class Person() {
   var age: Int = 0
       set(value) {
           field = if (value >= 0) value else 0
       }
}

fun main() {
    val person = Person()
    person.age = -5
    println(person.age) // 0
}
```

### 2.4 データクラスとオブジェクトの比較

#### データクラス

```kotlin
data class Person(val name: String, val age: Int)

fun main() {
    val person1 = Person("Alice", 29)
    val person2 = Person("Alice", 29)
    val person3 = Person("Bob", 30)

    println(person1 == person2) // true
    println(person1 == person3) // false
}
```

#### オブジェクトの比較

```kotlin
class Person(val name: String, val age: Int) {
    override fun equals(other: Any?): Boolean {
        if (other !is Person) return false
        return name == other.name && age == other.age
    }
}

fun main() {
    val person1 = Person("Alice", 29)
    val person2 = Person("Alice", 29)
    val person3 = Person("Bob", 30)

    println(person1 == person2) // true
    println(person1 === person2) // false
    println(person1 == person3) // false
}
```

#### copy()メソッド

```kotlin
class Person(val name: String, val age: Int) {
    override fun equals(other: Any?): Boolean {
        if (other !is Person) return false
        return name == other.name && age == other.age
    }
}

fun main() {
    val person1 = Person("Alice", 29)
    val person2 = Person("Alice", 29)
    val person3 = Person("Bob", 30)

    println(person1 == person2) // true
    println(person1 === person2) // false
    println(person1 == person3) // false
}
```

### 2.5 サンプルコード: 動物シミュレーション

```kotlin
open class Animal(val name: String, val age: Int) {
    open fun makeSound() {
        println("The animal makes a sound")
    }
}

class Dog(name: String, age: Int, var breed: String) : Animal(name, age) {
    override fun makeSound() {
        println("The dog barks")
    }

    override fun equals(other: Any?): Boolean {
        if (other !is Dog) return false
        return name == other.name && age == other.age && breed == other.breed
    }

    fun fetch() {
        println("The dog fetches a ball")
    }
}

class Cat(name: String, age: Int, color: String) : Animal(name, age) {
    override fun makeSound() {
        println("The cat meows")
    }

    fun sleep() {
        println("The cat Sleeps")
    }
}

data class Person(val name: String, val age: Int) {
    fun greet() {
        println("Hello, my name is $name and I am $age years old")
    }
}

fun main() {
    val dog = Dog("Gon", 3, "Labrador Retriever")
    val cat = Cat("Cyberd", 3, "Black")
    val person = Person("Alice", 35)

    dog.makeSound() // "The dog barks"
    dog.fetch() // "The dog fetches a ball"

    cat.makeSound() // "The cat meows"
    cat.sleep() // "The cat Sleeps"

    person.greet() // "Hello, my name is Alice and I am 35 years old"

    val dog2 = Dog("Gon", 3, "Labrador Retriever")
    val cat2 = Cat("Cyberd", 3, "Orange")

    println(dog == dog2) // true
    println(cat == cat2) // false

    val person2 = Person("Alice", 35)
    println(person == person2) // true
}
```

## 第３章 Kotlinの特徴的な機能

### 3.1 配列とリスト

#### 配列

```kotlin
fun main() {
    val numbers = arrayOf(1, 2, 3, 4, 5)
    println(numbers[0]) // 1
    println(numbers[2]) // 3

    numbers[3] = 10
    println(numbers[3]) // 10

    val size = numbers.size
    println(size) // 5
}
```

#### リスト

```kotlin
fun main() {
    val fruits = listOf("apple", "banana", "orange")
    println(fruits[1]) // "banana"

//    fruits[2] = "grape" // コンパイルエラー(読み取り専用リスト)

    val mutableFruits = mutableListOf("apple", "banana", "orange")
    mutableFruits[2] = "grape"
    mutableFruits.add("pineapple")
    println(mutableFruits) // [apple, banana, grape, pineapple]
}
```

#### リストの操作

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)

    val evenNumbers = numbers.filter { it % 2 == 0 }
    println(evenNumbers) // [2, 4]

    val squaredNums = numbers.map { it * it }
    println(squaredNums) // [1, 4, 9, 16, 25]

    val sum = numbers.reduce { acc, i -> acc + i }
    println(sum) // 15

    val firstEvenNumber = numbers.find { it % 2 == 0 }
    println(firstEvenNumber) // 2
}
```

#### arrayOf、listOf、mutableListOfの使い分け

| 目的                             | 使うもの          |
| -------------------------------- | ----------------- |
| 要素を **変更する必要がある**    | `arrayOf`（配列） |
| **読み取り専用**で安全に扱いたい | `listOf`          |
| 追加・削除・更新したい           | `mutableListOf`   |
| Java配列互換・高速・固定長       | `arrayOf`         |

- **基本は** listOf
- 変更が必要 → mutableListOf
- 配列は **特別な理由があるときだけ**
- Kotlinは「変更できない設計」を推奨する言語

### 3.2 セットとマップ

#### セット

```kotlin
fun main() {
    val fruits = setOf<String>("apple", "banana", "orange", "banana")
    println(fruits) // [apple, banana, orange]

    val numbers = mutableSetOf<Int>(1, 2, 3, 4, 5)
    numbers.add(6)
    numbers.add(3)
    println(numbers) // [1, 2, 3, 4, 5, 6]
}
```

#### マップ

```kotlin
fun main() {
    val fruits = setOf<String>("apple", "banana", "orange", "banana")
    println(fruits) // [apple, banana, orange]

    val numbers = mutableSetOf<Int>(1, 2, 3, 4, 5)
    numbers.add(6)
    numbers.add(3)
    println(numbers) // [1, 2, 3, 4, 5, 6]
}
```

#### セットとマップの操作

```kotlin
fun main() {
    val numbers = setOf(1, 2, 3, 4, 5)
    println(numbers.contains(3)) // true
    println(numbers.isEmpty()) // false
    println(numbers.size) // 5

    val ages = mapOf<String, Int>("Alice" to 25, "Bob" to 30, "Charlie" to 45)
    println(ages.containsKey("Alice")) // true
    println(ages.containsValue(45)) // trur
    println(ages.keys) // [Alice, Bob, Charlie]
    println(ages.values) // [25, 30, 45]
}
```

### 3.3 ラムダ式と高階関数

#### ラムダ式

```kotlin
fun main() {
    val sum = { x: Int, y: Int -> x + y }
    println(sum(1, 2)) // 3

    val square: (Int) -> Int = { x -> x * x }
    println(square(3)) // 9
}
```

#### 高階関数

```kotlin
fun main() {
    fun applyOptions(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
        return operation(x, y)
    }

    val result1 = applyOptions(10, 20, { x, y -> x + y })
    println(result1) // 30

    val result2 = applyOptions(10, 20, { x, y -> x * y })
    println(result2) // 200
}
```

#### スコープ関数

```kotlin
data class Person(var name: String, var age: Int, var address: String)

fun main() {
    val person = Person("Alice", 28, "").apply {
        address = "New York City"
        age++
    }

    println(person) // Person(name=Alice, age=29, address=New York City)
}

```

##### スコープ関数の特徴

- let: オブジェクトを"it"として参照、結果を返す
- run: オブジェクトを"this"として参照、結果を返す
- with: オブジェクトを"this"として参照、結果を返す(拡張関数ではない)
- apply: オブジェクトを"this"として参照、オブジェクト自体を返す
- also: オブジェクトを"it"として参照、オブジェクト自体を返す

### 3.4 コレクションの操作とスコープ関数

#### コレクションの操作関数

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)

    val evenNumbers = numbers.filter { it % 2 == 0 }
    println(evenNumbers) // [2, 4]

    val squaredNumbers = numbers.map { it * it }
    println(squaredNumbers) // [1, 4, 9, 16, 25]

    val sum = numbers.reduce{ acc, i -> acc + i}
    println(sum) // 15

    val firstEvenNumber = numbers.find { it % 2 == 0 }
    println(firstEvenNumber) // 2

    val sortedNumbers = numbers.sorted()
    println(sortedNumbers)  // [1, 2, 3, 4, 5]
}
```

#### スコープ関数とコレクションの操作

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)

    val result = numbers.filter { it % 2 == 0 }
        .map{it * it}
        .reduce{acc, i -> acc + i}
    println(result) // 20
}
```

```kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5)

    val result = numbers.let {
        it.filter { it % 2 == 0 }
            .map{it * it}
            .reduce { acc, i -> acc + i }
    }

    println(result) // 20
}
```

### 3.5 サンプルコード: タスク管理アプリケーション

```kotlin
data class Task(val name: String, var isCompleted: Boolean = false)

fun main() {
    val tasks = mutableListOf<Task>()

    fun addTask(name: String) {
        tasks.add(Task(name))
        println("Task added: $name")
    }

    fun completeTask(index: Int) {
        if (index in tasks.indices) {
            tasks[index].isCompleted = true
            println("Task completed: ${tasks[index].name}")
        } else {
            println("Invalid task index")
        }
    }

    fun printTasks() {
        if (tasks.isEmpty()) {
            println("No tasks found")
        } else {
            tasks.forEachIndexed { index, task ->
                val status = if (task.isCompleted) "completed" else "Pending"
                println("${index + 1}. ${task.name} - $status")
            }
        }
    }

    fun printCompletedTasks() {
        val completedTasks = tasks.filter { it.isCompleted }
        if (completedTasks.isEmpty()) {
            println("No completed tasks found")
        } else {
            println("Completed tasks")
            completedTasks.forEach { println("- ${it.name}") }
        }
    }

    fun countPendingTasks(): Int {
        return tasks.count { !it.isCompleted}
    }

    addTask("Buy groceries")
    addTask("Finish proect report")
    addTask("Check out")

    printTasks()
    // 1. Buy groceries - Pending
    // 2. Finish proect report - Pending
    // 3. Check out - Pending

    completeTask(1)
    // Task completed: Finish proect report

    printTasks()
    // 1. Buy groceries - Pending
    // 2. Finish proect report - completed
    // 3. Check out - Pending

    printCompletedTasks()
    // - Finish proect report

    val pendingTasksCount = countPendingTasks()
    println("Pending tasks count: $pendingTasksCount")
    // Pending tasks count: 2
}

```

## 第４章 Null完全性と例外処理

### 4.1 Null安全性とNullableタイプ

#### Nullableタイプ

```kotlin

```
