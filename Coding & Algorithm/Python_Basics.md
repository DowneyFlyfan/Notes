---
id: Python_Basics
aliases: []
tags:
  - Coding
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

# Torch

## Jit 即时编译

- jit.script, 即时编译的模块输入必须是确定的

- jit.compile解决了以上问题

## torchvision中常用的转换方法

1.  **注意**

- 以下转换不适用于Uint16类型数据  
    
- 只能用于PIL 或者 torchvision.Image  
      
    ****
2. **torchvision.transfroms 中的函数**  

```py
    from torchvision.transforms import (  
        **RandomResizedCrop,  
        RandomHorizontalFlip,  
        RandomGrayscale,  
        ColorJitter,  
        Compose,  
        RandomApply,  
        GaussianBlur,  
        ToTensor,  
        CenterCrop,  
        Resize,  
        Normalize,  
        Lambda,  
        RandomSolarize  
    )  
      
    # 将灰度图扩张成3通道图像  
    def expand_greyscale(t):  
        return t.expand(3, -1, -1)  
      
    transform1 = RandomResizedCrop(size = (1920,1080)) # 随机选定区域按照给定形状裁剪  
      
    transform2 = RandomHorizontalFlip(p = 0.5) # 按概率镜像  
    transform3 = RandomGrayscale(p = 0.5) # 按概率生成灰度图  
      
    transform4 = ColorJitter(brightness=0.2, contrast= 0.32, saturation=0.2, hue=0.2) # 亮度、对比度、饱和度、色调 (在 \[1-s, 1+s] 范围内随即调节)  
      
    transform5 = Compose(\[transform1, transform2, transform3]) # 按顺序执行这三个变换  
      
    transform6 = RandomApply(\[transform1, transform2], p = 0.6) # 根据概率选择是否使用这组变换  
      
    transform7 = GaussianBlur(kernel_size=5) # 高斯模糊  
      
    transform8 = ToTensor()  
      
    '''  
    对于 uint8 类型的图像数据（如 PIL 图像或 uint8 numpy 数组），将数据从 \[0, 255] 缩放到 \[0, 1]。
    
    将图像维度从 [H, W, C] 转换为 [C, H, W]。
    
    将图像数据转换为 torch.float32 的 PyTorch 张量.  
    '''
    
    transform9 = Resize(255) # 短边裁成255  
    transform10 = CenterCrop(224) # 从中心裁出224\*224的区域  
      
    transform11 = Normalize(\[0.4914, 0.4822, 0.4465], \[0.2023, 0.1994, 0.2010])]) # RGB通道的均值、方差  
      
    transform12 = Lambda(expand_greyscale) # Lambda 使用你自己定义的函数进行数据增强  
      
    transform13 = RandomSolarize(p = 0.5, threshold = 128) # 随机反转亮度 (高于128的 改成255 - x, 其他的不变)**
```

3. functional 

```py
import torchvision.transforms.functional  
    get_image_size(img: PIL.Image or Tensor) -> tuple # 返回H和W (不返回C)  
    five_crop(img: PIL.Image or Tensor, size: tuple or int) -> tuple # 返回5个size(2个元素的tuple)大小的元组  
    crop(img: PIL.Image or Tensor, top: int, left: int, height: int, width: int) -> PIL.Image or Tensor # 输出和输入类型相同  
```

