---
id: Rust_Basics
aliases: []
tags: []
---

# Common Features

- `mut`表示可变长度

- `const`表示常数不可更改
 
- `let`是赋值操作，若`let a = 6; let a = 3`; 则前面的`a`会被后面的`a` **shadowed**
 
- 元组和数组**长度都不可变**

- `println!`是一个宏

- 单位长度的类型叫做`scalar`, 比较长的类型叫做`compound`

# Ownership

- `Heap`需要**Memory Controller**分配内存, `Stack`直接从栈顶上出入; 因此尽可能多地使用`Stack`是Rust的使命

- 最后一次使用某变量后，该变量就会离开`scope`

- 任何离开`scope`的变量都会立刻被`drop`函数清理

- `as_bytes()`方法可以把`String`转换成`array`

- **任何时候都只能有一个mut引用或者多个imuttable引用**

# Enum

- 一个enum最终只能表示该enum中的某一个数据

# Vector, String

- `get`方法返回`Option<T>`,遇到不存在的索引就返回`None`,而不是报错

- `s1`的所有权被`add`函数夺取，`add`结束`s1`就失效,  `add`接受`&str`作为参数, 所以使用`&s2`, 输出会被`coerce`成`String`类型

```rs
let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2;

fn add(self, s: &str) -> String{...}
```

- `String`不定长，所以使用`char()`方法将其拆成单个字，`byte()`方法将其拆成字节

- `.copied()`是一种廉价拷贝; `.cloned()`更复杂，适合`Vec`等类型

- `vec!`宏可以更快捷地创建动态数组

# 
