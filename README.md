# Python 编码风格


<h2 id="3">编码规范</h2>

<h3 id="3.1"> PEP8 规范</h3>

[PEP 8 链接](https://www.python.org/dev/peps/pep-0008/ "With a Title")

具体 参考 PEP 8 编码规范 这里不在重复

* 静态检查 工具。
1. Pylint
2. Flake8
3. pytest

pychar vscode 可安装以上插件，检查编写是否规范


<h3 id="3.2"> tab 和 space </h3>

一个缩进级别四个空格。禁用 tab 

Python 3 不允许 tab 和 space 混用，  

<h3 id="3.3">变量命名</h3>

参考 PEP 8 编码规范

不要使用 l， O， I， 作为单字符变量命名，在某些字体中，这些字母和数字 1 0 无法区分

变量和硬编码 要有注释，包括对其功能、取值范围、注意事项等的说明


<h3 id="3.6">行注释</h3>

分支语句（条件分支、循环语句等）必须编写注释 描述功能而不是描述代码 



<h2 id="4">代码抽象性</h2>

注意代码抽象，不要一个函数写完所以功能，

以冒泡排序为例，如何代码抽象与分程

示例
```Python

from random import randint

def main():
    # 随机生成 10 组大小各异的数组并排序
    for i in range(10):
        # step 1. get random array
        arr = get_random_array()
        
        # step 2. print original array
        print('原数组', end='：')
        print_array(arr)
        
        # step 3. bubble sort
        bubble_sort(arr)
        
        # step 4. print sorted array
        print('排序后', end='：')
        print_array(arr)
        
        print()
    
def get_random_array():
    ''' 得到随机大小的随机数组 '''
    size = randint(0, 10)
    arr = []
    for i in range(size):
        arr.append(randint(0, 100) - 50)
    return arr

def print_array(arr):
    for i in arr:
        print(i, end=' ')
    print()

def bubble_sort(arr):
    ''' 对指定数组进行冒泡排序（从小到大） '''
    for i in range(len(arr)):
        for j in range(len(arr) - i - 1):
            if arr[j] > arr [j+1]:
                temp = arr[j]
                arr[j] = arr[j+1]
                arr[j+1] = temp
    
if __name__ == '__main__':
    main()
```


<h2 id="5">函数注释<h2/>


<h3 id="5.1">函数头部应进行注释</h3>
列出：函数的目的/功能、输入参数、输出参数、返回值、调用关系（函数、表）等。 
示例：下面这段函数的注释比较标准，当然，并不局限于此格式，但上述信息建议要包含在内
```Python

Function: // 函数名称

Description: // 函数功能、性能等的描述

Calls: // 被本函数调用的函数清单

Called By: // 调用本函数的函数清单

Table Accessed: // 被访问的表（此项仅对于牵扯到数据库操作的程序）

Table Updated:  // 被修改的表（此项仅对于牵扯到数据库操作的程序）
Input: // 输入参数说明，包括每个参数的作

       // 用、取值说明及参数间关系。
Output: // 对输出参数的说明。

Return: // 函数返回值的说明

Others: // 其它说明

```


<h3 id="5.2">其他建议</h3>

在任何地方避免使用尾随空格。




