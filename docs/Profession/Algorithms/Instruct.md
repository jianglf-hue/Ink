<h1 style="text-align:center;">算法大纲</h1>
**数据结构**：线性、树、图、集合和字典

**重要的问题类型**：排序、查找、字符串处理、图问题、组合问题、几何问题、数值问题。



## Table of Contents

#### Ⅰ 暴力法
+ 暴力排序
   + [选择排序](#1.选择排序)
   + [冒泡排序](#2.冒泡排序)
+ 线性查找
   + [顺序查找](#1.顺序查找)
   + [蛮力匹配](#2.蛮力匹配)
+ 穷举查找
   + [深度优先搜索](#1.深度优先搜索)
   + [广度优先搜索](#2.广度优先搜索)

#### Ⅱ 减治法
+ 减常量
  + [插入排序](#1.插入排序])
  + [希尔排序](#2.希尔排序)
  + [拓扑排序](#3.拓扑排序)
  + 生成组合对象
    + [生成排列](#4.生成排列)
    + [生成子集](#5.生成子集)
+ 减常因子算法
  + [折半查找]()
  + [俄式乘法]()
+ 减可变规模算法
  + [计算中值和选择]()
  + [插值查找]()
  + [二叉查找树的查找与插入]()
+ 双指针技巧
  + [左右指针]()
  + [快慢指针]()

#### Ⅲ 分治法
+ 分治排序
  + [归并排序]()
  + [快速排序]()
+ 分而治之
  + [二叉树的遍历]()
  + [karatsuba大整数乘法]()
  + [strassen矩阵乘法]()
  + [最近对问题]()
  + [凸包问题]()

#### Ⅳ 变治法
+ 变治排序
  + [堆排序]()
+ 预排序法
  + [元素唯一性]()
  + [模式计算]()
  + [查找问题]()
+ 高斯消去法
  + [部分选主元法]()
  + [LU分解]()
  + [计算矩阵的逆]()
  + [计算矩阵的行列式]()
+ 霍纳法则和二进制幂
  + [霍纳法则]()
  + [二进制幂]()
+ 平衡查找树
  + [AVL 树]()
  + [2-3 树]()
  + [红黑树]()
+ 问题化简
  + [求最小公倍数]()
  + [计算图中路径数量]()
  + [优化问题的化简]()
  + [线性规划]()
  + [简化为图问题]()

#### 时空权衡
+ 计数排序
  + [桶排序]()
+ 输入增强
  + [Horspool算法]()
  + [Boyer-Moore算法]()
+ 散列法
  + [开散列]()
  + [闭散列]()

#### Ⅴ 动态规划
+ [背包问题]()
+ [记忆化]()
+ [最优二叉树]()
+ [Warshall算法]()
+ [Floyd算法]()

#### Ⅵ 贪婪技术
+ [Prim算法]()
+ [Kruskal算法]()
+ [Dijkstra算法]()
+ [哈夫曼树]()

#### Ⅶ 迭代改进
+ [单纯形法]()
+ [最大流量问题]()
+ [二分图的最大匹配]()
+ [稳定婚姻问题]()

#### Ⅷ 算法能力的极限
+ 如何求下界
  + [平凡下界]()
  + [信息论下界]()
  + [敌手下界]()
  + [问题化简]()
+ 决策树
  + [排序决策树]()
  + [查找有序数组的决策树]()
+ P、NP和NP完全问题
  + [P和NP问题]()
  + [NP完全问题]()

#### Ⅸ 超越算法的极限
+ 回溯法
  + [n皇后问题]()
  + [曼哈顿回路]()
  + [子集]()
  + [一般性说明]()
+ 分支界限法
  + [分配问题]()
  + [背包问题]()
  + [旅行商问题]()
+ NP的近似算法
  + [旅行商问题的近似算法]()
  + [背包问题的近似算法]()
+ 解非线性方程的算法
  + [平分法]()
  + [试位法]()
  + [牛顿法]()



# Ⅰ 暴力法

> 蛮力法(brute force)是一种简单直接地解决问题的方法，常常直接基于问题的描述和所涉及的概念定义
>
> “力”指代计算机的计算能力。

## 暴力排序

### 1.选择排序

> 输入：无序数组； 输出：有序数组
>
> 时间复杂度：θ(n^2)  但键的交换次数为 θ(n)；空间复杂度：1；

```c++
//  selection_sort 将输入的int数组进行选择排序
//  时间复杂度：θ(n^2) 键的交换次数为 θ(n)
//  空间复杂度：0
void selection_sort(int * data, int len){
    for (int i = 0; i < len - 1; i++){
        int minKey = i;
        for (int j = i + 1; j < len; j++){
            // find min key
            if (data[j] < data[minKey]) minKey = j;
        }
        swap(&data[i], &data[minKey]);
    }
}

// swap It swap two int
void swap(int* a, int* b){
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

​	

### 2.冒泡排序

> 输入：无序数组； 输出：有序数组
>
> 时间复杂度：θ(n^2)  键的交换次数为 θ(n^2);空间复杂度：1；

```c++
//  冒泡排序 参数为需要排序的数组，数组的长度
//  时间复杂度：θ(n^2) 键的交换次数为 θ(n^2); 
void bubble_sort(int data[], int len){
    for (int i = 0; i < len - 1; i++){
        for (int j = 0; j < len - 1 - i; j++){           
            if (data[j] > data[j + 1]) 
                swap(&data[j], &data[j + 1]);
        }
    }
}

// swap It swap two int
void swap(int* a, int* b){
    int temp = *a;
    *a = *b;
    *b = temp;
}
```



## 线性查找

> 在一个给定的列表中查准一个给定的值

### 1.顺序查找

> 输入：字符串和待匹配**字符**； 输出：**字符**在字符串中的索引
>
> 时间复杂度：T(n) 最好Ω(1), 最差 O(n)；空间复杂度：S(n) = 1

```c++
// SequentialSearch 查准数组中给定键的索引
// 简单的将给定列表的连续元素和给定查找键比较
// trick：将查找键添加到列表的末尾，查准必定会成功，就不需要在循环时判断是否越界
// 时间复杂度：T(n) = θ(n)
int SequentialSearch(int* data, int len, int key)
{
    // 创建一个新数组 比原来数组长度+1
    int aux[len + 1];
    copy(data, aux, len);
    
    // 新数组最后一项为传入的 key，就无需判断是否越界
    aux[len] = key;

    int result = 0;
    while (aux[result] != key) result++;

    if (result == len) return -1;
    return result;
}

// copy 将 a复制到b 个数为len
void copy(int* a, int*b, int len){
    for (int i = 0; i < len; i++) {
        b[i] = a[i];
    }
}
```



### 2.蛮力法字符串匹配

> 输入：字符串和待匹配**子串**； 输出：**子串**在字符串中的索引
>
> 时间复杂度：T(n)最差 O(mn)空间复杂度： S（n）= 1

```c++
// BruteForceStringMatch 在data中查准匹配模式的字串， 返回字串的首索引
// 时间复杂度： 平均 Θ(n) 最差( data_len * pattern_len )
int BruteForceStringMatch(char* data, int data_len, char* pattern, int pattern_len) {
    for (int i = 0; i <= (data_len - pattern_len); i++) {
        int j = 0;
        while (j < pattern_len && pattern[j] == data[i + j]) {
            j++;
            if (j == pattern_len) return i;
        }
    }
    return -1;
}
```



## 穷举查找

> 它要求生成问题域中的，每一个元素，选出其中满足问题约束的元素，然后找到一个期望的元素

### 1.深度优先搜索

> 以栈的数据结构，系统的遍历图中的所有点和边
>
> 时间复杂度：链表法 θ( |v| + |E| ) 矩阵法 θ( |v|^2 )

```python
# Dfs 深度优先搜索， 输入邻接链表法表示的图, 第一个遍历的key
# 象征勇气：直到找到最远的节点才返回
class DFS():
    def __init__(self, graph: dict):
      self._graph: dict = graph
      self._result: list[str] = []
    
    def _dfs(self, key: str):
        self._result.append(key)
        for nodes in self._graph[key]:
            if nodes not in self._result:
                self._dfs(nodes)
                
    def dfs(self, key: str):
        self._dfs(key)
        return self._result
```



### 2.广度优先搜索

> 以队列的数据结构，系统的遍历图中的所有点和边
>
> 时间复杂度：链表法 θ( |v| + |E| ) 矩阵法 θ( |v|^2 )

```python
# Bfs 广度优先搜索， 输入邻接链表法表示的图, 第一个遍历的key
# 象征谨慎：从最近的元素开始搜索
class BFS():
    def __init__(self, graph: dict):
      self._graph: dict = graph
      self._result: list[str] = []

    def bfs(self, key: str):
        queue: list[str] = [key]
        while(len(queue) > 0):
            local = queue.pop(0)
            for v in self._graph[local]:
                if v not in self._result:
                    self._result.append(v)
                    queue.append(v)
        return self._result
```





# Ⅱ 减治法

> 减治技术利用了一个问题给定实例的解和同样问题的较小实例的解之间的某种关系
>
> 一旦建立了这种关系，我们可以自顶向下，或者自下而上的运用这种关系

## 减常量

### 1.直接插入排序

> f (小数组长度+1) = f (小数组) 。
>
> 性能：C<sub>worst</sub> = θ( n<sup>2</sup> ); C<sub>bast</sub> = θ( n ); C<sub>avg</sub> ≈ 1/4 n<sup>n</sup>  = θ ( n<sup>2</sup> )

```c++
// insertionSort 
// f (array[n+1]) = f (array[n]) 
// 时间复杂度  θ( n^2 ) - θ( n );
void insertionSort(int* a, int len){
    //小数组递增, 自下而上
    for (int i = 1; i < len; i++){
        //从第二个元素开始，取出该元素，进行比较排序
        int loacl = a[i];
        int j = i - 1;
        while (j >= 0 && a[j] > loacl){
            a[j + 1] = a[j];
            j--;
        }
        a[j + 1] = loacl;
    }
}
```



### 2.希尔排序

> 分组插入排序，缩小增量排序
>
> 性能：【非稳定】T = θ(2^n) ~ θ(nlog^2n)

```c++
// shellSort 插入排序的一种缩小增量排序
// 步长的选择是希尔排序的重要部分 T = θ(2^n) ~ θ(nlog^2n)
void shellSort(int a[], const int len){
    int gap = 1, j, temp;
    while (gap < len / 3) gap = 3 * gap + 1;
    while (gap >= 1){
        for (int i = gap; i < len; i++){
            temp = a[i];
            // 将 a[j] 插入到 a[j-grap], a[i-2*gap], a[i-3*gap]中
            for(j = i - gap; j >= 0 && a[j] > temp;  j -= gap)
                a[j + gap] = a[j];
            a[j + gap] = temp;
        }
        gap = gap / 3;
    }
}
```



### 3.拓扑排序

#### Kahn拓扑排序

> 有向图的排序
>
> 性能：T(n) = O(n+e)

```python
# KahnTopoSort 基于减源的拓扑排序, -1策略
class KahnTopo:
    def __init__(self, graph):
        self._graph = graph
   
    # 统计每个结点的边的数量
    def _countEdge(self):
        result = dict()
        # 初始化点
        for key in self._graph.keys():
            result[key] = 0
        # 统计节点的边数
        for value_list in self._graph.values():
            for vertex in value_list:
                result[vertex] += 1
        return result

    def sort(self):
        result = list()
        edgeCount = self._countEdge()
        while (edgeCount):
            for key in list(edgeCount.keys()):
                # 如果边数为0, 则减少关联点的入度并删除
                if edgeCount[key] == 0:
                    for i in self._graph[key]:
                        edgeCount[i] -= 1
                    result.append(key)
                    del edgeCount[key]
        return result

```



#### DFS拓扑排序

> 有向图的排序
>
> 性能：T(n) = O(n+e)

```python
# 基于dfs的拓扑排序 基于暴力法-DFS,输出DFS的逆序
# graph 为 map 结构 邻接链表法表示图
class DFSTopo:
    def __init__(self, graph):
        self._graph = graph
        self._keys = set(graph.keys())
        self._result = list()
        
    def sort(self):
        while len(self._keys) > 0:
            # 随机取一个元素进行dfs
            self._dfs(self._keys.pop())
        self._result.reverse()
        return self._result
    
    def _pushResult(self, value):
        if value not in self._result:
            self._keys.discard(value)
            self._result.append(value)
    
    def _dfs(self, key):
        if len(self._graph[key]) == 0:
            return
        for node in self._graph[key]:
            self._dfs(node)
            # 出栈时，构建dfs森林
            self._pushResult(node)
        self._pushResult(key)
```



### 4.生成排列

##### JohnsonTrotter

> 输入：数组，输出：数组的所有序列组合。
>
> 性能：T = n(n-1)! ≈ n!

```go
// JohnsonTrotter 全排列生成算法 邻位对换法
func JohnsonTrotter(aux []int) []int {
	result := make([]int, 0)
	direc := make([]int, len(aux))
	for i := range direc {
		direc[i] = -1
	}

	for k := findMove(aux, direc); k != -1; k = findMove(aux, direc) {
		result = append(result, toInt(aux))
		// 交换
		t := direc[k] + k
		aux[t], aux[k] = aux[k], aux[t]
		direc[t], direc[k] = direc[k], direc[t]
		// 反转
		reverse(aux, direc, t)
	}
	return result
}

// 数组转化成数字
func toInt(a []int) int {
	result := 0
	for _, v := range a {
		result *= 10
		result += v
	}
	return result
}

//反转比移动项大的所有项的移动方向
func reverse(aux []int, d []int, k int) {
	max := aux[k]
	for i := range aux {
		if aux[i] > max {
			d[i] = d[i] * -1
		}
	}
}

//找到最大可移动项
func findMove(aux []int, direction []int) int {
	result := -1
	max := -1
	for i := range aux {
		j := i + direction[i]
		if j < 0 || j >= len(aux) {
			continue
		}
		if aux[i] > max && aux[j] < aux[i] {
			result = i
			max = aux[i]
		}
	}
	return result
}
```

##### LexicographicPermute

```go
// 以字典序产生排序
// Permute 生成字典序排列
func LexicographicPermute(n int) []int {
	var result = []int{}
	var aux = createList(n)
	for {
		// 将排列添加到结果
		result = append(result, aToInt(aux))
		// 找到最大升序元素 aux[i] < aux[i+1]
		i := findMaxOrdered(aux)
		if i == -1 {
			break
		}
		// 找到最大索引j使得 aux[i] < aux[j]
		j := findMaxBigIndex(aux, aux[i])
		// 交换 a[i],a[j]
		aux[i], aux[j] = aux[j], aux[i]
		// 反转 aux[i+1...n]
		recover(aux, i+1, n-1)
	}
	return result
}

// createList 输入n 输出[1,2..n]
func createList(n int) []int {
	var result = make([]int, n)
	for i := 0; i < n; i++ {
		result[i] = i + 1
	}
	return result
}

// aToInt 将数组转化为数字
// {1，2，3} -> 123
func aToInt(a []int) int {
	var result = 0
	for _, v := range a {
		result *= 10
		result += v
	}
	return result
}

//  recover 反转数组
func recover(a []int, lo, hi int) {
	for lo < hi {
		a[lo], a[hi] = a[hi], a[lo]
		lo++
		hi--
	}
}

// findMaxBigIndex 找到比n大的数的最大索引
func findMaxBigIndex(a []int, n int) int {
	var result = -1
	for i, v := range a {
		if v > n {
			result = i
		}
	}
	return result
}

// findMaxOrdered 寻找数组中最大升序
func findMaxOrdered(a []int) int {
	var result = -1
	for i := 0; i < len(a)-1; i++ {
		if a[i] < a[i+1] {
			result = i
		}
	}
	return result
}
```



### 5.生成子集

> 架构：减治法-生成子集-二进制反射格雷码算法
>
> 效果：输入一个 序列，求该序列的所有子序列
>
> 应用：分配问题(求最有价值的子集)
>


#### 二进制反射格雷码

```go
// BRGC 二进制反射格雷姆码 生成幂集
// 生成二进制数组[[1,0,1]..] -> 对应子集的映射
func BRGC(n int) [][]byte {
	var list [][]byte
	if n == 1 {
		list = [][]byte{[]byte{0}, []byte{1}}
	} else {
		L1 := BRGC(n - 1)
		L2 := recoverCode(L1)

		L1 = shift(L1, byte(0))
		L2 = shift(L2, byte(1))

		list = append(L1, L2...)
	}
	return list
}

// shift 将n加到a的每一个位串前
func shift(a [][]byte, n byte) [][]byte {
	for i := 0; i < len(a); i++ {
		a[i] = append([]byte{n}, a[i]...)
	}
	return a
}

// recover 反转 a
func recoverCode(a [][]byte) [][]byte {
	var result = [][]byte{}
	// 深拷贝
	for i := range a {
		t := append([]byte{}, a[i]...)
		result = append(result, t)
	}
	// 反转
	i, j := 0, len(a)-1
	for i < j {
		result[i], result[j] = result[j], result[i]
		i++
		j--
	}
	return result
}
```





## 减常因子算法

### 1.折半查找

> 有序数组中的的快速查找
>
> 性能：C<sub>avg</sub>( n ) = log<sub>2</sub>n

```c++
// @params：一个有序数组和它的长度，需要查找的key
// @retrun: key的index
int binarySearch(int a[], int len, int k){
    int lo = 0, hi = len - 1;
    while (lo <= hi){
        int m = (lo + hi) / 2;
        if (k == a[m])      return m;
        else if (k < a[m])  hi = m - 1;
        else                lo = m + 1;
    }
    return -1;
}
```



### 2.俄式乘法

> 架构：减治法-减常因子-俄式乘法，位操作
>
> 性能：极高，机器底层的基础操作。

```c++
/**
 *  减治法-减常因子-俄式乘法
 *  n * m = n/2 * 2m
 *  n * m = (n-1)/2 * 2m + m 
*/
int RussianPeasant(int n, int m){
    int sum = 0;
    while (n > 1){
        // n * m = n/2 * 2m
        if (n % 2 == 0){
            n = n >> 1;
            m = m << 1;
        }
        //n * m = (n-1)/2 * 2m + m
        else{
            // 先把 m 存放 sum 中
            // 当 m = 1 时 (n-1)/2 * 2m 被加入sum中
            n = (n - 1) >> 1;
            sum += m;
            m = m << 1;
        }
    }
    return (sum + m);
}
```





## 减可变规模算法

### 1.计算中值和选择问题

> 划分问题：将大于a的划分在右侧，小于a的划分在左侧
>
> 选择问题：寻找数列第k个最小元素的问题。



#### Lomuto划分

```python
#
#   lomuto划分：求数列中值
#   架构：减治法-减可变规模-lomuto划分
#   @params l,r,需要规划的开始端和结束端
#

def lomutoPartition(a: list) -> int:
    l = 0
    r = len(a) - 1

    p = a[l]
    s = l
    for i in range(l, r + 1):
        if a[i] < p:
            s += 1
            a[s], a[i] = a[i], a[s]
    a[l], a[s] = a[s], a[l]
    return s

```



#### 快速选择

> 架构：反复调用Lomuto划分找到数组中第n小的数
>
> 性能：C<sub>worst</sub> = Θ( n<sup>2</sup> )

```python
#
#   快速选择是一种从无序列表找到第k小元素的选择算法。
#   具有很好的平均时间复杂度，然而最坏时间复杂度则不理想.
#   性能： 从O(n log n)至O(n)，不过最坏情况仍然是O(n2)。
#
def quickSelect(a: list, k: int) -> int:
    l = 0
    r = len(a)
    s = lomutoPartition(a)
    if s == (l + k - 1):
        return a[s]
    elif s > (l + k - 1):
        return quickSelect(a[l:s], k)
    else:
        return quickSelect(a[s+1:r], l+k-1-s)

```



### 2.插值查找

> 架构：查字典思想，通过增长率优化版本的二分查找，只适用于有序数组
>
> 性能：与数列均匀度有关，C<sub>best</sub> = O(1);

```c++
/**
 *  插值查找：减治法-减可变规模-插值查找
 *  输入：顺序数组，数组长度，需要查找的key
 *  输出：key对应的索引，如果没有则返回-1；
 * 
*/
int interpolationSearch(int a[], int len, int key)
{

    // 搜索的左右索引
    int l = 0, r = len - 1;
    // 选定的索引
    int index = 0;

    while (a[index] != key && l != r)
    {
        // 通过增长率求取近似索引
        int k = growthRate(a[l], a[r], r - l);
        index = (key - a[0]) / k;

        if (a[index] == key)
        {
            return index;
        }
        // 判断正序还是负序
        if (k >= 0)
        {
            // 缩减搜索范围
            if (a[index] > key)
                l = index;
            else
                r = index;
        }
        else
        {
            if (a[index] > key)
                r = index;
            else
                l = index;
        }
    }

    return -1;
}

// 计算增长率
int growthRate(int a, int b, int num)
{
    return (a + b) / num;
}
```



### 3.二叉查找树的查找和插入

> 架构：减治法-减可变规模-二叉查找树的插入和查找
>
> 性能：查找 C<sub>avg</sub>= O( log 2 (n) )

```c++
// 二叉查找树节点
struct BST_node
{
    int data;
    BST_node *left;
    BST_node *right;

    BST_node(int _data);
    ~BST_node();
};

BST_node::BST_node(int _data)
{
    data = _data;
    left = nullptr;
    right = nullptr;
}

BST_node::~BST_node()
{
    delete left;
    delete right;
}
```

#### 

```c++
// 二叉查找树类
class BST_tree
{
  protected:
    // 根节点
    struct BST_node *root;

  public:
    // 构造和析构
    BST_tree();
    ~BST_tree();

    // 二叉查找树添加节点
    // item：需要添加的节点数据，t：插入位置，默认传入根节点自动匹配插入位置
    struct BST_node *inseart(int item);
    // 二叉查找树查找
    int search(int key);
};

// 构造函数
BST_tree::BST_tree()
{
    this->root = nullptr;
}

// 释放内存
BST_tree::~BST_tree()
{
    delete root;
}
```

#### 插入

```c++
// 二叉查找树的插入
struct BST_node *BST_tree::inseart(int item)
{
    BST_node *local = this->root;
    // 不存在根节点时 将数据创建为根节点
    if (this->root == nullptr)
    {
        this->root = new BST_node(item);
        local = this->root;
        return local;
    }
    // 迭代寻找合适的节点插入数据
    while (true)
    {
        // 如果节点适合则插入
        if (local->left == nullptr && item <= local->data)
        {
            local->left = new BST_node(item);
            local = local->left;
            return local;
        }
        if (local->right == nullptr && item >= local->data)
        {
            local->right = new BST_node(item);
            local = local->right;
            return local;
        }
        // 如果节点不适合则切换
        if (local->left != nullptr && item <= local->data)
        {
            local = local->left;
        }
        else if (local->right != nullptr && item >= local->data)
        {
            local = local->right;
        }
    }
    return local;
}
```

#### 查找

```c++
// 二叉查找树的查找
int BST_tree::search(int key)
{
    // 将当前节点指向根节点
    BST_node *local = this->root;
    while (local != nullptr)
    {
        // 匹配成功则返回数据
        if (key == local->data)
        {
            return local->data;
        }

        // 不匹配则左右切换
        if (key >= local->data)
        {
            local = local->right;
        }
        else if (key <= local->data)
        {
            local = local->left; 
        }
    }
    return local->data;
}
```



## 双指针技巧

### 1.左右指针

### 2.快慢指针





# Ⅲ 分治法

## 合并排序

> 架构：分治法-自上而下合并排序；分治法-自下而上合并排序
>
> 性能：C( n ) = n long<sub>2</sub>n; 需要额外内存空间

### 合并排序-自上而下

```c++
/**
 * 分治法-自上而下合并排序
 * 
*/
void mergeSort(int a[], int l, int r)
{
    if (l == r)
    {
        return;
    }
    int m = (r + l) / 2;
    mergeSort(a, l, m);
    mergeSort(a, m + 1, r);
    merge(a, l, m + 1, r);
}
```

```c++
// 将数组的两段合并
void merge(int a[], int l, int m, int r)
{
    int i, j, k;

    int LEFT_SINZE = m - l;
    int RIGHT_SINZE = r - m + 1;

    // 将数组分割拷贝成两段
    int left[LEFT_SINZE], right[RIGHT_SINZE];
    for (i = l; i < m; i++)
    {
        left[i - l] = a[i];
    }
    for (i = m; i <= r; i++)
    {
        right[i - m] = a[i];
    }

    // 合并
    i = 0, j = 0, k = l;
    while (i < LEFT_SINZE && j < RIGHT_SINZE)
    {
        if (left[i] < right[j])
        {
            a[k++] = left[i++];
        }
        else
        {
            a[k++] = right[j++];
        }
    }

    // 合并剩余
    while (i < LEFT_SINZE)
    {
        
        a[k++] = left[i++];
        
    }
    while (j < RIGHT_SINZE)
    {
        a[k++] = right[j++];
    }
}
```



### 合并排序-自下而上

```c++
/**
 * 自下而上归并排序
*/
void mergeBuSort(int a[], int len)
{
    // 辅助数组aux；
    int *aux = new int[len];
    for (int sz = 1; sz < len; sz += sz)
    {
        for (int lo = 0; lo < len - sz; lo += sz + sz)
        {
            int t = lo + sz + sz - 1;
            int min = t > len - 1 ? len - 1 : t;
            merge(a, aux, lo, lo + sz - 1, min);
        }
    }

    delete[] aux;
}
```

```c++
// 将a[lo..mid]和 a[mid+1..hi]归并
void merge(int a[], int aux[], int lo, int mid, int hi)
{
    int i = lo, j = mid + 1;
    // 将a[lo..hi]复制到aux[lo..hi]
    for (int k = lo; k <= hi; k++)
    {
        aux[k] = a[k];
    }
    // 归并到a[lo..hi]
    for (int k = lo; k <= hi; k++)
    {
        // 当一个数组归并完毕
        if (i > mid)
            a[k] = aux[j++];
        else if (j > hi)
            a[k] = aux[i++];
        // 将小的先归并
        else if (aux[j] < aux[i])
            a[k] = aux[j++];
        else
            a[k] = aux[i++];
    }
}
```



## 快速排序

> 架构：分治法-快速排序
>
> 性能：C<sub>avg</sub>=1.39*n*log<sub>2</sub>n

```c++
// 分治法 ->快速排序
// 性能：C平均 = 1.39*n*log2*n
void quickSort(int a[], int lo, int hi)
{
    if (lo < hi)
    {
        int s = HoarePartition(a, lo, hi);
        quickSort(a, lo, s - 1);
        quickSort(a, s + 1, hi);
    }
}
```

```c++
int HoarePartition(int a[], int lo, int hi)
{
	// 以最左边的数(lo)为基准
	int base = a[lo];
	while (lo < hi) {
		// 从序列右端开始，向左遍历，直到找到小于base的数
		while (lo < hi && a[hi] >= base)
			hi--;
		// 找到了比base小的元素，将这个元素放到最左边的位置
		a[lo] = a[hi];
 
		// 从序列左端开始，向右遍历，直到找到大于base的数
		while (lo < hi && a[lo] <= base)
			lo++;
		// 找到了比base大的元素，将这个元素放到最右边的位置
		a[hi] = a[lo];
	}
 
	// 最后将base放到lo位置。此时，lo位置的左侧数值应该都比lo小；
	// 而lo位置的右侧数值应该都比lo大。
	a[lo] = base;
	return lo;
}
```



## 二叉树遍历及其相关特性

### 计算二叉树的高度

> 架构：分治法-二叉树高度搜索
>
> 性能： C(n) = 2n+1

```c++
struct node
{
    char data;
    node *left;
    node *right;
    node(char ch) : data(ch)
    {
        this->left = nullptr;
        this->right = nullptr;
    };
};

int treeHeight(node *t)
{
    if (t == nullptr)
        return -1;
    else
        return max(height(t->left), height(t->right)) + 1;
}

int max(int a, int b)
{
    if (a > b)
        return a;
    return b;
}
```



### 二叉树的遍历

> 架构：分治法-二叉树遍历
>
> 性能： C(n) = 2n+1

#### 前序遍历

```c++
// 入栈时输出
void preOrderTraversal(node *root)
{
    if (root != nullptr)
    {
        printf("%c\n", root->data);
        preOrderTraversal(root->left);
        preOrderTraversal(root->right);
    }
}
```



#### 中序遍历

```c++
// 中序遍历
// 用于二叉树排序
void inOrderTraversal(node *root)
{
    if (root != nullptr)
    {
        inOrderTraversal(root->left);
        printf("%c\n", root->data);
        inOrderTraversal(root->right);
    }
}
```



#### 后序遍历

```c++
// 后序遍历
// 出栈时输出
void postOrderTraversal(node *root)
{
    if (root != nullptr)
    {
        postOrderTraversal(root->left);
        postOrderTraversal(root->right);
        printf("%c\n", root->data);
    }
}
```



## 大整数乘法和Strassen矩阵乘法

### karatsuba 大整数乘法

> 思想：将大数分解为幂指数相加的形式
>
> 架构：分治法-大整数相乘
>
> 性能：A( n ) ∈ Θ ( n<sup>long<sub>2</sub>3</sup>)

```python
# Solve problem: 降低大数相乘的时间复杂度
# Thought： 将大数分解为幂指数相加的形式
# Architecture： 分治法-karatsuba乘法
# performance： n**(long2 3)
# @params {int,int} 需要相乘的两个大数
# @return int 相乘的结果
def karatsuba(num1: int, num2: int)->int:

    # 递归终止条件
    if (num1 < 10) or (num2 < 10):
        return num1 * num2

    # 计算拆分长度
    num1Str = str(num1)
    num2Str = str(num2)

    maxLength = max(len(num1Str), len(num2Str))
    splitPosition = int(maxLength / 2)

    # 拆分为 high1, low1, high2, low2
    high1, low1, high2, low2 = 0, 0, 0, 0
    if len(num1Str[: -splitPosition]) < 1:
        high1 = 0
        low1 = int(num1Str[-splitPosition:])
    else:
        high1 = int(num1Str[:-splitPosition])
        low1 = int(num1Str[-splitPosition:])

    if len(num2Str[: -splitPosition]) < 1:
        high2 = 0
        low2 = int(num2Str[-splitPosition:])
    else:
        high2 = int(num2Str[:-splitPosition])
        low2 = int(num2Str[-splitPosition:])

    # 计算z2, z0, z1, 此处的乘法使用递归
    z0 = karatsuba(low1, low2)
    z1 = karatsuba((low1 + high1), (low2 + high2))
    z2 = karatsuba(high1, high2)

    return (z2 * 10 ** (2 * splitPosition)) + ((z1 - z2 - z0)*10**(splitPosition)) + z0

```



### Strassen矩阵乘法

> 
>

。。。



## 用分治法解最近对问题和凸包问题

### 最近对问题

> 
>

```c++
#pragma one
#include <math.h>
#include <stdio.h>
#include <vector>
#define DBL_MAX 1.7976931348623158e+308  // max value

struct Point {
  double x, y;
};
class CloestPair {
 private:
  int size;
  char flage;
  Point* aux;     // 辅助函数
  Point* axis_x;  // x轴排序
  Point* axis_y;  // y轴排序

  void clean() {
    if (aux != nullptr) delete[] aux;
    if (axis_x != nullptr) delete[] axis_x;
    if (axis_y != nullptr) delete[] axis_y;
  };

  void merge(Point* a, int lo, int mid, int hi) {
    int i = lo, j = mid + 1;
    // copy to aux array
    for (int k = lo; k <= hi; k++) {
      this->aux[k] = a[k];
    }
    if (this->flage == 'x') {
      for (int k = lo; k <= hi; k++) {
        if (i > mid)
          a[k] = aux[j++];
        else if (j > hi)
          a[k] = aux[i++];
        else if (aux[j].x < aux[i].x)
          a[k] = aux[j++];
        else
          a[k] = aux[i++];
      }
    } else if (this->flage == 'y') {
      for (int k = lo; k <= hi; k++) {
        if (i > mid)
          a[k] = aux[j++];
        else if (j > hi)
          a[k] = aux[i++];
        else if (aux[j].y < aux[i].y)
          a[k] = aux[j++];
        else
          a[k] = aux[i++];
      }
    }
  };
  void MergeSort(Point* a, int lo, int hi) {
    if (hi <= lo) return;
    int mid = lo + (hi - lo) / 2;
    MergeSort(a, lo, mid);
    MergeSort(a, mid + 1, hi);
    merge(a, lo, mid, hi);
  };
  void copy(Point* from, Point* to, int len) {
    for (int i = 0; i < len; i++) {
      to[i] = from[i];
    }
  };
  double min(double a, double b) {
    if (a > b) {
      return b;
    }
    return a;
  }
  double EfficientClosestPair(Point* P, Point* Q, int _size) {
    double dminsq = DBL_MAX;

    if (_size <= 3) {
      // copy to aux array a;
      // 将点合并到一个辅助数组
      int len = _size * 2;
      Point* a = new Point[len];
      for (int i = 0; i < _size; i++) {
        a[i] = P[i];
      }
      for (int i = _size; i < len; i++) {
        a[i] = Q[i];
      }
      // Brute force method for the shortest distance
      // 蛮力法求最近距离
      for (int i = 0; i < len - 1; i++) {
        for (int j = i + 1; j < len; j++) {
          double dis = pow(a[i].x - a[j].x, 2) + pow(a[i].y - a[j].y, 2);
          if (dis != 0 && dis < dminsq) dminsq = dis;
        }
      }
      delete[] a;

    } else {
      int mid = _size / 2;

      Point* Pl = new Point[mid];
      Point* Ql = new Point[mid];
      Point* Pr = new Point[_size - mid];
      Point* Qr = new Point[_size - mid];

      copy(P, Pl, mid);
      copy(Q, Ql, mid);
      copy(P, Pr, _size - mid);
      copy(Q, Qr, _size - mid);

      double Dl = EfficientClosestPair(Pl, Ql, mid);
      double Dr = EfficientClosestPair(Pr, Qr, _size - mid);

      double d = min(Dl, Dr);
      double m = P[(_size / 2) - 1].x;

      std::vector<Point> vec;
      for (int i = 0; i < _size; i++) {
        if (abs(Q[i].x - m) < d) {
          vec.push_back(Q[i]);
        }
      }
      dminsq = pow(d, 2);

      int num = vec.size();
      for (int i = 0; i < num; i++) {
        int k = i + 1;
        while (k <= num - 1 && pow(vec[k].y - vec[i].y, 2) < dminsq) {
          double t = pow(vec[k].x - vec[i].x, 2) + pow(vec[k].y - vec[i].y, 2);
          dminsq = min(t, dminsq);
          k++;
        }
      }
    }

    return sqrt(dminsq);
  };

 public:
  // 构造函数
  CloestPair() {
    this->aux = nullptr;
    this->axis_x = nullptr;
    this->axis_y = nullptr;
  };

  // 析构函数
  ~CloestPair() { this->clean(); };

  // 计算最近对
  double solveCloestPair(Point* a, int _size) {
    // 先清理内存
    this->clean();

    // 分配内存
    size = _size;
    aux = new Point[size]();
    axis_x = new Point[size]();
    axis_y = new Point[size]();

    // 复制内容
    for (int i = 0; i < _size; i++) {
      axis_x[i] = a[i];
      axis_y[i] = a[i];
    }

    // 排序
    flage = 'x';
    MergeSort(axis_x, 0, _size - 1);
    flage = 'y';
    MergeSort(axis_y, 0, _size - 1);

    // 分治求最短距离
    return EfficientClosestPair(axis_x, axis_y, this->size);
  }
};
```

测试

```c++
int main() {
  int n = 20;

  CloestPair* cp = new CloestPair();
  Point a[] = {{1, 3}, {2, 7}, {1, 8}, {6, 0}};
  double dis = cp->solveCloestPair(a, 4);
  delete cp;
  printf("min dist: %lf\n", dis);
  return 0;
}
```



### 凸包问题

> 
>

…



<br />

# Ⅳ 变治法

## 预排序

>思想：有序列表更容易求解。

### 检测数组中元素的唯一性

```javascript
/**
 * @description 预排序检测数组唯一性
 * @param {array} a 
 * @returns {boolean}
 */
function PresortElementUniqueness(a) {
    let t = a.concat();
    mergeSort(t);
    for (let i = 0; i <= t.length - 2; i++) {
        if (t[i] == t[i + 1]) return false;
    }
    return true;
}

/**
 * @description 分治法-自下而上的归并排序
 * @param {array} a 
 */
function mergeSort(a) {
    let n = a.length;
    let aux = new Array(n);

    let min = (m, n) => m > n ? n : m;

    let merge = (a, lo, mid, hi) => {
        let i = lo, j = mid + 1;
        for (let k = lo; k <= hi; k++) {
            aux[k] = a[k];
        }
        for (let k = lo; k <= hi; k++) {
            if (i > mid)                a[k] = aux[j++];
            else if (j > hi)            a[k] = aux[i++];
            else if (aux[j] < aux[i])   a[k] = aux[j++];
            else                        a[k] = aux[i++];
        }
    }

    for (let sz = 1; sz < n; sz += sz) {
        for (let lo = 0; lo < n - sz; lo += sz + sz) {
            merge(a, lo, lo + sz - 1, min(lo + sz + sz - 1, n - 1));
        }
    }
}
```

测试

```javascript
function main() {
    let a = [3, 5, 6, 7, 8, 2, 8, 34, 6, 23, 12, 24, 6, 37, 7];
    console.log(PresortElementUniqueness(a));
}
```



### 模式计算

```javascript

/**
 * @description 预排序检测数组频率出现最多的元素
 * @param {array} a 
 * @returns {boolean}
 */
function PresortMode(a) {
    let t = a.concat();
    mergeSort(t);
    let i = 0, modefrequency = 0, modevalue = null;
    while (i <= t.length - 1) {
        let runlength = 1, runvalue = t[i];
        while (i + runvalue <= t.length - 1 && t[i + runlength] == runvalue) {
            runlength++;
        }
        if (runlength > modefrequency) {
            modefrequency = runlength;
            modevalue = runvalue;
        }
        i += runlength;
    }
    return modevalue;
}

/**
 * @description 分治法-自下而上的归并排序
 * @param {array} a 
 */
function mergeSort(a) {
    let n = a.length;
    let aux = new Array(n);

    let min = (m, n) => m > n ? n : m;

    let merge = (a, lo, mid, hi) => {
        let i = lo, j = mid + 1;
        for (let k = lo; k <= hi; k++) {
            aux[k] = a[k];
        }
        for (let k = lo; k <= hi; k++) {
            if (i > mid) a[k] = aux[j++];
            else if (j > hi) a[k] = aux[i++];
            else if (aux[j] < aux[i]) a[k] = aux[j++];
            else a[k] = aux[i++];
        }
    }

    for (let sz = 1; sz < n; sz += sz) {
        for (let lo = 0; lo < n - sz; lo += sz + sz) {
            merge(a, lo, lo + sz - 1, min(lo + sz + sz - 1, n - 1));
        }
    }
}
```

测试

```javascript
function main() {
    let a = [1, 1, 8, 5, 5, 6, 8, 8, 34, 6, 7, 5, 8, 6, 2, 5, 9, 10, 5];
    console.log(PresortMode(a));
}
```



### 查找问题

>架构:	先排序再进行折半查找。
>
>性能: 	T<sub>sort</sub>( n ) + T<sub>search</sub> = Θ(n log n) + Θ(long n)
>
> 如果我们要在同一个列表中进行多次查找，在排序上花费一些时间是值得的。

```javascript

/**
 * @description 变治法-预排序查找
 * @param {array} a  
 * @param {int} key 
 */
function PresortSearch(a, key) {
    let t = a.concat();
    let l = 0, r = t.length - 1, m = 0;
    mergeSort(t);
    while (l <= r) {
        m = parseInt((l + r) / 2);
        if (t[m] == key) {
            return m;
        }
        if (key < a[m]) {
            r = m - 1;
        } else {
            l = m + 1;
        }
    }
    return -1;
}


/**
 * @description 分治法-自下而上的归并排序
 * @param {array} a 
 */
function mergeSort(a) {
    let n = a.length;
    let aux = new Array(n);

    let min = (m, n) => m > n ? n : m;

    let merge = (a, lo, mid, hi) => {
        let i = lo, j = mid + 1;
        for (let k = lo; k <= hi; k++) {
            aux[k] = a[k];
        }
        for (let k = lo; k <= hi; k++) {
            if (i > mid) a[k] = aux[j++];
            else if (j > hi) a[k] = aux[i++];
            else if (aux[j] < aux[i]) a[k] = aux[j++];
            else a[k] = aux[i++];
        }
    }

    for (let sz = 1; sz < n; sz += sz) {
        for (let lo = 0; lo < n - sz; lo += sz + sz) {
            merge(a, lo, lo + sz - 1, min(lo + sz + sz - 1, n - 1));
        }
    }
}

```

测试
```javascript
function main() {
    let a = [3, 5, 7, 1, 9, 2, 3, 5, 7, 8, 9, 9, 0, 3, 12, 1, 14, 20, 17, 10]
    console.log(PresortSearch(a, 8));
}
```



## 高斯消去法

### 部分选主元法

```python
def betterForwardElimination(matrix:list,vector:list)->list:
    lenth = len(matrix)
    for i in range(lenth):
        matrix[i].append(vector[i])
    for i in range(lenth):
        pivotrow = i
        for j in range(i+1,lenth):
            if abs(matrix[j][i])>abs(matrix[pivotrow][i]):
                pivotrow = j
        for k in range(i,lenth+1):
            matrix[i][k],matrix[pivotrow][k] = matrix[pivotrow][k],matrix[i][k]
        for j in range(i+1,lenth):
            t = matrix[j][i]/matrix[i,i]
            for k in range(i,lenth+1):
                matrix[j][k] = matrix[j][k] - matrix[i][k]*t
    return []
```



### LU分解



### 计算矩阵的逆



### 计算矩阵的行列式





## 平衡查找树

### AVL 树

### 2-3 树

### 红黑树
