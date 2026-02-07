---
id: Cpp_Basics
aliases: []
tags:
  - Coding
sr-due: 2026-02-10
sr-interval: 4
sr-ease: 270
---

# Library

## Basics

| Concept                                 | Description                                                                                          |
| :-------------------------------------- | :--------------------------------------------------------------------------------------------------- |
| Pointer Array vs. Array Pointer         | `const char *pointer[]` is an array of pointers; `const char (*pointer)[]` is a pointer to an array. |
| Templates (`template <typename T>`)     | A generic data type for **classes**, **functions**, or **type aliases**.                             |
| Prefix `(char) malloc(sizeof(uint8_t))` | Prefix is a mandatory cast operator.                                                                 |
| `.o` File                               | Intermediate object file to be linked to generate the final binary executable.                       |
|                                         |                                                                                                      |

## std

### Common types

> `std::vector<T>` is a dynamic array typically implemented using three pointers: `start`, `finish` (points to the position after the last valid element), and `end_of_storage`.

| Container | Functions | Explanation |
| :--- | :--- | :--- |
| `std::string` | `substr(pos, len)`, `find(str)`, `c_str()`, `length()`, `+`, `==` | Use `+` for concatenation. `c_str()` provides compatibility with C-style string APIs. |
| `std::map<K, V>` | `insert({k,v})`, `find(k)`, `erase(k)`, `[]`, `count(k)` | Key-value pairs sorted by key. The `[]` operator is convenient but will insert a default element if the key is missing. |
| `std::unordered_map<K,V>` | `insert({k,v})`, `find(k)`, `erase(k)`, `[]`, `count(k)` | Hash-based map. Offers faster lookup than `std::map` but does not maintain order. |
| Smart Pointers | `std::unique_ptr`, `std::shared_ptr`, `std::weak_ptr` | Automated memory management. Prefer `std::unique_ptr` by default. Create using `std::make_shared` and `std::make_unique`. |

## Core Concepts

| Feature | Description | Explanation |
| :--- | :--- | :--- |
| RAII | Resource Acquisition Is Initialization | Binds resource lifecycle to object lifetime. Examples: `std::ifstream`, `std::lock_guard`. |
| `const` Correctness | `const T*`, `T* const`, `const T&`, `T my_func() const` | Use `const` whenever possible to prevent accidental modification and clarify interfaces. |
| Header Guard | `#pragma once` | Prevents a header file from being included multiple times. `#pragma once` is modern and widely supported. |
| Iterators | `begin()`, `end()`, `cbegin()`, `cend()`, `rbegin()`, `rend()` | Used for traversing containers. Use `auto` for declaration. C++11 range-based for loops are generally preferred. |
| R-value | Temporary, non-addressable expressions | Values that are about to be destroyed or are temporary. |
| `&` | Reference (definition) / Address-of (usage) | As efficient as pointers; does not create new memory (though compilers may use pointers internally). |

# Experiences

* **Overclock** is important.
