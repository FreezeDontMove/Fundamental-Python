# Python基础知识点

## 零零散散

* 乘方：**
* True False 首字母大写
* print后只能跟字符串，其他类型须转换成字符串
* 字符串切片list[a:b]中，b > a
  
---

## 字符串

* sorted()
  * 排序
  * sorted(iterable, key-None, reverse-False)
* upper()
  * 将字符串中小写字母转换成大写字母
  * str.upper()
* count()
  * 统计出现次数
  * str.count(sub, start= 0,end=len(string))
* index()
  * 找到索引
  * str.index(str, beg=0, end=len(string))

---

## 字典

* 字典.keys()和字典.values()返回的是视图
* 字典新增内容：字典[键] = 值
* 删除字典内容：del(字典[键])

---

## NumPy

* 导包

  * ```python
    import numpy as np
    ```

* np.array()
  * 一维数组
    * 生成的数组可以运算和比较（长度一致）
  
        ```python
        import numpy as np
        baseball = [180, 215, 210, 210, 188, 176, 209, 200]
        array = [1, 2, 3, 4, 5, 6, 7, 8]
        print(np.array(baseball) / np.array(array))
        ```

    * 生成的n数组可以进行如下操作（找到棒球队中身高超过180的具体身高）

        ```python
        np_baseball = np.array(baseball)
        tall = np_baseball[np_baseball > 180]
        ```

  * 二维数组
    * 原列表
  
        ```python
        baseball = [[180, 78.4],
            [215, 102.7],
            [210, 98.5],
            [188, 75.2]]
        ```

    * 查看shape（结果为(4, 2)）
  
        ```python
        print(np_baseball.shape)
        ```

    * 通过精确到行列来具体操作二维数组
  
        ```python
        np_baseball[1, 2]
        np_baseball[:, 1] #形成一个新的一维数组
        np_baseball[1, :] #形成一个新的一维数组
        ```

    * 求中位数（np.median()）

        ```python
        array([[10,  7,  4],
              [ 3,  2,  1]])
        np.median(a)
        # 1，2，3，4，7，10 
        # (3+4)/2 = 3.5
        3.5
        ```

    * 求平均数（np.mean()）

        ```python
        array([[10,  7,  4],
              [ 3,  2,  1]])
        np.mean(a)
        # 1，2，3，4，7，10 
        # (1 + 2 + 3 + 4 + 7 + 10)/ 6 = 4.5
        4.5
        ```

    * 求方差（np.std()）
  
        ```python
        print(np.std([1,2,3,4]))
        ```

    * 求相关系数矩阵（np.corrcoef(矩阵1, 矩阵2)）
  
        ```python
        Array1 = [[1, 2, 3], [4, 5, 6]]
        Array2 = [[11, 25, 346], [734, 48, 49]]
        Mat1 = np.array(Array1)
        Mat2 = np.array(Array2)
        correlation = np.corrcoef(Mat1, Mat2)
        print("矩阵1=\n", Mat1)
        print("矩阵2=\n", Mat2)
        print("相关系数矩阵=\n", correlation)
        #函数的返回值还是一个矩阵，
        #结果矩阵的行数*结果矩阵的列数==矩阵1的行数*矩阵2的行数
        ```

    * 两个长度相同的一维矩阵可以联合
  
        ```python
        height = [191, 184, 185, 183, 179, 179]
        position = ['GK', 'M', 'A', 'D', 'D', 'M']

        np_height = np.array(height)
        np_position = np.array(position)

        print((np_height[np_position == 'M']))
        ```

---

## Matplotlib

* 导包

  ```python
  import matplotlib.pyplot as plt
  ```

* 线图
  * plt.plot(列表1/一维数组, 列表2)
  * 两个列表的元素个数必须一致
* 散点图
  * plt.scatter(x, y, s=None, c=None, marker=None, alpha = None)
    * x，y：长度相同的数组，也就是我们即将绘制散点图的数据点，输入数据。
    * s：点的大小，默认 20，也可以是个数组，数组每个参数为对应点的大小。
    * c：点的颜色，默认蓝色 'b'，也可以是个 RGB 或 RGBA 二维行数组。
    * marker：点的样式，默认小圆圈 'o'。
    * alpha：透明度设置，0-1 之间，默认 None，即不透明。

* 直方图
  * plt.hist(列表/数组)

  * ```python
    a = np.array([22,87,5,43,56,73,55,54,11,20,51,5,79,31,27]) 
    plt.hist(a, bins =  [0,20,40,60,80,100]) # 按照[0,20,40,60,80,100]来划分
    plt.hist(a, bins = 10) # 平均分为10个  
    ```

* 绘制网格线
  * plt.grid(True)
* 在图中标记
  * plt.text(横坐标，纵坐标，值)

* 展示图片（plt.show()）
* 将y轴和x轴的比例设置为对数比例：plt.xscale('log')
* 添加横坐标纵坐标和标题描述：plt.xlabel(字符串)/ 
  pltylabel.(字符串)/ plt.title(字符串)
* 更改横纵坐标的数值：plt.xticks(列表1, 列表2)/plt.yticks(列表1, 列表2)
  * 列表1为原先直方图的数值，列表2的值将会替换列表1

---

## Pandas

* 导包: import pandas as pd
* 生成DataFrame
  * 方法：pandas.DataFrame( data, index, columns, dtype, copy)
  * 含义：
    * data：一组数据(ndarray、series, map, lists, dict 等类型)。
    * index：索引值，或者可以称为行标签。
    * columns：列标签，默认为 RangeIndex (0, 1, 2, …, n) 。
    * dtype：数据类型。
    * copy：拷贝数据，默认为 False。

  * 用列表生成
  
  ```python
  import pandas as pd
  data = [['Google',10],['Runoob',12],['Wiki',13]]
  df = pd.DataFrame(data,columns=['Site','Age'],dtype=float)
  ```

  * 用数组生成

  ```python
  import pandas as pd
  data = {'Site':['Google', 'Runoob', 'Wiki'], 'Age':[10, 12, 13]}
  df = pd.DataFrame(data)
  ```

  * 用字典生成
  
  ```python
  import pandas as pd
  data = [{'a': 1, 'b': 2},{'a': 5, 'b': 10, 'c': 20}]
  df = pd.DataFrame(data)
  ```