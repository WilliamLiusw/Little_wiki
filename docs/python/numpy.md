# 数组相关用法

这一页面是对于python中的数组（包括numpy.array和list）的一些用法进行总结


## 矩阵乘法

### np.dot()
    C = np.dot(AB)
对于二维矩阵，计算真正意义上的矩阵乘积，同线性代数中矩阵乘法的定义。对于一维矩阵，计算两者的内积。

### * 和np.multiply()
    C = A * B
    C = np.multiply(A,B)
实现的是对应元素相乘

## 矩阵的大小
### numpy.array类型
支持 len, size, shape等用法
对于矩阵 A (3, 4)

    len(A) = 3
    A.size = 12
    A.shape = (3,4)
    
需要注意的是，对于一维数组，size更加符合要求
### list类型
只有len一种用法

## 数组元素的修改

    // 增加元素
    A.append(element)
    A.insert(index,element)
    
    // 删除元素
    A.pop()
    A.pop(index)

## 数组拼接
### append()
numpy提供了numpy.append(arr, values, axis=None)函数。对于参数规定，要么一个数组和一个数值；要么两个数组，不能三个及以上数组直接append拼接。append函数返回的始终是一个一维数组。

    >>> b=np.array([11,22,33])
    >>> b
    array([11, 22, 33])
    >>> np.append(a,b)
    array([ 0,  1,  2,  3,  4, 11, 22, 33])
    >>> a
    array([[1, 2, 3],
           [4, 5, 6]])
    >>> b=np.array([[7,8,9],[10,11,12]])
    >>> b
    array([[ 7,  8,  9],
           [10, 11, 12]])
    >>> np.append(a,b)
    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12])
### extend()
先将array转化为list，然后使用

    a_list.extend(b_list)
进行转化，这个方法只适用于一位数组
### concatenate()
numpy提供了numpy.concatenate((a1,a2,...), axis=0)函数。能够一次完成多个数组的拼接。其中a1,a2,...是数组类型的参数

    >>> a=np.array([1,2,3])
    >>> b=np.array([11,22,33])
    >>> c=np.array([44,55,66])
    >>> np.concatenate((a,b,c),axis=0)  # 默认情况下，axis=0可以不写
    array([ 1,  2,  3, 11, 22, 33, 44, 55, 66]) #对于一维数组拼接，axis的值不影响最后的结果

     

    >>> a=np.array([[1,2,3],[4,5,6]])
    >>> b=np.array([[11,21,31],[7,8,9]])
    >>> np.concatenate((a,b),axis=0)
    array([[ 1,  2,  3],
           [ 4,  5,  6],
           [11, 21, 31],
           [ 7,  8,  9]])

    >>> np.concatenate((a,b),axis=1)  #axis=1表示对应行的数组进行拼接
    array([[ 1,  2,  3, 11, 21, 31],
           [ 4,  5,  6,  7,  8,  9]])
这个方法效率更高，更加适合多维数组拼接

## 最大值查找
### list类型

    max_num = max(list) #  找到最大值
    index = list.index(max(list)) # 找到最大值的索引
### array类型

    np.max(a) # 全局最大
    np.max(a,axis=0) # 每列最大
    np.max(a,axis=1) # 每行最大

    np.where(a==np.max(a)) #获取最大值索引
用where得到最大值的索引，返回值中，前面的array对应行数，后者对应列数
>\>>> print(np.where(a==np.max(a)))                            <br>
>(array([2], dtype=int64), array([2], dtype=int64))          <br>
>\>>> print(np.where(a==np.max(a,axis=0)))               <br>
>(array([2, 2, 2], dtype=int64), array([0, 1, 2], dtype=int64))  

如果array中有相同的最大值，where会将其位置全部给出
