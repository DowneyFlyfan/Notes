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

| Concept           | Description                                                                                                                              |
| :---------------- | :--------------------------------------------------------------------------------------------------------------------------------------- |
| `Struct`定义      | 字段名和变量名相同时，可以省略字段名（即字段初始化简写）。                                                                             |
| `Struct`更新语法  | 在末尾使用 `..` 语法，可以基于另一个结构体实例的值来创建新的结构体实例。                                                               |
| `Tuple Struct`    | 具名元组，例如 `struct Color(u8, u8, u8);`，使用 `.0`, `.1` 等数字索引访问其元素。                                                     |
| Associated Function | 不包含 `&self` 参数的 `impl` 块中的函数，与类型本身关联而非其实例。                                                                     |
| `Enum`            | 枚举类型，其中每一个选项都被称为一个 `variant`（变体）。                                                                               |
| `match`表达式     | 用于模式匹配。在末尾使用 `_` (通配符) 或一个变量名来匹配所有剩余模式；`_` 也可以用来忽略匹配到的值。                                      |
| `if let`表达式    | 是一种更简洁的模式匹配方式，用于处理只有一个匹配模式的情况，可以替代冗余的 `match`。                                                     |
| 单元结构体        | 例如 `struct example;`，不包含任何字段，不占用内存（零大小类型）。                                                                     |
| 匿名元组          | 没有命名字段的元组，例如 `(1, "hello", true)`，使用 `.0`, `.1` 等数字索引访问其元素。                                                  |
| `Option<T>`       | 一个泛型枚举，表示一个值可能存在 (`Some(T)`) 或不存在 (`None`)。                                                                       |
| `Result<T, E>`    | 一个泛型枚举，表示一个操作可能成功 (`Ok(T)`) 并返回一个值，或失败 (`Err(E)`) 并返回一个错误。                                            |
| `unwrap()`方法    | 用于获取 `Option` 或 `Result` 中的值。如果 `Option` 是 `None` 或 `Result` 是 `Err`，则会引发 `panic` 导致程序崩溃。                  |
| `expect()`方法    | 类似于 `unwrap()`，但允许提供一个自定义的错误消息，当发生 `panic` 时显示该消息，有助于调试。                                            |

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
| `vec!`宏         | 编译时确定长度，不使用`push`,更快创建`Vec`, `vec![]`可以表示空向量|
|`Collection`|可以在`Heap`上存储的数据类型|
|`format!`宏|将输入在编译时解析成`String`类型|
|特性|并没有`std::fmt::display`特性|

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
|`where`约束|规定了**trait bounds**, 使用`+`连接其必须具备的属性|
|结构体的特性和方法|只有**关联函数可以在不实例化时就可以使用**；**方法和特性都必须在实例化后使用**|

- 数据类型和生命周期**只在定义时确定，使用时不需要显式指定**。

# Closures, Iterators

| Concept          | Description                                                                 |
| :--------------- | :-------------------------------------------------------------------------- |
|`Closure`| 可以捕获其定义时所在环境的变量的**匿名函数**, 可使用`move`前缀强制获取某变量的所有权|
|`Closure`参数和返回值类型|一般可以不指定，让编译器自动推断；但是**闭包第一次使用后，类型就被确定不能更改**|
|列表的`sort_by_key`方法|使用闭包`|param| 排序变量`进行排序(默认从小到大)|
|`Closure` trait之`FnOnce`|只能`call`一次的闭包，比如把主函数中的某个变量`push`到一个`Vec`里，其Ownership就交给了`Vec`, 第二次`Call`主函数的该变量就失效了|
|不同的`iterator`|`.iter()`, `.into_iter()`, `mut_iter()`|
|**consuming adpater**|`.sum()`等使用`next()`方法的方法被称作**consuming adpater**, 因为他们会用尽`iterator`中的元素|
|**iterator adpater**|和**ietrator**一样都是**lazy**的，因此后面必须接`collect`方法把处理后的新**iterator**收集起来|
|`map`, `filter` 方法|都接受迭代器元素作为参数，返回一个参数(`map`)或`Booll`值(`filter`)|

# Smart Pointers

## Pointers

| Concept | Description |
| :--------------- | :-------------------------------------------------------------------------- |
| `Box<T>`类型 | 负责在**栈**上创建指针，在**堆**上分配内存。提供单层间接引用。 |
| 递归类型`Cons` | `Cons(头部， 尾部(一般使用Box<T>))`, 可以无限大小的递归类型, 拥有**数据所有权**。`Box<T>`使得递归类型在编译时有确定的大小。 |
| Deref Coercion |对于**所有智能指针**，当他们作为**函数参数**或者**方法调用**时，会**自动解引用** |
| `drop`方法 | 不可以主动`call`。当变量离开作用域时，Rust会自动调用`drop`方法进行资源清理。 |
| `std::mem::drop`方法 | 可以主动`call`，用于在变量离开作用域之前显式地释放其持有的资源。 |
| `Rc<T>`, (Reference-Counted)类型 | 通过创建对同一数据的多个不可变引用，实现**共享所有权**。`Rc::strong_count()`记录引用计数。当引用计数为0时，数据才会被清理。**只支持单线程**。`Rc::clone`只会在栈上复制|
| `RefCell<T>`类型 | 通过**interior mutability**，允许对不可变引用中的数据进行修改(主要是在`&self`方法中修改结构体字段)。使用`borrow()`借用不可变变量，`borrow_mut()`借用可变变量。 **只支持单线程**。|
| static dispatch | 在编译时确定调用的具体方法。通常通过在结构体字段中使用泛型和`trait bound` (`field: T where T: Trait`) 来实现。 |
| dynamic dispatch | 在运行时确定调用的具体方法。通常通过**胖指针** `Box<dyn Trait>` 来实现，胖指针包含数据指针和虚函数表指针。 |

## Circular References

| Concept | Description |
| :------ | :-------------------------------------------------------------------------- |
| 循环引用 | 使用`Rc<T>`时，如果存在循环引用（例如A引用B，B引用A），会导致引用计数永远不会降到0，从而造成**内存泄漏**。 |
| `Weak<T>`指针 | `Weak<T>`是一种弱引用，它不增加`Rc<T>`的强引用计数，且**没有对数据的所有权**。当所有强引用都消失时，`Weak<T>`指向的数据会被释放。`Weak<T>`可以通过`upgrade()`方法尝试获取一个`Option<Rc<T>>`。(**因此不能自动解引用**) |

- 树的结构定义

```rs
struct Node {
    value: usize,
    parent: RefCell<Weak<Node>>,
    children: RefCell<Vec<Rc<Node>>>,
}

```

# Concurrency

| 概念               | 描述                                                                                                   |
| :----------------- | :----------------------------------------------------------------------------------------------------- |
| 线程并发常见问题   | 数据竞争（Data Races）、死锁（Deadlocks，线程互相等待对方完成）。                                      |
| 主线程与子线程关系 | 当主线程终止时，所有子线程也会随之关闭。                                                               |
| 线程输出顺序       | 线程的执行和输出顺序由操作系统调度，不确定。                                                           |
| `recv` 与 `try_recv` | `recv` 方法会阻塞当前线程直到接收到消息；`try_recv` 方法会尝试立即接收消息，如果无消息则返回错误，不会阻塞线程。 |
| `mpsc::channel`    | `mpsc::channel()` 是 Rust 中最常用的多生产者单消费者（multi-producer, single-consumer）线程间通信方式。其中 `tx.send(val)` 会将 `val` 的所有权转移给接收端。 |
| `Mutex<T>`         | `Mutex<T>`（互斥锁）允许多个线程共享一个值，但确保在任何给定时间只有一个线程能访问该值。通过调用 `.lock().unwrap()` 方法获取 `MutexGuard<T>` 智能指针（一个可变引用），从而实现独占访问。 |
| `Send` trait       | `Send` trait 标记的类型可以在线程间安全地**转移所有权**。几乎所有基本类型都实现了 `Send`。             |
| `Sync` trait       | `Sync` trait 标记的类型可以在线程间安全地**共享引用**（即通过 `&` 引用在多线程间访问）。如果 `T` 是 `Sync`，那么 `&T` 可以安全地在线程间发送。 |
