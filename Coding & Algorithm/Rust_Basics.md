---
id: Rust_Basics
aliases: []
tags:
  - Coding
---

# Common Features

| Concept       | Description                                                                 |
| :------------ | :-------------------------------------------------------------------------- |
| `mut`         | 表示可变长度                                                              |
| `const`       | 表示常数, 在编译时确定(不可以来自函数调用或let变量), **必须指定类型**                                                            |
| `let`         | 结果在运行时确定，**可推断类型** |
| 元组和数组    | **长度都不可变**                                                            |
| `println!`    | 是一个宏                                                                    |
| `scalar`      | 单位长度的类型                                                              |
| `compound`    | 比较长的类型                                                                |
|`loop`|`loop`是**expression**, 可以通过`break`和`return`返回值, 否则无限循环|
|`iterator`|`iterator`循环长度是有限的|
|`while`|`while`是**statement**, 可以通过break终止循环，但不能返回值|
|越界|会引发panic, 终止编译|
|切片|可以使用`copy` trait 进行复制或直接进行指针引用|
|if条件表达式|必须**显示转化为`Bool`值**|
|statement|不返回值, 是一种命令, `()`**表示没有返回值**|
|expression|返回值|
| `super::` |调用父级条目|

# Ownership

| Concept           | Description                                                                                             |
| :---------------- | :------------------------------------------------------------------------------------------------------ |
| `Heap` vs `Stack` | `Heap`需要**Memory Controller**分配内存, `Stack`直接从栈顶上出入; 因此尽可能多地使用`Stack`是Rust的使命, 在函数执行结束后栈帧会一次性弹出 |
| Variable Scope    | 最后一次使用某变量后，该变量就会离开`scope`                                                              |
| `drop` function   | 任何离开`scope`的变量都会立刻被`drop`函数清理                                                           |
| `as_bytes()`      | `as_bytes()`方法可以把`String`转换成`array`                                                             |
| Mutable/Immutable References | **任何时候都只能有一个mut引用或者多个imuttable引用**                                                  |
|`.copy()`|**bit-to-bit** 复制，在**Stack**上进行，成本低，在`scalar`变量赋值时**隐式**调用|
|`.clone()`|必须**显式**调用，在**Heap**上进行，成本高|
|HashMap|没有`copy` trait的变量, 使用其他变量作为key或value时会直接将所有权拿过来|

# Struct, Enum

| Concept  | Description                                |
| :------- | :----------------------------------------- |
| `Struct`定义 | 字段名和变量名相同时，可以省略字段名|
| `Struct`便捷定义| 在末尾使用 `..` 语法，可以基于另一个结构体实例的值来创建新的结构体实例|
|`Tuple Struct`|就是有名字的元组, `struct (u32, i32, f64)`, 使用`.0`, `.1`...访问其元素|
|Associated Function|不包含`&self`参数的`impl`|
| `Enum` | enum 中的每一个选项都是一个`variant`|
|`match`匹配工具|在末尾使用`other`或其他自定义字符串表示**匹配剩下的所有pattern**, 使用`_`可以不接受变量|
|`if let`|代替繁琐的`match`, 在符合match的为唯一情况下进行赋值|
|单元结构体| `struct example;` 不占任何内存的结构体|
|元组|没有字段|

- `Result<T, E>`和`Option<T>`都是Generic Enum

```rs
enum Option<T> {
    Some(T),
    None,
}

enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

# Vector, String

| Concept          | Description                                                                 |
| :--------------- | :-------------------------------------------------------------------------- |
| `Vector.get()`   | 返回`Option<T>`,遇到不存在的索引就返回`None`; 比直接索引`Vec`类型更方便|
| `String`字符迭代 | `String`不定长，所以使用`char()`方法将其拆成单个字，`byte()`方法将其拆成字节|
| `vec!`宏         | 编译时确定长度，不使用`push`,更快创建`Vec` |
|`Collection`|可以在`Heap`上存储的数据类型|
|`format!`宏|将输入在编译时解析成`String`类型|

- `s1`的所有权被`add`函数夺取，`add`结束`s1`就失效,  `add`接受`&str`作为参数, 所以使用`&s2`, 输出会被`coerce`成`String`类型

```rs
let s1 = String::from("Hello, ");
let s2 = String::from("World!");
let s3 = s1 + &s2;

fn add(self, s: &str) -> String{...}
```

# Error Handling

| Concept          | Description                                                                 |
| :--------------- | :-------------------------------------------------------------------------- |
|`Result<T(ok), E(Err)>`| 使用`unwrap`方法解包可以获得其值，若结果为`Err`, 则程序立刻`panic`|
|`.expect()`|与`unwrap`相同， 多一个**在`()`中加上报错信息**的功能|
|`?` 运算符|放在返回`Result`类型的函数后，`Err`时会立即终止函数，并返回`Err(io_error.into())`,即转换为当前函数所返回的错误类型|

# Generic Types, Trait, Lifetime

| Concept          | Description                                                                 |
| :--------------- | :-------------------------------------------------------------------------- |
|`PartialOrd` trait bound|表示该类型必须实现部分元素可比较, 是`Ord`的超集|
|`Ord`|表示该类型必须实现所有元素可比较|
|`Turbofish`语法|在编译器无法推断`Generic Type`的情况下主动告诉编译器当前类型`::<>`|
|`Debug`|此种特性加载`#derive[Debug]`中可以实现debug特性，**包括输出**, `enum`等类型在非`debug`模式下是没有`Display`特性的|
|`impl`|后面接`<>`表示为Generic Type实现方法、特性; 不接`<>`表示为具体类型实现方法、特性|
|`{}`, `{:?}`和`{#?}`|`{}`实现`std::fmt::Display`, `{:?}`实现`std::fmt::debug`, `{#?}`用更美观的形式实现`debug`trait|

# Closures, Iterators

| Concept          | Description                                                                 |
| :--------------- | :-------------------------------------------------------------------------- |
|`Closure`参数和返回值类型|一般可以不指定，让编译器自动推断；但是**闭包第一次使用后，类型就被确定不能更改**|
|列表的`sort_by_key`方法|使用闭包`|param| 排序变量`进行排序(默认从小到大)|
|`Closure` trait之`FnOnce`|只能`call`一次的闭包，比如把主函数中的某个变量`push`到一个`Vec`里，其Ownership就交给了`Vec`, 第二次`Call`主函数的该变量就失效了|
|不同的`iterator`|`.iter()`, `.into_iter()`, `mut_iter()`|
|**consuming adpater**|`.sum()`等使用`next()`方法的方法被称作**consuming adpater**, 因为他们会用尽`iterator`中的元素|
|**iterator adpater**|和**ietrator**一样都是**lazy**的，因此后面必须接`collect`方法把处理后的新**iterator**收集起来|
|`map`, `filter` 方法|都接受迭代器元素作为参数，返回一个参数(`map`)或`Booll`值(`filter`)|

# Smart Pointers


