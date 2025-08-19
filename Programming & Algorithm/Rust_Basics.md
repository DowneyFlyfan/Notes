---
id: Rust_Basics
aliases: []
tags: []
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
|`loop`|`loop`是**expression**, 可以通过`break`返回值|
|`while`|`while`是**statement**, 可以通过break终止循环，但不能返回值|
|越界|会引发panic, 终止编译|
|切片|可以使用`copy` trait 进行复制|
|if条件表达式|必须显示转化为Bool值|
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
|`.clone()`|必须**显示**调用，在**Heap**上进行，成本高|
|HashMap|没有`copy` trait的变量, 使用其他变量作为key或value时会直接将所有权拿过来|

# Struct \& Enum

| Concept  | Description                                |
| :------- | :----------------------------------------- |
| `Struct`定义 | 字段名和变量名相同 ...|
| `Struct`便捷定义||
|`Tuple Struct`|就是有名字的元组, `struct (u32, i32, f64)`|
|Associated Function|不包含`&self`参数的`impl`|
| `Enum` | enum 中的每一个选项都是一个`variant`|
|`match`匹配工具|`other`和`_`|
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


| Concept  | Description                                |
| :------- | :----------------------------------------- |

# Vector, String

| Concept          | Description                                                                 |
| :--------------- | :-------------------------------------------------------------------------- |
| `Vector.get()`   | 返回`Option<T>`,遇到不存在的索引就返回`None`,而不是报错                     |
| `String`字符迭代 | `String`不定长，所以使用`char()`方法将其拆成单个字，`byte()`方法将其拆成字节 |
| `vec!`宏         | 可以更快捷地创建动态数组                                                    |
|`format!`宏||

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
|`?` 运算符|拥有控制流能力, `Err`时会立即终止函数，并返回`Err(io_error.into())`,即转换为当前函数所返回的错误类型|
