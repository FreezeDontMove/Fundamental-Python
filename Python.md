# Python基础知识点

## 零零散散

* 乘方：**
* True False 首字母大写
* print后只能跟字符串，其他类型须转换成字符串
* 字符串切片list[a:b]中，b > a
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
