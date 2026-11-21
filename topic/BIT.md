# 树状数组（Binary Indexed Tree，BIT）

## 一、 树状数组的引入

假设有一个数组，我们需要频繁执行两种操作：
1. 单点修改：将$`a[i]`$增加$`x`$。
2. 区间查询：查询$`[l,r]`$的元素之和。

### 方法一：

直接维护原数组，时间复杂度如下：单点修改：$`O(1)`$；区间求和：$`O(n)`$。

### 方法二：

维护一个前缀和数组：$`s[i]=\sum_{j=1}^{i} a[j]`$，则查询区间和$`sum(l,r)=s[r]-s[l-1]`$。此时时间复杂度如下：区间查询：$`O(1)`$；单点修改：$`O(n)`$。

上面两种方法只能兼顾 单点修改 或 区间查询 一种类型，有没有一种方法能够同时兼顾两种类型的方法？

有的，有一个数据结构叫做树状数组，它不维护所有的前缀和，而是将数组拆分成若干长度为$`2`$的幂的区间，保存这些区间的和。这样可以同时实现如下的时间复杂度：单点修改：$`O(log~n)`$；区间求和：$`O(log~n)`$

## 二、树状数组的原理

### 树状数组存储内容：

定义一个新数组：$`tree[i]=\sum_{j=(i-lowbit(i)+1)}^{i} a[j]`$。即$`tree[i]`$存储以$`i`$为右端点、长度为$`lowbit(i)`$的连续区间之和。例如：$`tree[1]`$管理$`[1,1]`$，$`tree[2]`$管理$`[1,2]`$，$`tree[4]`$管理$`[1,4]`$，$`tree[6]`$管理$`[5,6]`$

### lowbit函数

树状数组的$`lowbit`$函数返回一个正整数在二进制表示中，最低位的$`1`$所代表的数值。使用$`x~\&~(-x)`$实现，原因：计算机采用补码表示负整数，原数取反加$`1`$后，最低位的那个$`1`$会保留，而它右侧的位都是$`0`$。两者按位与，其他位置全部清零。

### query函数: i-=lowbit(i)

现在我们要查询$`prefix(7)=a[1]+a[2]+\dots+a[7]`$，直接累加需要遍历7个元素，但是树状数组可以把$`[1,7]`$拆分成$`[1,4]\cup[5,6]\cup[7,7]`$，因此$`prefix(7)=tree[4]+tree[6]+tree[7]`$。因为$`tree[i]`$已经覆盖$`[i-lowbit(i)+1,i]`$，下一步只需要处理$`[1,i-lowbit(i)]`$，所以新的右端点是$`i^{'}=i-lowbit(i)`$。

时间复杂度：$`O(log~n)`$

### range_sum函数

查询$`[l,r]`$的元素之和，只需要返回$`query(r)-query(l-1)`$即可。

### update函数: i+=lowbit(i)

现在我们要修改$`a[3]`$，因为$`tree[i]`$管理以$`i`$为右端点的一个区间，除了更新当前节点，还需要更新包含该区间的更大节点。节点$`i`$的直接父节点就是$`i+lowbit(i)`$，因此我们可以不断跳到父节点，直到超过数组长度。

### C++代码模板
```
    vector<int> tree;
    int n;
    int lowbit(int x){
        return x&-x;
    }
    void update(int x,int val){
        while(x<=n){
            tree[x]+=val;
            x+=lowbit(x);
        }
    }
    int query(int x){
        int ans=0;
        while(x){
            ans+=tree[x];
            x-=lowbit(x);
        }
        return ans;
    }
    int range_sum(int l,int r){
        return query(r)-query(l-1);
    }
```

## 三、树状数组的进阶应用

### 统计元素出现次数

树状数组维护的未必是原数组的数值，也可以是频率。令$`tree`$ 维护频率数组，就能快速查询：小于等于$`x`$的元素数量。某个值域 $`[l,r]`$ 内的元素数量。动态插入或删除一个数后的排名。

### 逆序对

当遍历到当遍历到 $`x`$ 时：已经遍历过的元素数量是 $`i`$。小于等于 $`x`$ 的元素数量是 $`query(x)`$。所以大于 $`x`$ 的元素数量就是 $`i - query(x)`$。

### 离散化

如果直接用数值作为树状数组的下标，会遇到负数和过大的值域，我们可以使用离散化保留大小关系的同时将值域压缩到$`[1,m]`$。

### 区间修改+单点查询

可以维护差分数组，$`d[i]=a[i]-a[i-1]`$，区间修改给$`[l,r]`$增加$`x`$，只需要$`d[l]+=x`$，$`d[r+1]-=x`$。而单点查询$`a[i]=\sum_{j=1}^{i} d[j]`$。因此，用树状数组维护差分数组即可。

## 四、相关题目

### [303. 区域和检索 - 数组不可变](https://leetcode.cn/problems/range-sum-query-immutable/)

这道题只需要使用前缀和即可，不需要树状数组。

### [307. 区域和检索 - 数组可修改](https://leetcode.cn/problems/range-sum-query-mutable/)

树状数组的模板题。

### [3152. 特殊数组 II](https://leetcode.cn/problems/special-array-ii/)

这道题的重点是要想明白树状数组中维护的是什么，这道题维护的是相邻元素奇偶性是否相同的0/1数组。因为不需要修改，所以使用前缀和更简单。

### [1649. 通过指令创建有序数组](https://leetcode.cn/problems/create-sorted-array-through-instructions/)

这道题树状数组维护的是元素出现次数，需要求动态排名。每次插入一个数$`x`$，需要知道：当前有多少个数严格小于它$`(query(x-1))`$；当前有多少数严格大于它$`i-query(x)`$

### [315. 计算右侧小于当前元素的个数](https://leetcode.cn/problems/count-of-smaller-numbers-after-self/)

离散化，创建原数组的副本；将副本排序；将副本去重；查找原数组的每一个元素在副本中的位置，位置即为排名，将其作为离散化后的值。然后从右往左遍历，计算右侧小于当前元素的个数$`(query(x-1))`$

### [493. 翻转对](https://leetcode.cn/problems/reverse-pairs/)

先离散化，对于倍数关系，关键是先计算原始数值的阈值，再通过二分查找将阈值转换为树状数组的查询边界。统计历史值落在指定值域中的数量：$`nums[i] \gt 2nums[j]`$

### [327. 区间和的个数](https://leetcode.cn/problems/count-of-range-sum/)

问题可以转化为统计历史前缀和落在指定值域中的数量。$`s[j]-upper\le s[i]\le s[j]-lower`$

### [2426. 满足不等式的数对数目](https://leetcode.cn/problems/number-of-pairs-satisfying-inequality/)

问题可以转化成统计历史数组差落在指定值域中的数量。$`nums1[i]-nums1[j]\le nums2[i]-nums2[j]+diff`$

### [2659. 将数组清空](https://leetcode.cn/problems/make-array-empty/)

上一个位置pre,下一个位置i。从pre到i要经过多少有效元素？树状数组维护已失效元素的位置下标。

### [2179. 统计数组中好三元组数目](https://leetcode.cn/problems/count-good-triplets-in-an-array/)

先把两个排列转化为相对位置关系，（$`nums2`$使用$`nums1`$的置换）。然后再统计每个位置左侧更小元素的数量$`(query(x))`$和右侧更大元素的数量：比$`nums[i]`$大的元素总共有$`n-1-nums[i]`$个，左边已经有$`i-query(x)`$，所以右边还有$`n-1-nums[i]-(i-query(x))`$。
