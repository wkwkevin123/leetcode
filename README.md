# leetcode

Improve algorithm skills

## 刷题计划

每天刷三道算法题：力扣每日一题+题库按顺序2题。要写一下自己的解题心得。必要的时候可以计时。

### 9月9日

#### [3871. 统计范围内的逗号 II](https://leetcode.cn/problems/count-commas-in-range-ii/)

前一天做了他的简单版，不过用的是面向测试用例解答，然后看题解详细说明了当测试用例变大的时候应该怎么做。今天就刚好把昨天看到的题解用代码敲出来了。用到的想法是按照数的位数进行分段讨论。

$\\color{red}{\text{时间：很快。但是不是独立思考出来的}}$

#### [1. 两数之和](https://leetcode.cn/problems/two-sum/)

暴力做法是遍历两遍，找到所有二元对的组合判断和是否为目标值$`target`$。改进做法使用哈希表，在遍历之前先询问哈希表中是否存在和当前遍历的数配对的情况，然后再将该数存入哈希表中。至于为什么要先找再存，是因为不能使用两次相同的元素，如果可以使用相同的元素，就要先存再找了。

$\\color{red}{\text{时间：1min30s。独立思考}}$

#### [2. 两数相加](https://leetcode.cn/problems/add-two-numbers/)

这道题是链表的两数之和，不过它简单一点，已经帮我们把数逆序了。我们要做的是按照高精度加法的思路，依次遍历每个数位和当前进位，得到该位的总和以及下一个进位。不断循环该过程，最后注意处理如果最后进位不为0的情况，要再追加一个1。

$\\color{red}{\text{时间：7min36s。独立思考}}$

### 9月10日

#### [2265. 统计值等于子树平均值的节点数](https://leetcode.cn/problems/count-nodes-equal-to-average-of-subtree/)

这道题的思路是计算子树的和以及子树的大小，我卡在了如何记录两个数据。我的想法是$`dfs`$两次,，但是$`dfs`$一次后对应的树改变了，无法进行第二次。然后看了题解，可以在返回值里做文章，返回一个$`pair`$对记录子树的总和以及子树的大小。豁然开朗，立马敲下代码，写出来了。

$\\color{red}{\text{时间：30min左右。看了一点题解}}$

#### [3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/)

这道题使用的是滑动窗口和哈希表解法，左端点固定，不断扩展右端点。如果中途右端点不满足要求了，就尝试移动左端点使其重新满足要求。属于不定长滑动窗口类型。

$\\color{red}{\text{时间：2min41s。独立思考}}$

#### [4. 寻找两个正序数组的中位数](https://leetcode.cn/problems/median-of-two-sorted-arrays/)

**我的第一想法是按照归并排序的思路，先合并两个有序链表存在一个新数组中，然后就可以求这个新数组的中位数了。难点是归并排序。但是该时间复杂度是$`O(m+n)`$，空间复杂度$`O(m+n)`$，不符合题目$`O(log(m+n))`$的要求。第二个想法是不用真的保存在一个数组中，而是每次遍历都排除一个答案，空间复杂度可以降到$`O(1)`$。另一个想法是分治，每次比较两个数组的中位数，排除其中较小元素左边的所有数，但是存在问题，可能排除了过多的元素。看了题解发现每次比较的是数组$`（k/2-1）`$位置上的数，并排除$`（k/2-1）`$个数，然后更新k。还有第四种解法，二分查找较短数组的分割点，使两个数组的个数相同，如果左边数组的最大值$` \le `$右边数组的最小值，则分割成立，返回答案。**

$\\color{red}{\text{时间：第二个想法29min39s，独立思考。第一个想法9min，独立思考。第三个想法没写出来。第四种解法自己没想到，看了题解才懂}}$

### 9月11日

#### [3483. 不同三位偶数的数目](https://leetcode.cn/problems/unique-3-digit-even-numbers/)

这道题我采用的暴力的做法，三重循环枚举每一个数位，然后判断最后形成的是否是三位数，是否是偶数。如果是把它存在$`set`$中，最后返回$`set`$的大小即可。

$\\color{red}{\text{时间：4min29s。独立思考}}$

#### [5. 最长回文子串](https://leetcode.cn/problems/longest-palindromic-substring/)

**这道题我的想法是让每一个位置作为回文串的中心，向左右两边遍历。有两种情况，一种是中心只有一个，另一种是中心有两个。可以遍历两次分别进行讨论。看题解发现这种方法叫做中心扩展法。然后还有一种叫做动态规划的解法，用一个数组$`dp[i][j]`$记录i到j是否是回文串来避免重复计算。具体做法是可以枚举左右端点，如果$`s[l]==s[r]\&\&(r-l<=2||dp[l+1][r-1])`$，则$`dp[i][j]`$为true。注意这里要先枚举右端点再枚举左端点。因为$`dp[i][j]`$的确定要依靠$`dp[i+1][j-1]`$**

$\\color{red}{\text{时间：中心扩展法5min左右。独立思考}}$

#### [6. Z 字形变换](https://leetcode.cn/problems/zigzag-conversion/)

这道题的想法是利用周期来做，计算出每个字符所在的行和列，然后存在一个新二维数组中，最后按行遍历这个二维数组。难点是找到计算行和列的表达式。看了题解，发现有一个更好的办法是设置一个标记记录当前的移动方向是向上还是向下，来判断当前字符位于第几行。

$\\color{red}{\text{时间：代码很快写出来了，debug用了很久。独立思考}}$

### 9月12日

#### [3414. 不重叠区间的最大得分](https://leetcode.cn/problems/maximum-score-of-non-overlapping-intervals/)

**刚开始写这道题没一点思路，不知道如何处理。然后看题解学习。这道题的前身是没有最多4个的限制,做法是先按照结束时间排序，然后动态规划遍历，如果不选第i个，$`dp[i]=dp[i-1]`$，如果选第i个，$`dp[i]=dp[j]+profit[i]`$,其中j是满足$`end[j]{<}start[i]`$条件中最大的数（可以用二分搜索，因为已经按结束时间排好序了）。然后这道题多了一个限制，所以在动态规划时多加一维度，如果不选第i个，$`dp[i][j]=dp[i-1][j]`$;如果选第i个，$`dp[i][j]=dp[k][j-1]+profit[i]`$，其中k是满足$`end[k] \lt start[i]`$条件中最大的数（可以用二分搜索，因为已经按结束时间排好序了）。这道题还有一个难点是要返回最小字典序的答案，所以在更新最大值时要顺便更新答案的组成。**
还做了几题相似题目:

+ [1235. 规划兼职工作](https://leetcode.cn/problems/maximum-profit-in-job-scheduling/)，[2008. 出租车的最大盈利](https://leetcode.cn/problems/maximum-earnings-from-taxi/):无限制;
+ [1751. 最多可以参加的会议数目 II](https://leetcode.cn/problems/maximum-number-of-events-that-can-be-attended-ii/):限制k个;
+ [2054. 两个最好的不重叠活动](https://leetcode.cn/problems/two-best-non-overlapping-events/):限制k=2;
+ [3414. 不重叠区间的最大得分](https://leetcode.cn/problems/maximum-score-of-non-overlapping-intervals/)（本题）:限制k=4且要输出字典序最小的方案。

$\\color{red}{\text{时间：3h左右}}$

#### [7. 整数反转](https://leetcode.cn/problems/reverse-integer/)

不断循环取模，得到反转整数。注意先判断是否是负数，再用$`abs`$函数转化为正数进行求解。要先判断是否越界再进行运算。注意判断溢出如果不能使用$`long~long`$的话使用如下方法：

![image-20260918113038730](https://github.com/wkwkevin123/leetcode/blob/main/images/image-20260918113038730.png)

$\\color{red}{\text{时间：5min35s}}$

#### [8. 字符串转换整数 (atoi)](https://leetcode.cn/problems/string-to-integer-atoi/)

遇到空格，跳过；遇到正号或者负号或者数字，循环看下一个字符直到不是数字为止，退出；遇到其他字符，退出。不能使用$`long~long`$的话先按照下面方法判断是否越界，再进行运算：

![image-20260918113222351](https://github.com/wkwkevin123/leetcode/blob/main/images/image-20260918113222351.png)

$\\color{red}{\text{时间：7min18s}}$

### 9月14日

#### [836. 矩形重叠](https://leetcode.cn/problems/rectangle-overlap/)

这道题可以把它转化为一维形式，只要横坐标严格相交并且纵坐标严格相交，则两个矩形相交。我判断两段线段相交的方法是分类讨论。分别判断左右两端点是否在落在另一个线段中，另一个线段也同样判断。看了题解后发现，判断两个区间是否有交集：正向思维就是我的想法，逆向思维是判断所有不相交的情况，A在B前或者A在B后。还有一种优化的思路，判断$`max(l_1,l_2)<min(r_1,r2)`$即可。

$\\color{red}{\text{时间：24min46s。独立思考}}$

#### [9. 回文数](https://leetcode.cn/problems/palindrome-number/)

这道题和[7. 整数反转](https://leetcode.cn/problems/reverse-integer/)类似，思路是分情况讨论，负数因为有负号不可能是回文数，然后判断正数，如果是回文数的话，反转后应该等于本身，判断溢出的方法是在运算之前判断$`res`$是否大于$`INT_MAX/10`$。看了题解后发现有更高效的方法，即只反转一半数字来避免溢出，只要$`x`$还大于$`res`$就继续反转，最终比较剩余的$`x`$是否等于$`res`$（长度为偶数）或者等于$`res/10`$（长度为奇数）即可

$\\color{red}{\text{时间：3min04s。独立思考}}$

#### [10. 正则表达式匹配](https://leetcode.cn/problems/regular-expression-matching/)

**没什么思路，看了题解。发现是动态规划，$`dp[i][j]`$代表字符串s的前i个字符和p的前j个字符能否匹配。当$`p[j-1]=='*'`$时，$`dp[i][j]=dp[i][j-2] || (dp[i-1][j] \&\& match(s[i-1],p[j-2]))`$。当$`p[j-1]!='*'`$时，$`dp[i][j]=dp[i-1][j-1]\&\&match(s[i-1],p[j-1])`$。初始化如下：$`dp[0][0]=true;dp[0][j]=dp[0][j-2]\&\&p[j-1]='*'`$。这题的难点主要是转移方程不好想，导致无从下手。**

$\\color{red}{\text{时间：43min。看了题解}}$

### 9月15日

#### [2472. 不重叠回文子字符串的最大数目](https://leetcode.cn/problems/maximum-number-of-non-overlapping-palindrome-substrings/)

**一开始没思路，看了题解后发现很简单，划分型$`dp`$/贪心。$`dp[i]`$表示以$`s[i-1]`$结尾的能划分的回文子字符串最大数目。如果不选$`s[i-1]`$，则$`dp[i]=dp[i-1]`$，如果选$`s[i-1]`$，则要求$`[i-k,i-1]`$或者是$`[i-k-1,i-1]`$是回文串，此时$`dp[i]=max(dp[L])+1`$，其中$`L`$为$`i-k`$或者是$`i-k-1`$。 另一种方法是贪心，第一个回文子串的右端点越小越好。另外还做了灵神题单中划分型$`dp`$的相关题目：**

+ [132. 分割回文串 II](https://leetcode.cn/problems/palindrome-partitioning-ii/)
+ [2707 字符串中的额外数组](https://leetcode.cn/problems/extra-characters-in-a-string/)
+ [3196 最大化子数组的总成本](https://leetcode.cn/problems/extra-characters-in-a-string/)
+ [2767 将字符串分割为最少的美丽子字符串](https://leetcode.cn/problems/partition-string-into-minimum-beautiful-substrings/)

$\\color{red}{\text{时间：dp用了16min。看了题解}}$

#### [11. 盛最多水的容器](https://leetcode.cn/problems/container-with-most-water/)

**这道题我一开始的想法是找左边的最大值和右边的最大值位置，然后结果是他们两个之间的较小值乘以他们的距离。但是这样忽略了一个问题：不一定是在最大值位置上能盛的水最多，因为他们的距离不一定是最远的。看了题解，发现用的是双指针的做法，开始时双指针指在数组的左右两端，每次移动较短的那根直到两指针相遇即可。**

$\\color{red}{\text{时间：1min49s。看了题解}}$

#### [12. 整数转罗马数字](https://leetcode.cn/problems/integer-to-roman/)

我的想法是将每个可能用到的数字存在一个$`map`$，然后从大到小遍历这个$`map`$得到最终的答案。看了题解发现有别的做法，根据千位，百位，十位，个位上的数字来做，更巧妙一点。

$\\color{red}{\text{时间：12min53s。独立思考}}$

### 9月16日

#### [1621. 大小为 K 的不重叠线段的数目](https://leetcode.cn/problems/number-of-sets-of-k-non-overlapping-line-segments/)

使用动态规划，$`dp[i][j]`$表示到$`x=i-1`$时，已经有$`j`$个线段的方案数。如果最后一个线段的右端点不是$`j`$，则$`dp[i][j]=dp[i-1][j]`$，如果最后一个线段的右端点是$`j`$，则对于$`\forall p \in [0,j)`$，都有最后一个线段在$`[p,j]`$，方案数为 $`\sum_{p=0}^{j-1} dp[i-1][p]`$。此时可以用前缀和优化，边计算值边计算前缀和。

$\\color{red}{\text{时间：想了很久。独立思考做出来了}}$

#### [13. 罗马数字转整数](https://leetcode.cn/problems/roman-to-integer/)

根据罗马数字的书写规则，当前字符所代表的数字比下一个字符更小时，用下一个字符减去当前字符。否则直接加上当前字符。

$\\color{red}{\text{时间：4min46s。独立思考}}$

#### [14. 最长公共前缀](https://leetcode.cn/problems/longest-common-prefix/)

这道题的思路是依次比较每个字符串和第一个字符串的前缀，如果超出了某个字符串的长度或是匹配到不相等就直接返回答案。如果最终没有返回答案，说明第一个字符串就是答案。第二种方法是字典树，通过构建字典树，然后从头开始遍历，如果该节点只有一个孩子且该节点不是结束字符，继续向下遍历，否则直接返回答案。

$\\color{red}{\text{时间：做的很快。独立思考}}$

### 9月17日

#### [1477. 找两个和为目标值且不重叠的子数组](https://leetcode.cn/problems/find-two-non-overlapping-sub-arrays-each-with-target-sum/)

**这道题的思路是前后缀分解。用$`pre[i]`$表示在$`i`$之前结束且和为$`k`$的最小长度。$`suf[i]`$表示在$`i`$开始或在$`i`$之后开始（反转一下就是以在$`i`$结束或在$`i`$之前结束）且和为$`k`$的最小长度。两个数组都可以用滑动窗口计算得到，最后的结果是$`min(pre[i]+suf[i])`$。$`pre[i]`$正序滑动窗口遍历，$`suf[i]`$逆序滑动窗口遍历。**

$\\color{red}{\text{时间：做了比较久。看了一点提示}}$

#### [15. 三数之和](https://leetcode.cn/problems/3sum/)

这道题的思路是双指针，排序之后固定第一个数，双指针指向第二个数和第三个数。如果三数之和等于$`target`$就加入结果中；如果三数之和小于$`target`$，左指针就右移；如果三数之和大于$`target`$，右指针就左移。一个关键的问题是去重问题，如果$`nums[i]==nums[i-1]`$，说明该数字重复应该跳过。当三数之和等于$`target`$时，$`nums[l]==nums[l-1]`$或者$`nums[r]==num[r+1]`$都会导致重复，应该跳过。

$\\color{red}{\text{时间：做的很快。去重部分看了一下题解}}$

#### [16. 最接近的三数之和](https://leetcode.cn/problems/3sum-closest/)

这道题和15题类似也是双指针。要维护一个数$`t=abs(nums[i]+nums[l]+nums[r]-target)`$。排序之后固定第一个数，计算$`t`$并更新答案。如果$`t==0`$，可以直接返回；如果$`nums[i]+nums[l]+nums[r]\gt target`$，右指针左移，如果$`nums[i]+nums[l]+nums[r]\lt target`$，左指针右移。最后返回答案

$\\color{red}{\text{时间：做的很快。独立思考}}$

### 9月18日

#### [1520. 最多的不重叠子字符串](https://leetcode.cn/problems/maximum-number-of-non-overlapping-substrings/)

**这道题首先要计算合法区间。先记录每个字符的起始位置和结束位置。然后对这些区间进行扩展，区间内部包含字符的起始及结束位置也要包含在里面，新扩展区间每个字符的起始和结束位置也要包含在里面。然后问题变成了从这些区间中，最多可以选多少个互不重叠的区间。按照右端点进行排序，不断记录新的右端点。另一种扩展区间的做法是有向图建模，如果$`a`$的区间中包含别的字符$`b`$，那么连一条从$`a`$到$`b`$的有向边。建模后，如果字串要包含第$`i`$个小写字母，就$`dfs`$这个有向图，所有能访问到的点的对应区间的并集，即为最终字串的下标区间。**

$\\color{red}{\text{时间：做了很久。扩展区间部分看了一下题解。}}$

#### [17. 电话号码的字母组合](https://leetcode.cn/problems/letter-combinations-of-a-phone-number/)

这道题是经典的回溯题，从第一个字符开始选择可能的字符，递归的选择下一个字符即能得到答案。可以用一个哈希表$`unordered\_map<int,string>`$存储数字对应的字母。

$\\color{red}{\text{时间：做的很快。独立思考}}$

#### [18. 四数之和](https://leetcode.cn/problems/4sum/)

这道题和三数之和特别类似。也是使用双指针。排序后固定第一个数和第二个数，双指针指向第三个数和第四个数。如果四数之和等于$`target`$就加入到结果中；如果四数之和小于$`target`$，左指针右移；如果四数之和大于$`target`$，右指针就左移。至于去重问题，如果$`i>0\&\&nums[i]==nums[i-1]`$，说明该数字重复应该跳过；如果$`j>i+1\&\&nums[j]==nums[j-1]`$，说明该数字重复应该跳过。当四数之和等于$`target`$时，$`nums[l]==nums[l-1]`$或者$`nums[r]==num[r+1]`$都会导致重复，都应该跳过。

$\\color{red}{\text{时间：15min。独立思考}}$

### 9月20日

#### [3498. 字符串的反转度](https://leetcode.cn/problems/reverse-degree-of-a-string/)

简单题。遍历每个字符，反转字母表的位置根据$`26-s[i]+'a'`$求，字符串的位置根据$`i+1`$求。最大结果$`26 \times 1000 \times 1000`$，未超过$`int`$。

$\\color{red}{\text{时间：1min33s。独立思考}}$

#### [21. 合并两个有序链表](https://leetcode.cn/problems/merge-two-sorted-lists/)

和合并两个有序数组类似，使用双指针，比较两个指针所在位置的大小。每次将较小的加入到结果中并移动它的指针。如果最后有个链表有剩余，把它们全部加入到结果中。看了题解发现有第二种方法，使用递归。如果$`list1[0] \lt list2[0]`$，最终是$`list1[0]+merge(list1[1:],list2)`$，其他情况则是$`list2[0]+merge(list1,list2[1:])`$。

$\\color{red}{\text{时间：第一种方法2min35s。独立思考}}$

#### [22. 括号生成](https://leetcode.cn/problems/generate-parentheses/)

这道题是回溯经典题目。具体的做法是在回溯过程中传递两个参数记录左括号和右括号的剩余数量$`cnt1`$和$`cnt2`$，只有当$`cnt1 \gt 0`$时，才能用左括号；只有当$`cnt2 \gt cnt1`$时，才能用右括号。最终如果$`cnt2==0`$就将其放入到结果中。

$\\color{red}{\text{时间：15min41s。结束条件看了一下题解}}$

### 9月21日

#### [3524. 求出数组的 X 值 I](https://leetcode.cn/problems/find-x-value-of-array-i/)

**这道题使用的是动态规划，定义$`dp[i][r]`$表示以索引$`nums[i-1]`$结尾且乘积模$`k`$等于$`r`$的子数组个数。从$`0`$到$`k-1`$枚举以$`nums[i-2]`$结尾的余数s，如果$`s*nums[i-1]\%k==r`$，$`dp[i][r]+=dp[i-1][s]`$。如果$`nums[i-1]\%k == r`$，则$`dp[i][r]++`$。最终统计$`res[k]= \sum_{1 \le i \le n} dp[i][k]`$。还可以用刷表法，在动态规划中，根据转移来源计算状态叫查表法，用当前状态更新其他状态叫刷表法。刷表法的意思是使用$`dp[i][r]`$的值可以贡献给$`dp[i+1][r \times (nums[i]\%k)\%k]`$。**

$\\color{red}{\text{时间：写了很久，看了一点提示。}}$

#### [23. 合并 K 个升序链表](https://leetcode.cn/problems/merge-k-sorted-lists/)

这道题最小堆的算法，先把头节点存入最小堆中，每次取最小的那个，如果它的$`next`$不为空，继续把它插入到堆中。另一种方法是分治法，把$`lists`$一分为二，先合并前一半的链表，再合并后一半的链表，然后把这两个链表合并成最终的链表。再另一种方法是迭代法，先两两合并，再四四合并，依次类推，直到所有链表都合并了。

$\\color{red}{\text{时间：最小堆10min左右。独立思考}}$

#### [24. 两两交换链表中的节点](https://leetcode.cn/problems/swap-nodes-in-pairs/)

这道题就是多次交换链表的两个元素，掌握了单词交换就能类推到整个链表。首先要记录当前指针$`cur`$，前一个指针$`pre`$，后一个指针$`nex`$。要交换当前指针和下一个指针的方法是：$`pre \rightarrow next=nex;nex \rightarrow next=cur;cur \rightarrow next=nex \rightarrow next;`$。然后令$`pre=cur;cur=cur \rightarrow next;nex=cur \rightarrow next;`$，继续下一个循环。另一种方法是递归，先交换$`nex`$为头节点的链表，然后把$`pre`$指向递归返回的链表头，然后把$`cur`$指向$`pre`$，最后返回$`cur`$。

$\\color{red}{\text{时间：5min39s。独立思考}}$

### 9月22日

#### [3525. 求出数组的 X 值 II](https://leetcode.cn/problems/find-x-value-of-array-ii/)

> [!TIP]
> 这道题和昨天的题区别是他要支持单点修改，且只能删除后缀。暴力做法是每次修改后统计所有的从 $`start`$ 开始的后缀乘积 $`mod k`$ 余数为 $`x`$ 的个数。但是这样的复杂度是 $`n \times q`$ ，会超时。需要使用线段树进行优化，后续有能力了可以再回过头来解决这道题。

$\\color{red}{\text{没有写出来}}$

#### [25. K 个一组翻转链表](https://leetcode.cn/problems/reverse-nodes-in-k-group/)

这道题首先要掌握反转整个链表的方法。定义三个指针$`pre=nullptr,cur=head,nex=cur \rightarrow next`$。遍历$`cur`$，令$`cur \rightarrow next=pre;pre=cur;cur=nex;`$，即可反转整个链表，最后$`pre`$指针和$`head`$指针分别是反转后链表的头指针和尾指针。$`k`$个一组反转要记录的是$`pre,head,nex`$，其中$`pre`$是第一个数的前一个，$`head`$是第一个数，$`nex`$是第$`k`$个数的后一个。先断开连接，然后调用反转整个链表的方法得到反转后的链表头尾指针，让$`pre`$指向反转后的头节点，然后令$`pre`$等于尾节点，$`head=nex`$，继续新一轮的循环。

$\\color{red}{\text{时间：写了很久。独立思考}}$

#### [26. 删除有序数组中的重复项](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)

左指针$`left`$指向去重后的最后一个元素，右指针$`right`$指向要处理的元素，如果$`nums[right]==nums[right-1]`$，忽略它；否则令$`nums[left++]=nums[right]`$。最后返回$`left`$即为去重后的个数

$\\color{red}{\text{时间：2min46s。独立思考}}$

### 9月23日

#### [1658. 将 x 减到 0 的最小操作数](https://leetcode.cn/problems/minimum-operations-to-reduce-x-to-zero/)

这道题的大意是让不重叠的前缀+后缀的和$`==x`$，且它们的个数最少。我的想法是因为都是正数，后缀和是单调递增的，可以用哈希表来存储位置$`i`$的后缀。而遍历时，正序遍历的同时计算前缀，查找哈希表中有没有目标值且其位置应该大于当前位置，有的话就可以更新答案。看了题解发现可以用逆向思维，前缀+后缀的和$`==x`$，等价于剩下的子数组$`==sum-x`$。所以题目变成了和为$`sum-x`$的最长子数组，因为没有负数，所以可以用滑动窗口解决，（有负数的话可以使用哈希表）

$\\color{red}{\text{时间：有想法了很快想出来了。独立思考}}$

#### [27. 移除元素](https://leetcode.cn/problems/remove-element/)

和[26. 删除有序数组中的重复项](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)类似，做指针$`left`$指向移除后的最后一个元素，右指针$`right`$指向要处理的元素，如果$`nums[right]==val`$，忽略它；否则令$`nums[left++]==nums[i]`$。最后返回$`left`$即为移除后的个数

$\\color{red}{\text{时间：很快。独立思考}}$

#### [28. 找出字符串中第一个匹配项的下标](https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/)

经典$`KMP`$算法，可以分为两步：求解前缀函数（$`next`$数组）+匹配。匹配过程除了用类似$`BF`$算法的回溯过程求，还可以将模式串+”#“+文本串的方式求解合并后的$`next`$数组，最后如果$`next`$数组的值等于模式串的长度即视为匹配成功。

$\\color{red}{\text{时间：很快。看了OI WIKI的KMP算法部分}}$

### 9月24日

#### [3550. 数位和等于下标的最小下标](https://leetcode.cn/problems/smallest-index-with-digit-sum-equal-to-index/)

依次判断数组中每个元素的数位和是否等于下标，如果等于直接返回结果。否则返回$`-1`$。

$\\color{red}{\text{时间：1min03s。独立思考}}$

#### [29. 两数相除](https://leetcode.cn/problems/divide-two-integers/)

因为不能使用$`long`$，乘法，除法和取余运算。这道题主要参考快速幂的方法，用加法快速得到乘法结果。然后使用二分法不断寻找符合条件的答案。注意要将所有的正数转化为负数，因为负数的表示范围更大，$`INT\_MIN`$没有对应的正数。要特判被除数是$`INT\_MIN`$，且除数是$`1`$的情况。

$\\color{red}{\text{时间：调试了很久。看了题解}}$

#### [30. 串联所有单词的子串](https://leetcode.cn/problems/substring-with-concatenation-of-all-words/)

**这道题我的想法是用哈希表记录$`words`$中所有单词的个数，然后遍历$`s`$中长度为$`m \times n`$的子字符串，将子字符串均分，也用哈希表记录其中的单词个数，判断和$`words`$的哈希表相不相等，如果相等就把它加入结果之中。看了题解之后发现可以用滑动窗口，根据第一个单词的起始位置不同，做不同的滑动窗口，最多要做$`wordlen`$次滑窗。每次定长滑窗有三步：枚举进入窗口的单词，把它的出现次数加一，可以用一个数字来记录过多的单词个数。更新答案，如果过多的单词个数等于$`0`$，把它加入答案。窗口最左边的单词离开窗口，减少其出现次数，如果符合要求了，就把过多变成符合要求。**

做了几道类似的题目：

+ [438. 找到字符串中所有字母异位词](https://leetcode.cn/problems/find-all-anagrams-in-a-string/)
+ [567. 字符串的排列](https://leetcode.cn/problems/permutation-in-string/)

$\\color{red}{\text{时间：我的想法做的很快。独立思考。滑窗方法看了一下题解}}$

### 9月28日

#### [1614. 括号的最大嵌套深度](https://leetcode.cn/problems/maximum-nesting-depth-of-the-parentheses/)

因为题目数据保证都是有效的括号字符串，所以遇到左括号的时候入栈顺便更新答案；遇到右括号的时候将栈顶元素出栈。

$\\color{red}{\text{时间：1min39s，独立思考}}$

#### [31. 下一个排列](https://leetcode.cn/problems/next-permutation/)

从右到左找到第一个$`nums[i] \lt nums[i+1]`$的位置$`i`$,然后从这个位置出发向右找到最后一个大于$`nums[i]`$的位置$`j`$。最后交换$`nums[i]`$和$`nums[j]`$，并将$`nums[i+1:-1]`$排序得到最终答案

$\\color{red}{\text{时间：思路想了很久，一直根据调试来改正自己的想法，独立思考}}$

#### [32. 最长有效括号](https://leetcode.cn/problems/longest-valid-parentheses/)

**这道题的关键点是栈中应该存什么。正确解答是应该存放不能被匹配的位置。当遇到左括号时，肯定不能匹配，存入栈中；当遇到右括号时，首先查看栈顶是否是左括号，是的话将先将左括号出栈，此时的栈顶元素是上一个未匹配的位置如果为空的话设置为$`-1`$，然后更新$`res=max(res,i-(st.empty()?-1:st.top()))`$；不是的话，说明这个右括号无法匹配，将其入栈。第二种方法遍历两次，是从左到右和从右到左各遍历一次，取最大值，遍历方法是到左括号个数等于右括号个数时更新答案，当右括号个数大于左括号个数时重置括号个数。第三种方法是将配对的位置置$`1`$，不匹配的位置置$`0`$，这道题就变成了[485. 最大连续 1 的个数](https://leetcode.cn/problems/max-consecutive-ones/)。**

$\\color{red}{\text{时间：看了一下题解}}$

### 9月30日

#### [33. 搜索旋转排序数组](https://leetcode.cn/problems/search-in-rotated-sorted-array/)

**这道题要想清楚一点就是$`mid`$将数组分成两部分，一定有其中一部分是有序的。如果$`target`$在有序区间内，将二分区间更新在有序区间内；否则就将二分区间更新在无序区间内。**

$\\color{red}{\text{时间：看到题目一开始没思路。看了一下题解}}$

#### [34. 在排序数组中查找元素的第一个和最后一个位置](https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array/)

这道题要我们手动实现$`lower\_bound()`$函数和$`upper\_bound()`$函数，$`lower\_bound()`$函数的实现方法是遇到小于的时候移动左指针，其他情况移动右指针，最后返回左指针。$`upper\_bound(x)`$函数其实就等价于$`lower\_bound(x+1)-1`$。

$\\color{red}{\text{时间：很快。之前了解过这两个函数如何进行转化}}$

### 10月8日

#### [1021. 删除最外层的括号](https://leetcode.cn/problems/remove-outermost-parentheses/)

这道题要记录三个变量，左括号的数量，右括号的数量和起始位置。当左括号的数量等于右括号的数量时就称其为原语。将原语去掉最外层括号加入答案中，同时更新起始位置。

$\\color{red}{\text{时间：非常快。独立思考。简单题}}$

#### [35. 搜索插入位置](https://leetcode.cn/problems/search-insert-position/)

二分搜索模板题，左指针指向$`0`$，右指针指向末尾。计算中点位置元素满不满足要求，满足要求直接返回结果；如果偏大，就把右指针变成$`mid-1`$；如果偏小，就把左指针变成$`mid+1`$。最后返回左指针就行。

$\\color{red}{\text{时间：非常快。独立思考。简单题}}$

#### [36. 有效的数独](https://leetcode.cn/problems/valid-sudoku/)

模拟题，分别判断行、列以及九宫格是否满足要求。使用$`unordered\_map`$来判断是否重复。

$\\color{red}{\text{时间：较快。独立思考。模拟过程有点繁琐}}$

### 10月9日

#### [1541. 平衡括号字符串的最少插入次数](https://leetcode.cn/problems/minimum-insertions-to-balance-a-parentheses-string/)

这道题我的想法是使用栈，遇到左括号入栈；遇到右括号，如果栈为空，补充一个左括号；栈不为空，将栈顶左括号顶出。然后看下一个元素是不是右括号，是的话将遍历下标跳转到$`i+2`$，不是的话补充一个右括号。最后返回补充的左右括号个数以及栈中剩余元素两倍的总和。

$\\color{red}{\text{时间：很快。独立思考。以后遇到左右括号匹配问题就用栈去模拟，万变不离其宗}}$

#### [37. 解数独](https://leetcode.cn/problems/sudoku-solver/)

回溯法，枚举每一个位置，如果该位置是$`'.'`$，就枚举可以填入的数字进行回溯。注意判断填入数字后数独是否有效只需要判断填入数字所在行，所在列，所在九宫格是否矛盾，不用判断整个数独。

$\\color{red}{\text{时间：看了一下题解}}$

#### [38. 外观数列](https://leetcode.cn/problems/count-and-say/)

我是迭代做的，如果当前元素和上一个元素相等，计数加$`1`$；否则就将其个数和数字加入结果中；最后别忘记将最后一个数的个数和数字也加入结果中。递归做的话，先写递归出口，$`n==1`$是直接返回$`“1”`$，然后从$`n-1`$去推导$`n`$的结果。

$\\color{red}{\text{时间：迭代方法做的很快。独立思考}}$

### 10月10日

#### [2333. 最小差值平方和](https://leetcode.cn/problems/minimum-sum-of-squared-difference/)

**$`k1`$和$`k2`$是等价的。先计算两个数组对应位置差值的绝对值，并排序。贪心地选择最大的数进行下降，如果有剩余，则完全降到该数；否则将其平均分到几个数中。**

相似题目：[1648. 销售价值减少的颜色球](https://leetcode.cn/problems/sell-diminishing-valued-colored-balls/)

$\\color{red}{\text{时间：贪心策略没有想到。看了一下题解}}$

#### [39. 组合总和](https://leetcode.cn/problems/combination-sum/)

选或不选思路：确定返回条件：下标遍历到数组最后或者总和超过了$`target`$或者总和等于$`target`$。不选第$`i`$个的话，递归到$`(i+1，left)`$；选第$`i`$个的话，递归到$`(i,left-candidates[i])`$。

枚举选哪个思路：在$`[i,n-1]`$中枚举要填在$`path`$中的元素$`candidates[j]`$，然后递归到$`(j,left-candidates[j])`$。

$\\color{red}{\text{时间：回溯经典题。做的很快}}$

#### [40. 组合总和 II](https://leetcode.cn/problems/combination-sum-ii/)

选或不选思路：确定返回条件：下标遍历到数组最后或者总和超过了$`target`$或者总和等于$`target`$。不选第$`i`$个的话，跳过后续所有等于 $`candidates[i]`$ 的数，递归到$`(i^{'},left)`$，其中$`[i,i^{'}-1]`$中的数都相同；选第$`i`$个的话，递归到$`(i+1,left-candidates[i])`$。

枚举选哪个思路：在$`[i,n-1]`$中枚举要填在$`path`$中的元素$`candidates[j]`$，然后递归到$`(j+1,left-candidates[j])`$，如果$`j \gt i\&\&candidates[j]==candidates[j-1]`$，则跳过，枚举下一个$`j`$。

$\\color{red}{\text{时间：回溯经典题。做的很快}}$

### 10月12日

#### [2897. 对数组执行操作使平方和最大](https://leetcode.cn/problems/apply-operations-on-array-to-maximize-sum-of-squares/)

| 数1  | 数2  | 与运算 | 或运算 |
| :--: | :--: | :----: | :----: |
|  0   |  0   |   0    |   0    |
|  0   |  1   |   0    |   1    |
|  1   |  0   |   0    |   1    |
|  1   |  1   |   1    |   1    |

**可以看到或运算把$`1`$都集中在一起，与运算把$`0`$集中在一起，且二进制$`1`$的个数不变。所以可以统计每个数位上二进制一的个数，然后贪心的让每个数最大。**

$\\color{red}{\text{一开始没思路，看了题解}}$

#### [41. 缺失的第一个正数](https://leetcode.cn/problems/first-missing-positive/)

遇到不在$`1 \sim n`$的数字时跳过，否则，如果和正确位置上的数字不相等就交换它们继续判断。最后遍历一次得到第一个不相等的位置返回，如果没有就返回$`n+1`$。看了题解发现还有一个更好的方法，先将负数变成$`n+1`$，然后遍历每一个数（取绝对值就是原本的数），如果在$`1 \sim n`$之间，将对应位置的数变成负数（不重复变）。最后遍历一次得到第一个正数的位置返回，如果都是负数就返回$`n+1`$。

$\\color{red}{\text{时间：做的很快，独立思考}}$

#### [42. 接雨水](https://leetcode.cn/problems/trapping-rain-water/)

方法一：前后缀分解（竖着计算面积），用两个数组分别记录其左侧的最大值和右侧的最大值。然后遍历每一个位置$`i`$，累加$`max(min(left[i],right[i])-height[i],0)`$。

方法二：单调栈（横着计算面积），找下一个更大元素，再找的过程中填坑。在出的时候累加。其中遍历到的是右挡板$`i`$，栈顶元素是底边$`h`$，出栈后的栈顶元素是左挡板$`l`$。则面积为$`(min(height[l],height[i])-height[h])*(i-l-1)`$

$\\color{red}{\text{时间：方法一做的很快，方法二看了题解才会写}}$

### 10月13日

#### [3727. 最大交替平方和](https://leetcode.cn/problems/maximum-alternating-sum-of-squares/)

将数组每个数字变成它们的平方，然后排序。让前一半数组作为奇数项，后一半数组作为偶数项可以得到最大的交替得分。

$\\color{red}{\text{时间：很快。独立思考}}$

#### [43. 字符串相乘](https://leetcode.cn/problems/multiply-strings/)

这道题前置是高精度加法和高精度一位数乘多位数。有了这些之后，选定一个作为乘数，用另一个数的每个数位去乘它，注意高位乘它要将其扩大对应的倍数（即在末尾加上$`0`$），然后再将结果加起来。

|      |      | $x_1$ | 9    | 5    | 4    | 7    |
| ---- | ---- | ----- | ---- | ---- | ---- | ---- |
| *    |      | $x_2$ |      | 3    | 2    | 8    |

---

|      |      | 7    | 6    | 3    | 7    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
|      | 1    | 9    | 0    | 9    | 4    |      |
| 2    | 8    | 6    | 4    | 1    |      |      |

---

| 3    | 1    | 3    | 1    | 4    | 1    | 6    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |

$\\color{red}{\text{时间：这道题比较繁琐，但是每一步都知道自己在干什么，很快就写出来了。}}$

#### [44. 通配符匹配](https://leetcode.cn/problems/wildcard-matching/)

这道题和[10. 正则表达式匹配](https://leetcode.cn/problems/regular-expression-matching/)特别相似。$`dp[i][j]`$代表字符串$`s`$的前$`i`$个字符和$`p`$的前$`j`$个字符能否匹配。当$`p[j-1]=='*'`$时，$`dp[i][j] = dp[i][j]||dp[k][j-1]`$，其中$`0\le k\le i`$，我使用的优化思路是前缀和。当$`p[j-1]!='*'`$时，$`dp[i][j]=dp[i-1][j-1]\&\& match(s[i-1],p[j-1])`$。初始化如下：$`dp[0][0]=true;if(p[j-1]='*'\&\& p[0:j-1]=='*'){dp[0][j]=ture; }`$。题解的优化思路如下，当$`p[j-1]=='*'`$时：

|          |  0   |$\ldots$|                          j-1                           |  j   |
| :------: | :--: | :----: | :----------------------------------------------------: | :--: |
|    0     |      |        |    $\\color{red}{\text{y}}\\color{green}{\text{x}}$    |      |
| $\vdots$ |      |        |    $\\color{red}{\text{y}}\\color{green}{\text{x}}$    |      |
|   i-1    |      |        |    $\\color{red}{\text{y}}\\color{green}{\text{x}}$    |  y   |
|    i     |      |        |               $\\color{green}{\text{x}}$               |  x   |

$dp[i-1][j]=dp[0][j-1]|| \dots ||dp[i-1][j-1]$

$dp[i][j]=dp[0][j-1]|| \dots ||dp[i-1][j-1]||dp[i][j-1]$

$dp[i][j]=dp[i-1][j]||dp[i][j-1]$

$\\color{red}{\text{时间：独立完成，很快}}$

## 计划调整

力扣每日一题+题库按顺序3题。多加一题，要是遇到困难题想太久可以只做两题。

### 10月14日

#### [3723. 数位平方和的最大值](https://leetcode.cn/problems/maximize-sum-of-squares-of-digits/)

和固定，将数值尽量集中在少数数位上能获得最大的平方和。所以遍历每一个数位，该数位就填$`min(9,left)`$并记录在结果字符串中。最后如果$`left`$还有剩余，直接返回空字符串；否则返回结果字符串。

$\\color{red}{\text{时间：独立完成，很快}}$

#### [45. 跳跃游戏 II](https://leetcode.cn/problems/jump-game-ii/)

我先做了一下这道题的前置[55. 跳跃游戏](https://leetcode.cn/problems/jump-game/)，每次都维护最远可以达到的距离，如果当前下标大于最远可以达到的距离就返回$`false`$，最后返回$`true`$。我想到的方法是动态规划，使用刷表法，到达一个位置后，该位置能到达的下一个位置都是该位置的步数$`+1`$，即$`dp[cur+j]=min(dp[cur+j],dp[cur]+1)`$，其中$`1 \le j \le nums[cur]`$。但是这样的复杂度太高了，是$`o(n \times k)`$。另一种方法则也是维护最远可以达到的距离，当到达最远可以达到的距离后就将步数加$`1`$，同时更新最远可以达到的距离，这样复杂度就是$`o(n)`$了。

$\\color{red}{\text{时间：动态规划独立思考，很快。贪心法看了题解学习}}$

#### [46. 全排列](https://leetcode.cn/problems/permutations/)

这道题是排列问题。组合问题的做法是每个元素选或不选/枚举选哪个两种做法，如果有重复元素要先排序，选或不选做法的去重方法为如果不选$`nums[i]`$则跳过后续所有等于$`nums[i]`$的数，枚举选哪个的去重方法为在$`[i,n-1]`$中选一个$`nums[j]`$，跳过$`j \gt i\&\& nums[j]==nums[j-1]`$的数；而排列问题的做法是用一个数组记录哪些位置已经被用了。当被用了的数字为$`n`$时将结果加入。从$`0`$开始遍历数组，找到一个未被用的数字作为当前位置，同时修改它为已被使用，最后继续递归，递归完后恢复现场。

$\\color{red}{\text{时间：想了一会，一开始没有想到vis数组导致卡了一会}}$

#### [47. 全排列II](https://leetcode.cn/problems/permutations-ii/)

这道题是排列问题的有重复数字的情况。重点是去重，如果$`nums[i]!=nums[i-1]`$，那么可以随便填。如果$`nums[i]==nums[i-1]`$，如果$`nums[i-1]`$没有填入排列，为了避免重复，不能填$`nums[i]`$，后续所有等于$`nums[i]`$的数都不能填；如果$`nums[i-1]`$已经填入排列，那么可以随便填$`nums[i]`$。

$\\color{red}{\text{时间：不知道怎样去重，看了题解。}}$

### 10月15日

#### [2913. 子数组不同元素数目的平方和 I](https://leetcode.cn/problems/subarrays-distinct-element-sum-of-squares-i/)

这道题是简单版本，数组长度最大才$`100`$。我用的是方法是遍历每个子数组并统计不同计算。用两个循环，一个作为左端点，一个作为右端点，在遍历的同时使用set记录子数组中不同元素的个数并加入到数组中。但是这样复杂度为$`O(n^2)`$，在数据范围过大时会超时。看了题解发现有更好的方法，对于子数组问题，使用**增量法**思考，我们可以考虑按照其末尾字符的下标进行分组，对于两组相邻的字串：以$`s[i]`$结尾的字串可以看作是以$`s[i-1]`$结尾的字串在末尾添加上$`s[i]`$组成。如果$`s[i]`$之前没遇到过，这些子数组的不同计数都会增加$`1`$，不同计数的平方之和增加量为$`\sum_{j=0}^{i-1} {(x_j+1)^2-(x_j)^2=2x_j+1}`$。如果$`s[i]`$之前遇到过，设其上次出现的下标为$`j`$，对于子数组$`s[0:j,i-1]`$，这些子数组的不同计数是不会变化的，对于子数组$`s[j+1:i-1,i-1]`$，这些子数组的不同计数都会增加$`1`$，不同计数的平方之和增加量为$`\sum_{k=j+1}^{i-1} {(x_k+1)^2-(x_k)^2=2x_k+1}`$。所以需要这样一个数据结构：$`f[k]`$表示左端点为$`k`$的子数组的不同计数；能够实现区间加一操作；能够计算区间元素和操作。所以可以使用线段树方法。

做了几道这题的简单版本：
+ [2262. 字符串的总引力](https://leetcode.cn/problems/total-appeal-of-a-string/)：贡献法/增量法都可做。这道题贡献法可以考虑每个$`s[i]`$的贡献，对于重复字符，只考虑第一个字符的贡献。设$`s[i]`$上一次出现的下标为$`last[s[i]]`$，不存在则为$`-1`$。那么字串的左端点可以为$`[last[s[i]:i]`$，字串的右端点可以为$`[i:n-1]`$。所以$`s[i]`$的贡献是$`(i-last[s[i]]) \times (n-i)`$
+ [828. 统计子串中的唯一字符](https://leetcode.cn/problems/total-appeal-of-a-string/)：增量法

$\\color{red}{\text{时间：遍历方法较快写完，独立思考}}$

#### [48. 旋转图像](https://leetcode.cn/problems/rotate-image/)

先将行首尾互换，然后沿着对角线互换。

$\\color{red}{\text{时间：很快，独立思考}}$

#### [49. 字母异位词分组](https://leetcode.cn/problems/group-anagrams/)

这道题使用哈希表，将每个字符串排序后作为键，存在哈希表$`unordered\_map<string,vector<string>>`$中，最后遍历哈希表，将每个键对应的值加入到结果中返回即可。

$\\color{red}{\text{时间：很快，独立思考}}$

#### [50. Pow(x, n)](https://leetcode.cn/problems/powx-n/)

这道题是快速幂模板题。要注意几个细节：当指数为负数时，使用$`mypow(1/x,-n)`$来计算误差太大，应该使用$`1/mypow(x,-n)`$；然后是要注意当n为$`-2^{31}`$时没有对应的整数，所以应该用$`long~long`$存储。快速幂的做法是每次计算其二进制位上是否是$`1`$，是的话加上相对应的值。还可以用递归的方法，$`mypow(x,n)=mypow(x,n/2)*mypow(n/2)*(n\%2==1?x:1)`$

$\\color{red}{\text{时间：没有注意细节，导致写了很久才AC}}$

### 10月16日

#### [2916. 子数组不同元素数目的平方和 II](https://leetcode.cn/problems/subarrays-distinct-element-sum-of-squares-ii/)

> [!TIP]
> 思路是昨天每日一题[2913. 子数组不同元素数目的平方和 I](https://leetcode.cn/problems/subarrays-distinct-element-sum-of-squares-i/)的想法，但是目前我还不会使用线段树，所以暂时写不出来，后续有时间可以学一下线段树和树状数组

$\\color{red}{\text{没有写出来}}$

#### [51. N 皇后](https://leetcode.cn/problems/n-queens/)

这道题看上去很简单，但是做起来要想到很多东西。有三种想法：子集枚举：从$`n^2`$个格子中选一个子集，使得子集中恰好有$`n`$个格子，且满足题目限制；组合枚举：从$`n^2`$个各自中选择$`n`$个，且满足题目限制；排列枚举：所有行中皇后的列号正好构成一个$`1`$到$`n`$的排列。我做的时候想到的是组合枚举。但是有一堆重复答案，然后一直思考，发现是填入的顺序没有限制，于是就使用两个参数表示最后一个填入的位置，后续填入的位置要在这个位置后面，于是就得到了正确答案。后来看题解发现可以使用行号来规定填入的顺序，而且此时判断有效只需判断列，左上以及右上部分。

$\\color{red}{\text{时间：写了很久。独立思考}}$

#### [52. N 皇后 II](https://leetcode.cn/problems/n-queens/)

和[51. N 皇后](https://leetcode.cn/problems/n-queens/)的区别是：这道题只需要输出答案的个数，而[51. N 皇后](https://leetcode.cn/problems/n-queens/)需要输出每个方案。

$\\color{red}{\text{时间：写了51题之后，52题的代码可以照搬，改加入答案部分即可}}$

#### [53. 最大子数组和](https://leetcode.cn/problems/maximum-subarray/)

这道题我的做法是动态规划，$`dp[i]`$表示以$`nums[i]`$结尾的最大子数组和。那么$`dp[i]=max(dp[i-1]+nums[i],nums[i])`$，并在遍历的过程中更新结果$`res=max(res,dp[i])`$。

第二种做法是把子数组的元素和转化为两个前缀和的差，当遍历到数$`nums[i]`$时，其前缀和固定，要找到前面最小的前缀和相减。而且由于子数组不能为空，所以应该先计算$`sum[i]-minpre`$，其中$`minpre=min_{k=0}^{i-1} sum[k]`$，再更新最小前缀和$`minpre=min(minpre,sum[i])`$。

第三种做法是分治法，我们可以把数组对半分为两部分，最大子数组和有三种情况，只在左半数组，只在右半数组，跨左右两个数组。我们使用分治法计算只在左半数组和右半数组的情况，然后单独计算跨左右两个数组的情况，最后取这三种情况的最大值即可。

$\\color{red}{\text{时间：方法一很快写完}}$

### 10月19日

#### [2089. 找出数组排序后的目标下标](https://leetcode.cn/problems/find-target-indices-after-sorting-array/)

我的做法是使用$`lower\_bound`$函数找到第一个$`\ge target`$的位置$`left`$，使用$`upper_bound`$函数找到第一个$`\gt target`$的位置$`right`$，结果就是$`[left,right)`$。看了题解发现还有只用遍历$`O(n)`$的方法也能解决，设$`\le target`$的个数为$`cnt_1`$，$`== target`$的个数为$`cnt_2`$，结果就是$`[cnt_1,cnt_1+cnt_2)`$。

$\\color{red}{\text{时间：很快，简单题}}$

#### [54. 螺旋矩阵](https://leetcode.cn/problems/spiral-matrix/)

要记录上下左右四个方向的墙和行进的方向。注意初始化，初始化方向为向右，初始化坐标为$`(0,-1)`$，初始化上面的墙为$`1`$。过程是根据方向来移动坐标，如果碰到了墙，就更新墙的位置并改变方向。然后将当前元素加入到结果中。

$\\color{red}{\text{时间：较快，之前做的还有点印象}}$

#### [55. 跳跃游戏](https://leetcode.cn/problems/jump-game/)

维护最远可以达到的距离，按顺序遍历每一个元素，先判断当前下标是否大于最远距离，如果$`i \gt maxnum`$，直接返回$`false`$；否则更新能到达的最远距离。若是遍历完还没有返回就返回$`true`$。

$\\color{red}{\text{时间：很快。10月14日做45题的时候顺便做了这题}}$

#### [56. 合并区间](https://leetcode.cn/problems/merge-intervals/)

方法一：排序。将区间按照**左端点**升序排序，则能合并的区间必然相邻。根据[836. 矩形重叠](https://leetcode.cn/problems/rectangle-overlap/)，我们知道两区间相交的充要条件是$`max(l_1,l_2) \le min(r_1,r_2)`$，我们按照左端点排序后，只需判断$`l_2 \le r_1`$即可，因为$`l_1 \le l_2 \le r_2`$已经成立。具体做法是记录两个变量$`start`$和$`end`$。当遍历到一个区间时，如果这个区间的左端点小于等于$`end`$，说明可以合并，更新$`end`$；否则不能合并，将合并后的区间写入结果中，并更新$`start`$和$`end`$。

方法二：差分数组。对于区间$`[start,end]`$，把$`cnt[start],cnt[start+1],\ldots,cnt[end]`$都增加1.最终满足$`cnt[i] \gt 0`$的连续下标就是合并后的区间。注意这样会把区间$`[1,2]`$和$`[3,4]`$错误合并，所以解决方法是把区间左右端点乘以2进行合并，最后将得到的结果左右区间除以2即可。

方法三：扫描线。如果垂线遇到左端点$`start`$，把$`cnt`$加$`1`$。如果加之前$`cnt=0`$，说明开始了一段新的合并区间，$`start`$是合并后的区间左端点。如果垂线遇到右端点$`end`$，把$`cnt`$减$`1`$。如果减之后$`cnt=0`$，说明$`end`$是合并后的区间右端点。

$\\color{red}{\text{时间：方法一debug了好久，较快完成。方法二和方法三看了题解后也较快写出来了}}$

### 10月20日

#### [3886. 可排序整数求和](https://leetcode.cn/problems/sum-of-sortable-integers/)

**要让整个数组是递增的，要满足：分割后每个子数组都递增；每个子数组的最小值$`\ge`$上一个子数组的最大值。循环有序的条件是：子数组本来就是递增的，或者子数组由两个递增段组成，且第一段的最小值$`\ge`$第二段的最大值。具体的流程如下：首先预处理每个位置的下一个递减的位置。记录上一个区间的最大值$`last\_max`$，初始化为$`0`$。对于每个子数组，如果左端点的下一个递减位置在右端点的右边，说明这个子数组已经有序了，只需满足左端点的值$`\ge last\_max`$，然后更新$`last\_max`$为右端点的值；如果左端点的下一个递减位置在数组中间位置$`m`$，则必须满足：$`m`$位置下一个递减的位置大于等于右端点（保证右边有序），$`nums[l]>=nums[r]`$（保证子数组能够循环有序），$`nums[m+1] \ge last\_max`$（保证整个数组有序）。**

$\\color{red}{\text{时间：开始没有想法，后来看了题解后写出来了。从这道题中可以学到循环有序的判断方法}}$

#### [57. 插入区间](https://leetcode.cn/problems/insert-interval/)

延续[56. 合并区间](https://leetcode.cn/problems/merge-intervals/)的思路，先将区间按左端点升序排序。然后分情况讨论。遍历到一个区间时，
1. 如果新区间的左端点大于这个区间的右端点，说明新区间在这个区间的右边，不重叠，直接加入答案；
2. 如果新区间的右端点小于这个区间的左端点，说明新区间在这个区间的左边，不重叠，直接加入答案；
3. 否则的话，有重叠，更新合并区间后的左右端点。当第一次遇到第二种情况时将合并后的区间加入答案。

$\\color{red}{\text{时间：较快完成，做了56题后再做这题还是比较简单的。}}$

#### [58. 最后一个单词的长度](https://leetcode.cn/problems/length-of-last-word/)

简单题简单做，倒序遍历，先排除掉前导空格，然后累加字母的个数直到下一个空格。

$\\color{red}{\text{时间：很快，简单题}}$

#### [59. 螺旋矩阵 II](https://leetcode.cn/problems/spiral-matrix-ii/)

这道题是[54. 螺旋矩阵](https://leetcode.cn/problems/spiral-matrix/)的后置题，但是解答过程完全类似，唯一不同的点是将其还原成二维数组。照搬其代码并改一下输出即可。

$\\color{red}{\text{时间：很快，有了54题的基础，这道题没有什么难度。}}$

### 10月21日

#### [3863. 将一个字符串排序的最小操作次数](https://leetcode.cn/problems/minimum-operations-to-sort-a-string/)

这道题主要考察的是分析问题的能力，首先可以知道答案只可能是$`-1`$次，$`0`$次，$`1`$次，$`2`$次或者$`3`$次。
1. 当数组本身就是有序时，不需要交换，次数为$`0`$；
2. 当数组长度为2时，不可能交换成功，返回$`-1`$；
3. 找到第一个最小值的下标和最后一个最大值的下标。如果其中至少有一个在正确位置，只需交换$`1`$次
4. 如果最小值下标在最后一个位置，最大值下标在第一个位置，则需要交换$`3`$次。
5. 其余情况需要交换$`2`$次

$\\color{red}{\text{时间：较快。刚开始有些情况没考虑进去，debug了一会。}}$

#### [60. 排列序列](https://leetcode.cn/problems/permutation-sequence/)

递归做法，根据k不断确定当前位的值，使用一个数组记录每一个元素是否被使用过。返回条件是当$`k==1`$时，按顺序返回当前剩余的数字，否则的话计算未确立数字的全排列个数，以此来确立下一个数字，并减小相应的$`k`$值。

$\\color{red}{\text{时间：刚开始思路不是很清晰，做了好久。独立思考。}}$

#### [61. 旋转链表](https://leetcode.cn/problems/rotate-list/)

将链表每个节点向右移动$`k`$个位置等价于在第$`n-k\%n`$位置处断开，然后再将尾指针指向头指针。因此关键是求整个链表长度（可用遍历法）以及第$`n-k\%n`$位置（可以快慢指针）。具体操作如下，先让快指针走$`k`$步，那么快指针走到$`n`$时，慢指针刚好比他慢$`k`$步，在$`n-k\%n`$的位置。

$\\color{red}{\text{时间：较快。求链表长度+求第k个节点。快慢指针的方法已经掌握的比较熟练了。独立思考}}$

#### [62. 不同路径](https://leetcode.cn/problems/unique-paths/)

动态规划入门题。（初学$`DP`$推荐从记忆化搜索开始，先了解有哪些常见的$`DP`$题目，用记忆化搜索完成这些常见题型。之后，用递推写法再刷一遍这些题目。）

方法一：记忆化搜索。记忆化搜索的原理是减少重复递归调用的计算次数。如果一个状态（递归入参）是第一次遇到，那么可以在返回前，把状态及其结果记到一个$`memo`$数组中。如果一个状态不是第一次遇到（$`memo`$中保存的结果不等于$`memo`$的初始值），那么可以直接返回$`memo`$中保存的结果。递归入口:$`dfs(m-1,n-1)`$，递归边界：$`dfs(-1,j)=dfs(i,-1)=0,dfs(0,0)=1`$，转移方程：$`dfs(i,j)=dfs(i-1,j)+dfs(i,j-1)`$

方法二：传统动态规划，转移方程：$`dp[i][j]=dp[i-1][j]+dp[i][j-1]`$，返回值：$`dp[m-1][n-1]`$，初始化$`if(i==0||j==0) dp[i][j]=1`$

方法三：空间优化，可以只用一维数组记录，转移方程：$`if(j \gt 0) dp[j]+=dp[j-1]`$，初始化$`dp[0]=1`$，最后返回$`dp[n-1]`$即可。

$\\color{red}{\text{时间：经典题，方法二写的很快，独立思考。}}$

### 10月22日

#### [3942. 排序排列的最少操作数](https://leetcode.cn/problems/minimum-operations-to-sort-a-permutation/)

在[3886. 可排序整数求和](https://leetcode.cn/problems/sum-of-sortable-integers/)中，我学会了如何判断循环有序的方法。这道题需要分类讨论：循环递增或是循环递减。判断循环递增的过程如下，找出递减位置的个数，如果递减位置的个数等于$`0`$个，说明数组已经有序，可以直接返回$`0`$，如果递减位置的个数等于$`1`$个且第一段的最小值大于第二段的最大值，说明是循环递增的，找到这个位置$`a`$，可以将其左移$`a`$次变得有序，还可以先逆序再左移$`(n-a)`$次最后逆序，所以操作次数是$`min(a,n-a+2)`$。判断循环递减的过程同理。

$\\color{red}{\text{时间：想了挺久的，看了一点提示。}}$

#### [63. 不同路径 II](https://leetcode.cn/problems/unique-paths/)

动态规划入门题。[62. 不同路径](https://leetcode.cn/problems/unique-paths/)的进阶题。

方法一：记忆化搜索。递归入口：$`dfs(n-1,m-1)`$，递归边界：$`if(i \lt 0||j \lt 0||obstacleGrid[i][j]==1) dfs(i,j)=0, dfs(0,0)=1`$，转移方程：$`dfs(i,j)=dfs(i-1,j)+dfs(i,j-1)`$

方法二：传统动态规划。转移方程：$`if(obstacleGrid[i][j]==0) dp[i][j]=dp[i-1][j]+dp[i][j-1]`$，返回值：$`dp[n-1][m-1]`$，初始化：第一行找到第一个障碍物的位置，其前面的都赋值为$`1`$，第一列找到第一个障碍物的位置，其前面的都赋值为$`1`$。

方法三：空间优化。可以只用一维数组记录，转移方程：如果当前位置是障碍物的话，$`dp[i][j]=0`$，否则的话$`if(j \gt 0) dp[j]+=dp[j-1]`$，初始化：第一行找到第一个障碍物的位置，其前面的都赋值为$`1`$，最后返回$`dp[m-1]`$即可。

$\\color{red}{\text{时间：有了62题的基础三种方法做起来很快。独立思考}}$

#### [64. 最小路径和](https://leetcode.cn/problems/minimum-path-sum/)

这道题同样三种方法：记忆化搜索，传统动态规划和空间优化。这里只写核心转移方程。$`dp[i][j]=min(dp[i-1][j],dp[i][j-1])+grid[i][j]`$

$\\color{red}{\text{时间：三种方法，写的较快。独立思考}}$

#### [65. 有效数字](https://leetcode.cn/problems/valid-number/)

这道题改吐了。我的想法是拆分为三个函数：是否是整数，是否是小数，是否是指数。最后返回它们三个或的结果即可。其中最难的是小数的判断。注意只有一个小数点或者只是符号位加小数点并不是小数。只有当小数点前面是整数或者符号位，小数点后面是数位时才是小数。指数的判断如下：判断$`e`$或$`E`$前面的数可以是整数或者小数，后面的数只能是整数，注意如果$`e`$或$`E`$前面的数或后面的数有一个为空时则不是指数。**看了题解发现还有状态机，正则表达式的方法。**

$\\color{red}{\text{时间：改了非常久，不想在做第二遍了。独立思考}}$

### 10月23日

#### [3644. 排序排列](https://leetcode.cn/problems/maximum-k-to-sort-a-permutation/)

**这道题没想到解法，看了题解发现是脑筋急转弯：答案是所有不在正确位置上的数字的$`AND`$值。**

$\\color{red}{\text{时间：没有思路，看了题解}}$

#### [66. 加一](https://leetcode.cn/problems/plus-one/)

延续[43. 字符串相乘](https://leetcode.cn/problems/multiply-strings/)中高精度加法的思路，这道题相当于将数组加$`1`$。具体做法是倒序遍历数组，计算当前位$`(in+digits[i])\%10`$和进位$`(in+digits[i])/10`$，将当前位加入结果中。不要忘记将最后的进位加入结果，然后翻转结果即可。

$\\color{red}{\text{时间：很快。高精度加法模板题}}$

#### [67. 二进制求和](https://leetcode.cn/problems/add-binary/)

和[66. 加一](https://leetcode.cn/problems/plus-one/)类似，也是高精度加法，相当于两个高精度二进制数字相加。具体做法是倒序遍历两个字符串，计算当前位的和$`(a[i]-'0'+b[j]-'0'+in)\%2`$以及进位$`(a[i]-'0'+b[j]-'0'+in)/2`$，将当前位加入结果中。不要忘记将最后的进位加入结果，然后翻转结果即可。

$\\color{red}{\text{时间：很快。高精度加法模板题}}$

#### [68. 文本左右对齐](https://leetcode.cn/problems/text-justification/)

模拟题，记录每一行的开始位置$`start`$，已经加入的总长度$`sum`$。然后遍历数组，如果总长度再加上当前长度超过了最大长度限制，就将结果加入一行，然后重新开始计数。这道题的难点是格式化，如果这一行只有一个单词，就用空格补齐到最大长度。否则的话计算总的空格数量和单词间隔个数，然后将这些空格数量平均分配个所有单词间隔，如果不能均分，左边的空格应该多$`1`$。还要注意最后一行单词间只需一个空格，然后把它补齐到最大长度。

$\\color{red}{\text{时间：做了蛮久的，主要模拟有点费时间，写出来后没有什么bug，一次通过。}}$

### 10月25日

#### [1254. 统计封闭岛屿的数目](https://leetcode.cn/problems/number-of-closed-islands/)

这道题要求被水包围的陆地个数。我的做法是在四个边界处执行搜索，排除掉和边界连通的陆地，最后在计算内部陆地的连通量。第二种方法是把最外面一圈视为边界，如果在搜索过程中到达了边界，就意味着不是封闭岛屿。注意就算到达了边界，也要遍历完不能中途退出。这里边界可以按照如下方式遍历：如果是第一行和最后一行，访问所有格子；如果不是，只访问第一列和最后一列的格子。

$\\color{red}{\text{时间：很快，图的遍历还是比较熟练的。独立思考。}}$

#### [69. x 的平方根 ](https://leetcode.cn/problems/sqrtx/)

二分查找答案，注意$`right`$最大应该取$`46430`$防止溢出。当$`mid \times mid \le x`$时移动左端点；当$`mid \times mid \ge x`$时移动右端点，最后返回左端点减一。

$\\color{red}{\text{时间：很快。独立思考。一开始只是循环遍历，后来发现答案有单调性，所以使用二分算法降低事件复杂度。}}$

#### [70. 爬楼梯](https://leetcode.cn/problems/climbing-stairs/)

动态规划入门题。从记忆化搜索到动态规划最后空间优化一步步思考。这题的转移方程为$`dp[i]=dp[i-1]+dp[i-2]`$。空间优化可以只记录两个数：上一个数和上上一个数，不断计算再更新。看了题解发现还有快速幂的做法：
```math
\begin{bmatrix}f[i]\\f[i-1]\end{bmatrix} = \begin{bmatrix}1&1\\1&0\end{bmatrix} \begin{bmatrix}f[i-1]\\f[i-2]\end{bmatrix}
```
把上式中的三个矩阵分别记作 $`F[i],M,F[i−1]`$,那么有$`F[i]=M \times F[i-1]=M^n \times F[0]`$。然后我们可以使用快速幂来计算$`M^n`$。

$\\color{red}{\text{时间：很快。独立思考。动态规划入门}}$

#### [71. 简化路径](https://leetcode.cn/problems/simplify-path/)

简单栈的模拟。以$`/`$分割字符串，当前的字符串是$`".."`$时，如果栈不为空，将栈顶元素弹出。当前字符串不是空且不是$`"."`$，将其压入栈中，最后遍历栈中元素。**可以用$`vector`$来模拟栈，这样可以在最后遍历时从栈底开始遍历**。

$\\color{red}{\text{时间：很快。独立思考。}}$

### 10月26日

#### [3619. 总价值可以被 K 整除的岛屿数目](https://leetcode.cn/problems/count-islands-with-total-value-divisible-by-k/)

这道题也是图的搜索问题，在搜索的同时记录总和，最后判断是否可以被$`k`$整除。注意总和要用$`long~long`$记录防止溢出

$\\color{red}{\text{时间：很快，图的搜索模板题。独立思考。}}$

#### [72. 编辑距离](https://leetcode.cn/problems/edit-distance/)

动态规划题，重点是想清楚转移方程。如果是删除元素，$`dp[i][j]=dp[i-1][j]+1`$；如果是替换元素，$`dp[i][j]=dp[i-1][j-1]+1`$；如果是插入元素，$`dp[i][j]=dp[i][j-1]+1`$；初始化时，$`dp[0][i]=i`$（只能通过插入），$`dp[i][0]=i`$（只能通过删除）。

$\\color{red}{\text{时间：转移方程的书写想了一会，独立思考。}}$

#### [73. 矩阵置零](https://leetcode.cn/problems/set-matrix-zeroes/)

我一开始的想法是使用一个长度为$`m+n`$的数组记录某一行或者某一列是否有$`0`$，然后将有$`0`$的行或列全置为$`0`$。看了题解后发现遍历时可以通过判断当前元素所在行或所在列是否有$`0`$来置$`0`$。我的想法空间复杂度是$`O(n+m)`$。题解中的做法是使用原数组第一行和第一列来充当这个记录数组的角色。但是要额外去判断第一行和第一列。这样时间复杂度就是$`O(1)`$了。

$\\color{red}{\text{时间：O(1)空间复杂度方法看了一下题解}}$

#### [74. 搜索二维矩阵](https://leetcode.cn/problems/search-a-2d-matrix/)

二分搜索，我的想法是使用一次二分确定行，再使用一次二分确定列。这样需要两次二分。看了题解发现还有一次二分的做法，可以把二维矩阵拉成一维数组即把矩阵每一行拼在一起，具体的$`a[i]=matrix[i/n][i~mod~n]`$。这样一次遍历就能找到答案了。

$\\color{red}{\text{时间：两次遍历很快写完，独立思考。}}$

### 10月27日

#### [3963. 构造恰好一条路径的网格](https://leetcode.cn/problems/create-grid-with-exactly-one-path/)

这道题是一道构造题，只需要找到一条唯一的路径即可。一种做法是先往右走到最右端，然后往下走到最左端。

$\\color{red}{\text{时间：很快，简单题。独立思考。}}$

### 10月28日

#### [3882. 网格图中最小异或路径](https://leetcode.cn/problems/minimum-xor-path-in-a-grid/)

