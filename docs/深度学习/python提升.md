## 注释规范
良好的代码风格是必须要养成的，其实从数据库大程就应该做起了
[Python类和方法注释规范](https://blog.csdn.net/lly1122334/article/details/80733908)，这这里我觉得[Google](https://www.sphinx-doc.org/en/master/usage/extensions/example_google.html)的规范还是不错的

[Python注释的特殊关键字/貌似所有语言都是](https://blog.csdn.net/weixin_31514087/article/details/113984760)
!!! note
    ```python
    def function_with_types_in_docstring(param1, param2):
    """Example function with types documented in the docstring.

    :pep:`484` type annotations are supported. If attribute, parameter, and
    return types are annotated according to `PEP 484`_, they do not need to be
    included in the docstring:

    Args:
        param1 (int): The first parameter.
        param2 (str): The second parameter.

    Returns:
        bool: The return value. True for success, False otherwise.
    """
    ```

## Class 相关
在Python中，函数定义后面跟着的->符号用于类型注解，指定了函数返回值的类型。这是Python 3的一个特性，使得代码更易于理解和维护，尽管它对代码的运行没有直接影响（即Python运行时不会强制类型检查）。

```python
def forward(self, input: Tensor) -> Tensor:
```
这表示forward方法接受一个名为input的参数，其类型为Tensor，并且这个方法的返回值也是一个Tensor类型的对象。这种类型注解主要用于提高代码的可读性和帮助开发工具提供更好的支持，比如类型检查、代码补全等。


### __call__方法
!!! example
    ```python
    class Adder:
        def __init__(self, value):
            self.value = value

        def __call__(self, x):
            return self.value + x

    # 创建一个Adder实例，初始化value为10
    adder = Adder(10)

    # 直接调用实例，这会触发__call__方法
    result = adder(5)  # 等同于 adder.__call__(5)

    print(result)  # 输出 15
    ```

## os 库相关
### os.path.join函数
!!! example
    ```python
    import os

    # 合并目录和文件名
    path = os.path.join("my_dir", "my_file.txt")
    print(path)

    # 在Windows上输出: my_dir\my_file.txt
    # 在Unix/Linux上输出: my_dir/my_file.txt
    ```
自动处理不同操作系统中的路径分隔符差异，避免了手动拼接路径字符串时可能出现的错误。

## struct 库相关
[struct实际用法教学](https://www.liaoxuefeng.com/wiki/1016959663602400/1017685387246080)，搭配[python字符格式Format Characters](https://docs.python.org/3/library/struct.html#format-characters)来使用struct对齐

## Numpy 库相关
### numpy.fromfile(file, dtype=None, count=-1, sep='', offset=0)
![](images/2024-07-02-20-55-14.png)
返回值为一个list

### numpy.array(list)
可以将`list`转化为一个numpy的矩阵，后面加上`reshape()`方法可以来实现维度的设置

### numpy.sum(a, axis=None, dtype=None, out=None, keepdims=False)
[numpy.sum()的使用](https://zhuanlan.zhihu.com/p/85790648),其中`axis`默认为None，此时表示矩阵所有的值加和`axis=0`表示列相加，`axis=1`表示行相加，`dtype`用来指定返回值的类型，`out`暂时先用不到，`keeydim`表示结果是否保持原来的维度。

### numpy.repeat(a, repeats, axis=None)   numpy.tile(a, reps)
[reference](https://blog.csdn.net/zyl1042635242/article/details/43052403)

简单来说，**repeat**的用法是为了让指定位置的指定元素重复几次，**tile**则是让一个矩阵重复几次，接在原来的矩阵的后面

### numpy.stack(arrays.axis) 沿着新轴连接数组的序列
参考[numpy.stack最通俗的理解](https://blog.csdn.net/qq_17550379/article/details/78934529)，举一个非常简单的例子
```python
>>> a = np.array([[1, 2, 3], [1, 2, 3], [1, 2, 3]])
>>> b = np.array([[4, 5, 6], [4, 5, 6], [4, 5, 6]])
>>> np.stack((a, b), axis=1)
array([[[1, 2, 3],
        [4, 5, 6]],

       [[1, 2, 3],
        [4, 5, 6]],

       [[1, 2, 3],
        [4, 5, 6]]])
```
axis=1指明了表示第二维度链接，运算顺序应该是先遍历a的第一个维度，a[0]=[1,2,3]，然后遍历b的第一个维度，b[0]=[4,5,6]，然后将这两个数组链接起来，所以结果就是[[1,2,3],[4,5,6]]，然后再遍历a的第二个维度，a[1]=[1,2,3]，然后遍历b的第二个维度，b[1]=[4,5,6]，然后将这两个数组链接起来，所以结果就是[[1,2,3],[4,5,6]]，然后再遍历a的第三个维度，a[2]=[1,2,3]，然后遍历b的第三个维度，b[2]=[4,5,6]，然后将这两个数组链接起来，所以结果就是[[1,2,3],[4,5,6]]，所以最后的结果就是[[[1,2,3],[4,5,6]],[[1,2,3],[4,5,6]],[[1,2,3],[4,5,6]]]

## numpy.transpose(a, axes=None) 
[numpy.transpose()的用法](https://blog.csdn.net/weixin_40522801/article/details/106172380)

## numpy.lib.stride_tricks.as_strided(x, shape=None, strides=None, subok=False, writeable=True)
[np.lib.stride_tricks.as_strided 详解](https://blog.csdn.net/weixin_46559271/article/details/105188300)

## numpy.stack(arrays, axis=0)
[numpy.stack最通俗的理解](https://blog.csdn.net/qq_17550379/article/details/78934529)

## 索引相关 None indices
[索引](https://www.numpy.org.cn/user/basics/indexing.html)

