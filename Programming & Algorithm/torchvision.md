---
id: torchvision
aliases: []
tags: []
---

# torchvision中常用的转换方法

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
