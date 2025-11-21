---
id: Cpp_Basics
aliases: []
tags:
  - Coding
---

# Library

## Basics

| Concept                      | Description                                                                 |
| :--------------------------- | :-------------------------------------------------------------------------- |
| Pointer Array vs. Array Pointer | `const char *pointer[]` is an array of pointers; `const char (*pointer)[]` is a pointer to an array. |
| Templates (`template <typename T>`) | A generic data type for **classes**, **functions**, or **type aliases**. |
| Prefix `(char) malloc(sizeof(uint8_t))`| Prefix is a mandatory cast operator |
| `.o` File | Middle File to be linked to generate final binary files |

## `std`

### 新的类型

|类 | 常用方法/用法 | 解释 |
| :--- | :--- | :--- |
| `std::vector<T>` | `push_back(val)`, `pop_back()`, `size()`, `empty()`, `begin()`, `end()`, `at(i)`, `[]` | 动态数组。调试时推荐使用 `at()` 进行边界检查，追求性能时使用 `[]`。 |
| `std::string` | `substr(pos, len)`, `find(str)`, `c_str()`, `length()`, `+`, `==` | 使用 `+` 进行拼接。`c_str()` 用于与 C 字符串 API 交互 |
| `std::map<K, V>` | `insert({k,v})`, `find(k)`, `erase(k)`, `[]`, `count(k)` | 键值对，按键排序。`[]` 很方便，但如果键不存在，会插入新元素。 |
| `std::unordered_map<K,V>`| `insert({k,v})`, `find(k)`, `erase(k)`, `[]`, `count(k)` | 基于哈希的 map，查找比 `std::map` 快，但无序。 |
| 智能指针 | `std::unique_ptr`, `std::shared_ptr`, `std::weak_ptr` | 自动化内存管理。默认优先使用 `std::unique_ptr`。使用 `std::make_shared` 和 `std::make_unique` 创建。 |

## Core Concepts

| 特性 | 描述 | 解释 |
| :--- | :--- | :--- |
| RAII | 资源获取即初始化 (Resource Acquisition Is Initialization) | 将资源生命周期与对象生命周期绑定。例如：`std::ifstream`, `std::lock_guard`。 |
| `const` 正确性 | `const T*`, `T* const`, `const T&`, `T my_func() const` | 尽可能使用 `const` 来防止意外修改，并使接口更清晰。 |
|
头文件保护 | `#pragma once` | 防止同一头文件被多次包含。`#pragma once` 更简单且被广泛支持。 |
| 迭代器 | `begin()`, `end()`, `cbegin()`, `cend()`, `rbegin()`, `rend()` | 用于遍历容器。使用 `auto` 来简化迭代器声明。C++11 基于范围的 for 循环是更好的选择。 |
|右值|临时的，不可寻址的，即将销毁的表达式|-|
|`&`| 定义时是引用(reference)符, 使用时是取地址操作|和指针一样高效, 不创建新的内存(编译器可能会创建指针来实现这一操作)|

# Experiences

- **Overclock** is important
