# 参数 arguments #
在这个文件里，我们主要介绍python中函数相关的知识。这一部分在学习的时候也存在forward reference，要结合`Basic.md`中的`kwarg和arg`内容进行参考。

> 术语：`调用`函数、 `接收`参数

## 位置参数 Positional Argument

经过前面的描述，我们已经有了基本的意识。在函数定义中，带有=号并且设定了默认值的参数，我们称之为`关键字参数（keyword argument，缩写为【kwarg】）`。另外的那些叫做`位置参数（positional argument，缩写为【arg】）`，位置参数arg在接收参数时候所处的位置很关键。而位置参数（postinoal argument/arg），又引申出来了2个概念：
    
- `可选位置参数`：
    这里举了2个函数来说明【可选位置参数】。
    >pow(x,y[,z])

    这个z就是可选位置参数

    > exec(oject[,globals[,locals]])
    
    这个函数内部，object是不可或缺的参数，调用时必须提供；可以有第二个参数，第二个参数会被接收为`globals`；在第二个参数存在的前提下，第三个参数会被接收为`locals`。

    so，对于可选位置参数：它不一定存在。它存在的时候，接收参数也要注意别整错它的位置。
- `可接收“很多值”的位置参数`：
    
    如果再看`print()函数`：
    > print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
    
    这个函数有4个kwarg，然后位置参数是`*objects`，objects还是个复数形式。这种带`1个*`的形式，就表述这个地方能够接收`很多值`，或者说，这个位置能够接收`1个列表或者1个元组`。这个`*objects`就被叫做`可以接收很多值的位置参数`！

    Thus，generally speaking，在一个函数里面，最多只有1个这种`能够接收很多值的位置参数`。如果两个这种*objects，肯定会混乱了。

    还有一种情况，有1个*objects这种“能够接收很多值的位置参数”，然后还有其他的位置参数arg，如果把他们都写在函数的参数中，Python也不知道哪个是那个。解决的方案就是，把`能够接收很多个值的位置参数`放在最后。就好比`max()`函数。

    >max(arg1, arg2, *args[, key])

    Return the `largest item in an iterable` or the `largest of two or more arguments`. 返回，可迭代对象中的最大项目，或者是2个以上位置参数中的最大项目。

    If one positional argument is provided, it should be an iterable. The largest item in the iterable is returned. If two or more positional arguments are provided, the largest of the positional arguments is returned. 如果只有一个位置参数，它应该是一个可迭代对象。可迭代对象中的最大item被返回。如果2个以上的位置参数被接收，返回所有位置参数中的最大项。

    There are two `optional keyword-only arguments`. The key argument specifies a one-argument ordering function like that used for `list.sort()`. The default argument specifies an object to return if the provided iterable is empty. If the iterable is empty and default is not provided, a ValueError is raised. 有2个`可选关键字参数`。关键字参数指明了一个类似于list.sort()中使用的one-argument排序函数。如果要接收的可迭代对象是空的，默认参数就指明了要返回的对象。如果可迭代对象是空的，默认参数也没有指明，那么`ValueError`就发生了。注：这里提到的就是key的相关信息。

    If multiple items are maximal, the function returns the first one encountered. This is consistent with other sort-stability preserving tools such as `sorted(iterable, key=keyfunc, reverse=True)[0]` and `heapq.nlargest(1, iterable, key=keyfunc)`.如果多个item都是最大项，那么函数返回第一个。这和sorted()、heapq.nlargest()等方法中提供的sort-stability 维持工具是一贯的。


    `New in version 3.4`: The default keyword-only argument.


    `Changed in version 3.8`: The key can be None.

    ```python
    # Sample dictionary
    ages = {
    'Matt': 30,
    'Katie': 29,
    'Nik': 31,
    'Jack': 43,
    'Alison': 32,
    'Kevin': 38
    }

    # Find the key with the maximum value
    max_key = max(ages, key=ages.get)
    print(max_key)
    ```
    这段代码执行的结果就是：
    > Jack
    
    此时，max()函数的位置参数是`ages`这个字典类型的可迭代对象。

# 第11章-第11节 关于参数（上）
每个函数可以看做一个完整的程序，程序的核心就是3个要素：
- 输入：从外部接收参数传递的值
- 处理：内部有能够完成某一特定任务的代码，尤其可以根据“输入”得到输出
- 输出：程序可以输出，向外部输送返回值

>这里要插一句，函数都是有返回值的。如果没有return语句，就会返回“None”，在Boolean运算中，None是作为False来处理的，以下代码：

```python
output_print = print('abc')
print("print()函数的返回值是：{}".format(output_print))
```
输出的结果是：
```
abc
print()函数的返回值是：None
```
