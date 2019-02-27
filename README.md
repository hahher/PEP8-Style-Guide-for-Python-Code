# Python 编码风格


<h2 id="3">pe</h2>

<h3 id="3.1">PEP 8 规范</h3>
the [PEP 8 链接](https://www.python.org/dev/peps/pep-0008/ "With a Title")
参考 PEP 8 编码规范 这么不在重复


一个缩进级别四个空格。

* 连续行使用两种方式使封装元素成为一行：括号内垂直隐式连接 & 悬挂式缩进。 使用悬挂式缩进应该注意第一行不应该有参数，连续行要使用进一步的缩进来区分。

```Python

是：

# 括号内隐式连接，垂直对齐
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# 悬挂缩进，进一步缩进区分其他语句
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# 悬挂缩进，一般是四个空格，但非必须
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)

否：

# 括号内隐式连接，没有垂直对齐时，第一行的参数被禁止
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# 悬挂缩进，需要进一步的缩进区分其他行
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

* 当 if 语句过长时，可选的处理方式，但不限于此：

```python
# 不使用额外缩进
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# 增加注释区分，支持语法高亮
if (this_is_one_thing and
    that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()
    
# 条件连续行额外缩进
if (this_is_one_thing
        and that_is_another_thing):
    do_something()
```

* 当闭环括号内元素跨行时，可以采用以下方式。

```Python
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
```
或者
```python
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

<h3 id="3.2"> tab 和 space </h3>



Python 3 不允许 tab 和 space 混用，同时混用了 tab 和 space 的 Python 2 代码应该被转换为仅使用 space。  

<h3 id="3.3">代码行最大长度</h3>

将所有行限制为最多79个字符。


反斜杠有时可能仍然要用。 例如，又多又长的 with - 语句不能使用隐式连接，这时反斜杠是可以接受的：

```Python
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())
```

assert 语句也是如此。

<h3 id="3.4">在二元运算符之前还是之后断行?</h3>

推荐使用以下形式：

```Python
# 是： easy to match operators with operands
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```  

只要保持本地一致性，在二元运算符之前和之后断开都是允许的，但是新的 Python 代码推荐使用 Knuth 形式。  

<h3 id="3.5">空行</h3>

顶层函数和类定义间使用两个空行。

类内方法定义间使用一个空行。

不同函数组之间使用两个空行隔离。

总之，空行的作用就是隔离不同函数类等，使层次分明。


<h3 id="3.6">模块导入</h3>

```Python
是：
    from subprocess import Popen, PIPE
    import os
    import sys

否：
    import sys, os
```

模块导入总是位于文件顶部，在模块注释和文档字符串之后，模块全局变量和常量之前。

导入应该按照以下顺序分组，不同组间用空行隔离。

* 标准库 imports  
* 相关第三方 imports  
* 本地特定应用／库 imports  

推荐使用绝对导入，标准库代码应总是使用绝对导入。

```Python
import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example
```


<h2 id="4">字符串引号</h2>

在 Python 中，单引号和双引号是等价的，只需要坚持使用一种并保持一致即可。

在双引号中使用单引号，单引号中使用双引号。三引号中使用双引号。

<h2 id="5">表达式和语句中的空格<h2/>

<h3 id="5.1">在以下场景避免不必要的空格</h3>

推荐示例

```Python
是： spam(ham[1], {eggs: 2})
否： spam( ham[ 1 ], { eggs: 2 } )

是： foo = (0,)
否： bar = (0, )

是： if x == 4: print x, y; x, y = y, x
否： if x == 4 : print x , y ; x , y = y , x

是：
    ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
    ham[lower:upper], ham[lower:upper:], ham[lower::step]
    ham[lower+offset : upper+offset]
    ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
    ham[lower + offset : upper + offset]

否：
    ham[lower + offset:upper + offset]
    ham[1: 9], ham[1 :9], ham[1:9 :3]
    ham[lower : : upper]
    ham[ : upper]
    
是： spam(1)
否： spam (1)

是： dct['key'] = lst[index]
否： dct ['key'] = lst [index]

是：
    x = 1
    y = 2
    long_variable = 3
    
否：
    x             = 1
    y             = 2
    long_variable = 3
    
```

<h3 id="5.2">其他建议</h3>

在任何地方避免使用尾随空格。

在二元运算符周围使用空格：

```python
是：

    i = i + 1
    submitted += 1
    x = x*2 - 1
    hypot2 = x*x + y*y
    c = (a+b) * (a-b)
    
否：

    i=i+1
    submitted +=1
    x = x * 2 - 1
    hypot2 = x * x + y * y
    c = (a + b) * (a - b)
```
表示关键字参数或默认参数值时，不要使用空格：

```python
是：

    def complex(real, imag=0.0):
        return magic(r=real, i=imag)
否：

    def complex(real, imag = 0.0):
        return magic(r = real, i = imag)
```
函数注解的示例：

```python
是：

    def munge(input: AnyStr): ...
    def munge() -> AnyStr: ...

否：

    def munge(input:AnyStr): ...
    def munge()->PosInt: ...
```

当参数注释和默认值共存时：

```python
是：

    def munge(sep: AnyStr = None): ...
    def munge(input: AnyStr, sep: AnyStr = None, limit=1000): ...

否：

    def munge(input: AnyStr=None): ...
    def munge(input: AnyStr, limit = 1000): ...
```

同行多语句不建议使用：

```python
是：

    if foo == 'blah':
        do_blah_thing()
    do_one()
    do_two()
    do_three()

Rather not:

    if foo == 'blah': do_blah_thing()
    do_one(); do_two(); do_three()
```



<h2 id="6">何时使用逗号结尾</h2>

单元素元组强制使用逗号：

```python
是：

    FILES = ('setup.cfg',)

OK, but confusing:

    FILES = 'setup.cfg',
```


<h2 id="7">注释</h2>

糟糕的注释不如没有注释

<h3 id="7.1">块注释</h3>

同等级别的一块代码的注释，块注释内每行注释以 \# 开头，内部注释段落之间使用以 \# 开头的空行注释隔开。

<h3 id="7.2">行注释</h3>

行注释和代码声明间至少间隔两个空格，不要使用无聊的行注释，例如：

```python 
Don't do this:

x = x + 1                 # Increment x

But sometimes, this is useful:

x = x + 1                 # Compensate for border
```

<h3 id="7.3">文档字符串</h3>

为所有公共模块，函数，类和方法编写文档字符串。 对于非公共方法，文本字符串不是必需的，但应该有一个描述该方法的注释。例如：  
```python
"""Return a foobang

Optional plotz says to frobnicate the bizbaz first.
"""

"""only one single docstring line"""
```
<blockquote>
注意当注释为多行时，最终的 """ 单独起一行。
</blockquote>

<h2 id="8">命名约定</h2>

<h3 id="8.1">圣经戒律</h3>

对用户可见的公共 API 部分的命名应该遵从反应如何使用而不是怎么实现。

<h3 id="8.2">描述性: 命名风格</h3>

以下命名风格通常区分彼此使用：

* b (单个小写字母)

* B (单个大写字母)

* lowercase（小写）

* lower\_case\_with_underscores（带下划线的小写）

* UPPERCASE（大写）

* UPPER\_CASE\_WITH\_UNDERSCORES（带下划线的大写）

* CapitalizedWords（驼峰式，蒙古包式 whatever.）

<blockquote>Note: 使用驼峰式时，缩写全部大写，例如：HTTPServerError 好于 HttpServerError </blockquote>

* mixedCase (乌鬼头)

* Capitalized_Words_With_Underscores (丑！不解释！)

* \_single\_leading\_underscore : 弱地 "内部使用" 指示器. 例如，from M import * 不会导入下划线开头的对象

* single\_trailing\_underscore\_ : 用来避免和 python 关键字冲突，例如：
```python
Tkinter.Toplevel(master, class_='ClassName')
```


<h3 id="8.3">规定性: 命名习惯</h3>

<h4 id="8.3.1">避免的命名</h4>

一定不要使用 l， O， I， 作为单字符变量命名，在某些字体中，这些字母和数字 1 0 无法区分。

<h4 id="8.3.2">包和模块名</h4>

模块应该使用简短并且全小写的命名，下划线也可以使用以提升可读性。

Python 包也应该使用简短的全小写名称，尽管不鼓励使用下划线。

当 C/C++ 编写的扩展模块伴随一个提供更高级别接口的 python 模块时，C/C++ 模块命名应该以下划线开头(例如，\_socket)。

<h4 id="8.3.3">类名</h4>

类名通常使用驼峰式命名习惯。

在类的接口有文档说明，并且主要用于 callable 的情况下，类都是 callable 的，call 一个类将返回一个新的类实例，例如 instance = Class()。如果类实现了 \_\_call\_\_() 函数，那么类实例也将是 callable 的，类的命名也可以使用函数命名习惯。

对于 builtin 函数的命名习惯，可以通过 <code>dir(\_\_builtins\_\_)</code> 查看系统函数命名样例。注意区分普通命名，异常名命名和 builtin 常量。

<h4 id="8.3.4">类型变量名</h4>

相对于短名称如：T，AnyStr，Num，类型变量使用驼峰式命名习惯较好。另外建议在变量名前添加 \_co 或 \_contra 前缀响应的声明 covariant 或 contravariant 行为。例如：

```python
from typing import TypeVar

VT_co = TypeVar('VT_co', covariant=True)
KT_contra = TypeVar('KT_contra', contravariant=True)
```

<h4 id="8.3.5">异常名</h4>

异常应该是类，所以可以使用类命名习惯，但是，如果异常是个错误类，一般加上 "Error" 后缀。

<h4 id="8.3.6">全局变量名</h4>

我们假设这些全局变量只在一个模块内使用，这样的话和函数的命名习惯是一样的。

设计为通过 <code>from M import *</code> 导入的类应该使用 \_\_all\_\_ 机制避免导出全局变量，或者可以使用老式的习惯，给这些全局变量名加上下划线作为前缀(表示这是非公有变量)。


<h4 id="8.3.7">常量</h4>

常量一般定义在模块级别。命名风格如：MAX_OVERFLOW 或 TOTAL 。


<h3 id="9">编码建议</h3>

* 代码不应该以一种不利于其他 python 实现（PyPy, Jython, IronPython, Cython, Psyco 诸如此类）的方式编写。 例如：不要使用 a += b 或 a = a + b 来实现就地字符串连接，在库的性能敏感部分，应该使用 ''.join() 的形式，这就能保证在不同的 python 实现中，连接动作可以在线性时间内完成。

* 和例如 None 这类 singleton 的比较，应该使用 is 或 is not 而不是 ==。另外，小心使用 <code>if x</code> 如果你的本意是 <code>if x is not None</code>，如果 x 是个布尔变量值 false，那可就完蛋了。

* 尽管功能相同，从可读性上考虑：

```python
是：

    if foo is not None:

否：

    if not foo is None:
```

* 使用 def 语句而不要使用赋值语句去直接绑定一个 lambda 表达式到标识符上：

```python
是：

    def f(x): return 2*x

否：

    f = lambda x: 2*x
```

赋值语句的使用消除了 lambda 表达式相对于显式 def 语句的唯一好处，那就是它能够嵌入到一个更大的表达式里面。

* 捕获的异常要说明 "错误出在哪里了 ？" 而不是仅仅说明 "哎呀！出问题了！"。


* 对于所有的 try/except 子句，将 try 子句限制为必需的绝对最小代码量避免隐藏 bug：

```python
是：

    try:
        value = collection[key]
    except KeyError:
        return key_not_found(key)
    else:
        return handle_value(value)

否：

    try:
        # Too broad!
        return handle_value(collection[key])
    except KeyError:
        # Will also catch KeyError raised by handle_value()
        return key_not_found(key)
```

* 特定代码块的本地资源使用 with 语句确保使用后立即释放，不能自动释放的使用 try/finally 也可以。

* 除了申请和释放资源，任何时候都应该使用单独的函数和方法调用 Context managers，例如：

```python
是：

    with conn.begin_transaction():
        do_stuff_in_transaction(conn)

否：

    with conn:
        do_stuff_in_transaction(conn) 
```

* 函数返回语句要一致。在一个函数内的所有返回语句要么都返回一个表达式，要么都不返回。如果任何一个返回语句返回了表达式，那么其他任何没有返回值的语句应该明确声明为 return None。在函数结束部分必须出现返回语句：
```python
是：

    def foo(x):
        if x >= 0:
            return math.sqrt(x)
        else:
            return None
    
    def bar(x):
        if x < 0:
            return None
        return math.sqrt(x)

否：

    def foo(x):
        if x >= 0:
            return math.sqrt(x)
    
    def bar(x):
        if x < 0:
            return
        return math.sqrt(x)
```



* 对于序列（字符串，列表，元组）的判空操作：
```python
是：
    if not seq:
    if seq:

否：
    if len(seq):
    if not len(seq):
```

* 不要使用尾随空格。

* 不要使用 == 验证布尔值为 Ture 或 False：

```python
是：
      if greeting:
否：
      if greeting == True:
      
      if greeting is True:
```


