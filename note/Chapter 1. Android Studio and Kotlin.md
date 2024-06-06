## Chapter 1. Android Studio and Kotlin

### 1. 什么是Android Studio和Kotlin

Android Studio是由google支持的android官方集成开发环境（IDE），而Kotlin是google推荐的用于开发android应用的编程语言，兼容java。

#### 1.1 Kotlin样式指南

* 函数名称应采用驼峰式大小写形式，并且应该是动词或者动词短语
* **左花括号应出现在函数开始行的末尾**
* 左花括号前应有一个空格

* 函数主体应缩进4个空格
* 右花括号位于函数主体中的末行代码之后，单独占一行，右花括号应与函数开头的**fun**关键字对齐。

> 详细代码样式规范可参考：https://developer.android.com/kotlin/style-guide?hl=zh-cn

#### 1.2 hello world

```kotlin
fun main() {
    println("hello world!")
}
```

#### 1.3 Kotlin变量定义

##### 1.3.1 数据类型

| **Kotlin 数据类型** | **可包含的数据类型**                                         | **字面量值示例**                       |
| ------------------- | ------------------------------------------------------------ | -------------------------------------- |
| `String`            | 文本                                                         | `"Add contact"` `"Search"` `"Sign in"` |
| `Int`               | 整数                                                         | `32` `1293490` `-59281`                |
| `Double`            | 小数                                                         | `2.0` `501.0292` `-31723.99999`        |
| `Float`             | 小数（不如 `Double` 精确），数字末尾带有 `f` 或 `F`。        | `5.0f` `-1630.209f` `1.2940278F`       |
| `Boolean`           | `true` 或 `false`。当只有两个可能的值时，可使用此数据类型。请注意，`true` 和 `false` 是 Kotlin 中的关键字。 | `true` `false`                         |

##### 1.3.2 变量定义

```kotlin
fun main() {
    val count: Int = 2
    println("You have $count unread messages.")
}
```

* val: 定义新变量的关键字
* count：变量名称，应遵循驼峰式大小写惯例
* Int：变量类型，在变量名称后，需依次添加**冒号、空格和变量的数据类型**。
* $count：字符串模板，其包含模板表达式，会将求得的值替换到字符串中

##### 1.3.3 类型推断

当为变量**提供了初始值**，就可以在变量声明中省略数据类型，Kotlin编译器会查看初始值的数据类型，并假定变量存储该类型的数据。

```kotlin
val count : Int = 2	// 方法1
val count = 2		// 方法2 类型推断
```

基本运算：

```kotlin
fun main() {
    val unreadCount = 5
    val readCount = 100
    println("You have ${unreadCount + readCount} total messages in your inbox.")
}
```

关于字符串模板，我们了解到，可以在单个变量名称前加上 `$` 符号。但是，如果您使用更复杂的表达式，就必须用大括号将该表达式括起来，并在大括号前添加 `$` 符号：`${unreadCount + readCount}`。

##### 1.3.4 更新变量

```kotlin
fun main() {
    var cartTotal = 0
    cartTotal = 20
    println("Total: $cartTotal")
    cartTotal++
    cartTotal--
}
```

如果需要更新变量的值，请使用 Kotlin 关键字 `var`（而不是 `val`）声明该变量。

- `val` 关键字 - 预计变量值不会变化时使用。
- `var` 关键字 - 预计变量值会发生变化时使用。
- 变量名称和增量/减量运算符之间不应有空格。

##### 1.3.5 字符串

可以使用 + 号将两个字符串加在一起（这种做法称为“串联”）

```kotlin
fun main() {
    val nextMeeting = "Next meeting is: "
    val date = "January 1"
    val reminder = nextMeeting + date + " at work"
    println(reminder)
}
```

#### 1.4 编码规范

- 变量名称应采用驼峰式大小写形式，并以小写字母开头。
- 在变量声明中指定数据类型时，应在冒号后面添加一个空格。

#### 1.5 添加注释

方法一：

在一行代码的中间位置插入注释。

```kotlin
height = 1 // Assume the height is 1 to start with.
```

方法二：

如果要添加超过100字符的长注释来详细说明代码，可使用多行注释：使用由正斜杠 (`/`) 和星号 (`*`) 组成的 `/*` 来作为多行注释的开头，在注释的每个新行开头添加一个星号，最后使用由星号和正斜杠符号组成的 `*/` 作为结尾。

```kotlin
/*
 * This is a very long comment that can
 * take up multiple lines.
 */
```

#### 1.6 函数

**添加返回值**

定义函数时，可以指定希望其返回的值的数据类型。如需指定返回值类型，只需在圆括号后面添加冒号 (`:`)，然后在冒号后面添加一个空格和类型名称（`Int`、`String` 等）。然后，在返回值类型与左大括号之间添加一个空格。在函数主体中，可以在所有语句之后使用 return 语句指定希望函数返回的值。

```kotlin
fun name(): return type {
	body
	return statement
}
```

* 默认情况下，如果没有指定返回类型，默认返回值类型为`Uint`，`Uint`表示函数并不会返回值，类似于c++中的`void`

返回字符串：

```kotlin
fun birthdayGreeting(): String {
    val nameGreeting = "Happy Birthday, Rover!"
    val ageGreeting = "You are now 5 years old!"
    return "$nameGreeting\n$ageGreeting"
}
```

==不知道这里怎么区分按值传递还是按引用传递。==

**添加形参**

行参会指定变量的名称和数据类型，形参在函数名称后面的圆括号内进行声明，每个行参均由变量名称和数据类型组成，以冒号和空格分隔，多个行参以**英文逗号**分隔。

```kotlin
fun birthdayGreeting(name: String): String {
    val nameGreeting = "Happy Birthday, $name!"
    val ageGreeting = "You are now 5 years old!"
    return "$nameGreeting\n$ageGreeting"
}
```

```kotlin
fun main() {
    println(birthdayGreeting("Rover", 5))
    println(birthdayGreeting(name = "Rex", age = 2))	// 具名实参
}
```

> 形参是可供函数访问的变量（例如 `name` 变量），而实参是传递的实际值。

注意：==在Kotlin中行参是不可变的，不能在函数主体中重新分配行参的值。==

#### 1.7 函数签名

函数名称及其输入（行参）通称为“函数签名”，函数签名包含返回值类型前面的所有内容（不包含返回值类型），如下所示：

```kotlin
fun birthdayGreeting(name: String, age: Int)
```

行参有时也成为行参列表

#### 1.8 实参

**具名实参**

如果我们在调用函数时添加了行参名称，该名称就称为具名实参。

```kotlin
println(birthdayGreeting(name = "Rex", age = 2))
```

**默认实参**

函数行参还可以指定默认实参

```kotlin
fun birthdayGreeting(name: String = "Rover", age: Int): String {
    return "Happy Birthday, $name! You are now $age years old!"
}
```

```kotlin
// 由于age行参是在name后面定义，这里必须使用具名实参
println(birthdayGreeting(age = 5))
println(birthdayGreeting("Rex", 2))
```

