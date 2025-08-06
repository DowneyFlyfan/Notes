---
id: Python_Basics
aliases: []
tags: []
---

# python 迭代器的 特点、用法
*   **迭代器类** 的 方法  
    __iter__() 方法: 返回迭代器自身，方便继续迭代  
    __next__(): 返回下一个值  
      
    
*   特点:  
    无法用索引访问  
    使用后就会消失(不占用内存)

*   zip迭代器  
    

1.  作用: 将多个可迭代对象（如列表、元组等）中的元素打包成一个个对应的元组，然后返回由这些元组组成的迭代器
2.  特点: 当处理的可迭代**对象长度不同**时，它会按照最短的可迭代对象截断

*   enumerate(iterable, start = 0): 返回(index, 下一个iterable的值)  
      
    
*   range()  
      
    
*   map(): 对可迭代对象运用函数， 返回的是一个map对象，所以需要转换成可输出对象  
    numbers = \[1, 2, 3, 4]  
    squares = map(lambda x: x \*\* 2, numbers)  
    print(list(squares))  
      
    
*   reversed(): 反向迭代器  
    for i in reversed(\[1, 2, 3, 4]):  
        print(i)  
      
    
*   next(): 从迭代器中获取元素  
    iterable = iter(\[1,2,3,4])  
    print(next(iterable))  
    print(next(iterable))  
      
    
*   sorted(): 排序后返回元素的迭代器  
    iterable = \[3,4,2,1]  
    for idx in sorted(iterable):  
        print(idx)  
      
    
*   itertools.chain(): 将多个可迭代对象组合成一个迭代器  
    import itertools  
    for i in itertools.chain(\[1, 2], \['a', 'b']):  
        print(i) # 输出为 1 2 a b  
      
    
*   filter(): 过滤掉不满足第一个函数的参数, 返回的是一个filter对象，所以需要转换成可输出对象  
      
    numbers = \[None,2,3,4, 5]  
    x = filter(lambda x: x % 2 == 0, numbers)  
    print(list(x))

*   Experience

1.  重写一个类的时候，**不要重写属性**
2.  点乘会自动广播  
3.  常见的inplace操作**(可能导致不可导): 直接修改张量中的元素**

*   Tricks

# 元组 和 集合
1.  元组的创建  
    a = (1,)\*3  
    b = (3,)  
      
    
2.  元组组合  
    print(b + a)  
    \# Result: (3,1,1,1)  
      
    
3.  集合(元素唯一、无序)  
    my_set = set(\[1, 2, 3, 2, 1])  
    print(my_set)  # 输出：{1, 2, 3}


