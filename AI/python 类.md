# python 类
1.  self 是 **实例本身的引用**， 可以通过 self 对属性进行操作  
      
    
2.  特殊方法 (均可重写)

*   `__init__`: 构造函数，在创建对象时自动调用，用于初始化对象的状态。
*   `__len__`: 在调用 `len()` 函数时自动调用，用于返回对象的长度。
*   `__getitem__`: 在对象通过索引访问时自动调用，比如 `obj[idx]`。
*   `__str__`: 在调用 `str()` 函数或使用 `print()` 输出对象时自动调用，用于返回对象的字符串表示。
*   __call__: 创建实例后传入参数  
      
     3. 类的属性  
    
*   **用self定义实例属性**  
    
*   在类外部动态添加**实例属性**  
    
*   class MyClass:  
        def __init__(self):  
            self.instance_attr = 0  
      
    instance = MyClass()  
    instance.dynamic_attr = 200  # 动态添加实例属性  
    print(instance.dynamic_attr)  # 200  
      
    
*    **类属性** (所有实例共享该属性)  
    class MyClass:  
        class_attr = 42  # 类属性  
      
    print(MyClass.class_attr)  # 42  
    instance = MyClass()  
    print(instance.class_attr)  # 42
