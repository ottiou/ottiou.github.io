---
layout: post
title:  "python调用c的dll的示例"
date:   2019-05-25 20:33:08 +0800
categories: python
---
# python调用C的示例（ctypes）

## 环境
- C：Visual Studio 2019 vs_community__77941699.1558086422
- python: pyCharm

## 生成dll文件

- 文件->新建->项目->windos桌面向导->输入项目名称、地址等->创建->动态链接库(.dll)->空项目(E)->确定
- 在项目中添加新建项，选择从cpp文件(.cpp),文件名自己取如add_dll..cpp
- 在刚刚的文件中输入如下代码：
``` c
// 定义生成dll的函数
#define DLLEXPORT extern "C" __declspec(dllexport)
// dll库中的函数
DLLEXPORT int add(int a, int b) {
    return a + b;
}
```
- 生成->生成解决方案(注意记得选择解决方案平台与python一致，我的是64位x64，否则会出错)， 在对应的debug文件夹下面找到对应的add_dll.dll文件

## python调用dll文件
- 创建py文件,内容如下：
``` py
# 从ctypes导入CDLL来读取dll文件
from ctypes import CDLL
# 从对应路径下导入dll文件
dll = CDLL('.\\add_dll.dll')
# 使用dll的add_c函数
print(dll.add_c(1,5))
```
- 运行结果 6

## 直接python与ctypes调用c的速度对比
- 计算求和，分别是c循环，python得for循环，python内建函数sum：
```
ctypes cost 0.015625 second
python for-loop cost 0.078125 second
python sum cost 0.015625 second
```
