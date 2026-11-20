### 11月1日

#### [453. 最小操作次数使数组元素相等](https://leetcode.cn/problems/minimum-moves-to-equal-array-elements/)

这道题要学会转换，$`n-1`$个元素都加一的效果是只有一个元素减一，所以最少次数是让每个元素都减到这个数组的最小值。遍历两次，第一次找最小值，第二次计算每个元素和最小值的差值。

$\\color{red}{\text{时间：很快。独立思考。想到转化了就不难}}$

#### [87. 扰乱字符串](https://leetcode.cn/problems/scramble-string/)

**区间$`dp`$做法，定义$`dp[i][j][len]`$为$`s_1`$以$`i`$开始，长度为$`len`$的子字符串和$`s_2`$以$`j`$开始，长度为$`len`$的子字符串是否互为扰乱字符串。当长度为$`1`$时，直接判断字符是否相等。当长度大于$`1`$时，枚举分割位置$`k`$，则$`dp[i][j][len]=(dp[i][j][k]\&\&dp[i+k][j+k][len-k])||(dp[i][j+len-k][k]\&\&dp[i+k][j][len-k])`$。注意要先枚举$`len`$这一层，确保我们转移所需要的状态都已经被计算好。**

$\\color{red}{\text{没做出来，看了题解。}}$

#### [88. 合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/)

这道题可以使用双指针，但是我做的时候使用了额外的空间来保存$`nums1`$，更高效的做法是倒序遍历就可以省下这个额外空间。

$\\color{red}{\text{时间：很快。独立思考。O(1)空间复杂度看了题解才想明白。}}$

#### [89. 格雷编码](https://leetcode.cn/problems/gray-code/)

**方法一：公式法：格雷码$`G_i`$的计算公式如下：$`G_i=i⊕(i/2)`$。方法二：构造法，已知$`G_{n-1}`$，先把$`G_{n-1}`$复制一份然后再最高位添加一位$`0`$，记为$`G^{'}_{n-1}`$。然后将$`G_{n-1}`$镜像再最高添加一位$`1`$，记为$`G^{''}_{n-1}`$。则$`G_n`$为$`G^{'}_{n-1}+G^{''}_{n-1}`$**。

$\\color{red}{\text{看了题解}}$

### 11月2日

#### [462. 最小操作次数使数组元素相等 II](https://leetcode.cn/problems/minimum-moves-to-equal-array-elements-ii/)

一次操作一个元素加一或者减一，让所有元素相等需要的最小操作数是当所有元素为数组中位数时，所以这道题首先需要排序找到中位数，然后再遍历计算每一个数和中位数差值的绝对值。

$\\color{red}{\text{时间：很快。独立思考。想到转化了就不难}}$

#### [90. 子集 II](https://leetcode.cn/problems/subsets-ii/)

这题是[78. 子集](https://leetcode.cn/problems/subsets/)的进阶。数组中可能包重复元素，所以代码不同的地方在于去重逻辑。选或不选的去重逻辑是：先将数组排序，如果不选第$`i`$个数，那么也不选后续和第$`i`$个数相等的元素；枚举选哪个的去重逻辑是：如果当前数和前一个数相等，直接跳过该数。

$\\color{red}{\text{时间：很快。独立思考。有了39题，40题，46题，47题，77题，78题的基础，这道题没有什么难点。}}$

#### [91. 解码方法](https://leetcode.cn/problems/decode-ways/)

动态规划题。这道题我的方法是先判断是不是有效的整数。如果当前字符自己是有效整数，那么$`dp[i]+=dp[i-1]`$。如果当前字符和前一个字符组合也是有效整数，那么$`dp[i]+=dp[i-2]`$。最后返回$`dp[n]`$即可。判断有效整数的方法是：首个字符为$`0`$的话肯定不是有效数字；如果是一位数，一定是有效字符；如果是两位数，把它转为整数看结果是否小于$`26`$。后续还可以进行空间优化，可以只用三个变量来代替$`dp`$数组。

$\\color{red}{\text{时间：较快，独立思考。感觉方法和70题差不多。}}$

#### [92. 反转链表 II](https://leetcode.cn/problems/reverse-linked-list-ii/)

我的做法是先找到第$`left-1`$位置和第$`right+1`$位置，然后反转$`left`$到$`right`$整个区间，返回头尾指针。然后让$`left-1`$位置的$`next`$指向反转后的头指针；让反转后尾指针的$`next`$指向$`right+1`$位置。反转链表的逻辑是使用两个指针$`cur`$和$`pre`$，每当遍历到一个节点时，按照如下操作：$`ListNode* temp=cur \rightarrow next;cur \rightarrow next=pre;pre=cur;cur=temp;`$

相似题目：
[206. 反转链表](https://leetcode.cn/problems/reverse-linked-list/):这题是反转整个链表。

$\\color{red}{\text{时间：很快，独立思考。反转整个链表的逻辑要熟练。}}$

### 11月3日

#### [3736. 最小操作次数使数组元素相等 III](https://leetcode.cn/problems/minimum-moves-to-equal-array-elements-iii/)

这题和[453. 最小操作次数使数组元素相等](https://leetcode.cn/problems/minimum-moves-to-equal-array-elements/)类似。遍历两次，第一次找到数组的最大值，第二次计算最大值和数组中每个元素的差值。

$\\color{red}{\text{时间：很快。简单题。}}$

#### [93. 复原 IP 地址](https://leetcode.cn/problems/restore-ip-addresses/)

回溯枚举三个$`.`$的位置，然后判断是否是有效$`IP`$。判断是否有效的方法是$`4`$个字串是否是有效数字，有效数字的判定和[91. 解码方法](https://leetcode.cn/problems/decode-ways/)类似。先把它转为整数$`num`$，如果它$`num \ge 256`$或者$`num==0\&\&s.length() \gt 1`$，返回$`false`$，其余情况返回$`true`$。

$\\color{red}{\text{时间：较快。模拟性质的题}}$

#### [94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)

方法一：递归。根据左根右的遍历顺序，先递归遍历左子树，然后将根节点放入结果集中，最后再遍历右子树。

方法二：迭代。用栈来模拟递归的过程，从根节点出发，如果左子树存在，压入栈中并一直向左。然后将栈顶元素弹出加入结果集中，然后让指向其右子树。

方法三：morris遍历。第一步是找$`root`$的前驱$`pre`$。具体方法是从$`root`$的左子树开始，一直向右走，直到走到尽头，或者遇到指向$`root`$的线索；如果$`root`$的左子树还没访问（表现为线索还没建立），将线索建立并访问左子树。当左子树访问完毕后去掉线索。左子树访问完毕后记录当前节点的值，如果有右子树就访问右子树，没有就顺着线索回到指向的节点。

做了几道相关的题：
+ [144. 二叉树的前序遍历](https://leetcode.cn/problems/binary-tree-preorder-traversal/)
+ [145. 二叉树的后序遍历](https://leetcode.cn/problems/binary-tree-postorder-traversal/)

$\\color{red}{\text{时间：第一种方法很快。其余两种方法在慢慢消化}}$

#### [95. 不同的二叉搜索树 II](https://leetcode.cn/problems/unique-binary-search-trees-ii/)

**可以采用递归的方式，从$`1`$到$`n`$中选择一个$`i`$作为根节点。则左子树为$`1`$到$`i-1`$，右子树为$`i+1`$到$`n`$。然后从可行左子树集合和可行右子树集合分别选一颗拼接到根节点上，最后将生成的二叉搜索树放入答案数组即可。**

$\\color{red}{\text{时间：看了题解。自己想比较难想到。}}$

### 11月4日

#### [3505. 使 K 个子数组内元素相等的最少操作数](https://leetcode.cn/problems/minimum-operations-to-make-elements-within-k-subarrays-equal/)

> [!WARNING]
> 待做

前置题目：
+ [295. 数据流的中位数](https://leetcode.cn/problems/find-median-from-data-stream/)
+ [480. 滑动窗口中位数](https://leetcode.cn/problems/sliding-window-median/)
+ [2602. 使数组元素全部相等的最少操作次数](https://leetcode.cn/problems/minimum-operations-to-make-all-array-elements-equal/)
+ 划分型$`DP`$

划分型$`DP`$有三类，判断能否划分，最优划分，约束划分个数。
1. 第一类判断能否划分：一般定义$`f[i]`$表示长为$`i`$的前缀$`a[:i]`$能否划分，枚举最后一个子数组的左端点$`L`$，从$`f[L]`$转移到$`f[i]`$，并考虑$`a[L:i]`$是否满足要求；
2. 第二类最优划分：一般定义$`f[i]`$表示长为$`i`$的前缀$`a[:i]`$在题目约束下，分割出的最少（最多）子数组个数，枚举最后一个子数组的左端点$`L`$，从$`f[L]`$转移到$`f[i]`$，并考虑$`a[L:i]`$对最优解的影响；
3. 第三类约束划分个数：一般定义$`f[i][j]`$表示将长为$`j`$的前缀$`a[:j]`$分成$`i`$个连续子数组所得到的最优解。枚举最后一个子数组的左端点$`L`$，从$`f[i-1][L]`$转移到$`f[i][j]`$，并考虑$`a[L:i]`$对最优解的影响。

#### [96. 不同的二叉搜索树](https://leetcode.cn/problems/unique-binary-search-trees/)

方法一：动态规划。定义$`G(n)`$为$`n`$个节点存在的二叉搜索树个数，$`f(i)`$为以$`i`$为根的二叉搜索树个数。则有$`G(n)=\sum_{i=1}^{n} f(i)`$，又因为当$`i`$为根节点时，其左子树节点个数为$`i-1`$，右子树节点个数为$`n-i`$，所以有$`f(i)=G(i-1)*G(n-i)`$。综上可$`G(n)=\sum_{i=0}^{n-1} G(i)*G(n-1-i)`$。

方法二：卡特兰数。公式为$`G_{n+1}=\frac{2(2n+1)}{(n+2)}G_{n}`$，其中$`G_{0}=1`$。

$\\color{red}{\text{时间：看了题解。}}$

#### [97. 交错字符串](https://leetcode.cn/problems/interleaving-string/)

动态规划。转移方程为$`dp[i][j]=(dp[i-1][j]\&\&s1[i-1]==s3[i+j-1])||(dp[i][j-1]\&\&s2[j-1]==s3[i+j-1])`$。注意要单独计算$`dp[0][j]`$和$`dp[i][0]`$。空间优化，可以只需要长为$`m+1`$的一维数组就够了。

$\\color{red}{\text{时间：独立思考。debug了一会时间，初始化的问题没有考虑的很全面，特别是空间优化的时候。}}$

#### [98. 验证二叉搜索树](https://leetcode.cn/problems/validate-binary-search-tree/)

我的做法是递归。首先找到左子树中的最大值，具体方法是：从左子树开始，一直向右走，直到走到尽头；然后找到右子树中的最小值，具体方法是：从右子树开始，一直往左走，直到走到尽头；判断当前元素是否大于左子树的最大值并且小于右子树的最小值。最后再递归的判断以左孩子为根节点的子树和以右孩子为根节点的子树。注意这里的数字要用$`long~long`$去存储，才能比较是否大于$`INT\_MAX`$或是小于$`INT\_MIN`$。

$\\color{red}{\text{时间：较快，独立思考。}}$

### 11月5日

#### [1385. 两个数组间的距离值](https://leetcode.cn/problems/find-the-distance-value-between-two-arrays/)

这道题数据范围不大，可以使用二重遍历。看了答案发现可以二分，对于$`arr_1`$中的元素$`x`$，如果$`arr_2`$中没有值再闭区间$`[x-d,x+d]`$中的元素，把答案加一。具体的做法是，先将$`arr_2`$从小到大排序，然后在$`arr_2`$中二分查找$`\ge x-d`$的最小数$`y`$，如果$`y`$不存在或者$`y \gt x+d`$，把答案加一。

$\\color{red}{\text{时间：很快，独立思考。简单题}}$

#### [99. 恢复二叉搜索树](https://leetcode.cn/problems/recover-binary-search-tree/)

这道题因为恰好只有两个节点的值被错误交换，而二叉搜索数的中序遍历是递增的。所以我们可以中序遍历得到一个序列。找到相邻的递减对，然后交换第一个相邻递减对的第一个数和最后一个相邻递减对的第二个数。中序遍历的方法如[94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)，这题我重新写了一下$`morris`$遍历，加深了一下印象。

$\\color{red}{\text{时间：看了一下题解。}}$

> [!TIP]
> 100题小成就！！！

#### [100. 相同的树](https://leetcode.cn/problems/same-tree/)

这道题的思路是只有当根节点，左子树，右子树都相同时，整棵树才是相同的。所以可以递归的去判断左子树和右子树是否分别相同。注意初始条件的返回，如果两个根节点有一个为空节点的话，返回两个根节点是否相等即可。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [101. 对称二叉树](https://leetcode.cn/problems/symmetric-tree/)

这道题的思路是只有当左子树和右子树互为镜像时，整棵树才是轴对称的。判断左右子树是否互为镜像的方法和[100. 相同的树](https://leetcode.cn/problems/same-tree/)类似，不过要对应的是左子树的左子树对应右子树的右子树；左子树的右子树对应右子树的左子树。

$\\color{red}{\text{时间：看了一下题解。}}$

### 11月6日

#### [2747. 统计没有收到请求的服务器数目](https://leetcode.cn/problems/count-zero-request-servers/)

这道题是离线的（可以把所有询问按照某种顺序处理，但不是按输入的顺序处理。与之对应的在线就是按照输入的顺序处理，来一个处理一个）。我的第一个想法就是昨天的每日一题[1385. 两个数组间的距离值](https://leetcode.cn/problems/find-the-distance-value-between-two-arrays/)的二分做法，先将日志按照时间顺序排序，然后将其按照服务器进行分类。对于每个询问，查询每个服务器在区间$`[queries[i]-x,queries[i]]`$是否有取值。但是这样的时间复杂度为$`O(q \times n \times log(m))`$，其中$`q`$为询问数组的长度，$`m`$为日志的长度，时间复杂度不能达到要求。然后认真思考了一会，发现可以使用滑动窗口，将询问和日志均按照时间顺序排序，对于一个新的询问$`queries[i]`$，则窗口内$`<queries[i]-x`$的数离开窗口；$`\le queries[i]`$的数进入窗口。同时维护每个服务器收到的请求数，服务器$`i`$收到的请求进入窗口，计数加一，如果加一前是零，把最终答案减一；服务器$`i`$收到的请求离开窗口，计数减一，如果减一后计数是零，把最终答案加一。这样做时间复杂度就是$`O(m\times log(m)+q \times log(q))`$，瓶颈主要在排序上。

$\\color{red}{\text{时间：做了非常久。独立思考}}$

#### [102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)

$`BFS`$遍历，用队列操作。如果根节点不为空，先把根节点放入队列中。一开始记录队列的长度，然后循环这些次数，将队列头部移出，如果其左子树不为空，将其左子树放入队列；如果其右子树不为空，将其右子树放入队列。最后统计答案即可。

$\\color{red}{\text{时间：很快。独立思考。层序遍历已经很熟练了。}}$

#### [103. 二叉树的锯齿形层序遍历](https://leetcode.cn/problems/binary-tree-zigzag-level-order-traversal/)

和[102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)类似，只需要额外一个变量记录是否需要反转，如果需要就将那一层反转。

$\\color{red}{\text{时间：很快。独立思考。一开始想这按照遍历顺序访问节点，发现没有办法。}}$

#### [104. 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)

方法一：自底向上。如果$`root`$为空，返回深度为零。否则递归返回左子树深度和右子树深度的较大值加$`1`$。

方法二：自顶向下。传递一个参数表示深度，每当递归到左子树或右子树时将深度加$`1`$。并使用一个全局变量记录答案，在深度变化时取深度的最大值。

方法三：根据[102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)，直接返回层序遍历结果的长度

$\\color{red}{\text{时间：自底向上很快。独立思考。}}$

### 11月7日

#### [1882. 使用服务器处理任务](https://leetcode.cn/problems/process-tasks-using-servers/)

这道题要使用两个堆，第一个堆用来存放空闲服务器下标及其权重；第二个堆用来存放忙碌服务器下标及其服务器完成任务的时刻。记录两个变量：当前时间$`t`$和正在遍历的任务下标$`cnt`$。初始化阶段先把所有服务器放入空闲堆。然后进行循环，先根据当前时间$`t`$是否大于等于忙碌服务器的结束时间，如果是的话，将其转移到空闲服务器堆中，然后循环判断是否有空闲的服务器和未被分配服务器的任务，将空闲服务器分配给相应的任务。如果服务器全部忙碌，将时间$`t`$更新为忙碌服务器的最早结束时间，否则将$`t`$增加一秒。注意几个要注意的点：时间$`t`$要用$`long ~ long`$数据类型；忙碌服务器只需要两个关键变量即可。

$\\color{red}{\text{时间：做了非常久，一些细节没有注意到。看了一点提示，其他独立思考。}}$

#### [105. 从前序与中序遍历序列构造二叉树](https://leetcode.cn/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

递归解法，将前序遍历的第一个数作为根，然后在中序遍历中找到根的位置下标$`index`$，中序遍历中$`[s2,index-1]`$是左子树的中序遍历，$`[index+1,e2]`$是右子树的中序遍历。前序遍历中$`[s1+1,s1+index-s2]`$是左子树的前序遍历，$`[s1+1+index-s2,e1]`$是右子树的前序遍历。然后递归的进行左右子树的还原。

$\\color{red}{\text{时间：很快。独立思考。}}$

#### [106. 从中序与后序遍历序列构造二叉树](https://leetcode.cn/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)

类似[105. 从前序与中序遍历序列构造二叉树](https://leetcode.cn/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)，也是递归解法。将后序遍历的最后一个数作为根，然后在中序遍历中找到根的位置下标$`index`$，中序遍历中$`[s2,index-1]`$是左子树的中序遍历，$`[index+1,e2]`$是右子树的中序遍历。后续遍历中$`[s1,s1+index-s2-1]`$是左子树的后序遍历，$`[s1+index-s2,e1-1]`$是右子树的后续遍历。然后递归的进行左右子树的还原。

注意已知前序遍历和后续遍历不能构造出唯一的二叉树。

$\\color{red}{\text{时间：很快。独立思考。}}$

#### [107. 二叉树的层序遍历 II](https://leetcode.cn/problems/binary-tree-level-order-traversal-ii/)

和[102. 二叉树的层序遍历](https://leetcode.cn/problems/binary-tree-level-order-traversal/)类似，只需要将结果数组反转一下即可。

$\\color{red}{\text{时间：很快。独立思考。}}$

### 11月8日

#### [1267. 统计参与通信的服务器](https://leetcode.cn/problems/count-servers-that-communicate/)

使用两个数组分别记录每行服务器的数量和每列服务器的数量，然后遍历数组，如果$`grid[i][j]==1`$并且其所在行或者所在列的服务器数量大于$`1`$说明它可以与其他服务器通信，将答案加$`1`$。

$\\color{red}{\text{时间：很快。独立思考。}}$

#### [108. 将有序数组转换为二叉搜索树](https://leetcode.cn/problems/convert-sorted-array-to-binary-search-tree/)

递归解法。将数组的中点作为二叉树的根。然后左子树对应的数组是$`[s,mid-1]`$，右子树对应的数组是$`[mid+1,e]`$。然后递归的进行左右子树的还原。

$\\color{red}{\text{时间：很快。独立思考。}}$

#### [109. 有序链表转换二叉搜索树](https://leetcode.cn/problems/convert-sorted-list-to-binary-search-tree/)

也是递归解法，使用快慢指针找到链表的中点$`slow`$和中点的前一个数$`pre`$，将中点对应的数作为根节点。如果链表的中点等于头节点，说明只有一个数，直接返回这个数；否则先记录下中点的$`next`$指针指向的数$`right`$，然后断开中点前一个数和中点的$`next`$指针，则左子树的头节点是$`head`$，右子树的头节点是$`right`$。然后递归的进行左右子树的还原。

$\\color{red}{\text{时间：较快。只有一个数的情况考虑了好久。独立思考。}}$

#### [110. 平衡二叉树](https://leetcode.cn/problems/balanced-binary-tree/)

先根据[104. 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)，计算每棵树的最大深度，如果左子树的最大深度和右子树的最大深度的差值绝对值$`\le 1`$，就递归的判断左子树和右子树是否平衡。否则直接返回$`false`$。

**看了题解发现可优化，可以在计算高度时就开始判断是不是平衡的，在计算高度时如果左子树返回$`-1`$或者右子树返回$`-1`$或者左右子树的高度差大于$`1`$，直接返回$`-1`$。**

$\\color{red}{\text{时间：较快。独立思考。我的方法在递归中又有递归，两者逻辑相似，完全可以省略掉其中一个递归。}}$

### 11月9日

#### [1606. 找到处理最多请求的服务器](https://leetcode.cn/problems/find-servers-that-handled-most-number-of-requests/)

> [!WARNING]
> 待做

#### [111. 二叉树的最小深度](https://leetcode.cn/problems/minimum-depth-of-binary-tree/)

方法一：自顶向下。传递一个参数表示深度，每当递归到左子树或右子树时将深度加$`1`$。并使用一个全局变量记录答案，在左右子树均为空时（叶子节点）时取深度的最小值。

**方法二：自底向上。注意对于非叶子节点，如果一个儿子时是空节点，另一个儿子不是空节点，那么答案只能来自非空的那一侧。所以要比[104. 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)多写两段逻辑。**

$\\color{red}{\text{时间：自顶向下很快。独立思考。自底向上看了题解才想到。}}$

#### [112. 路径总和](https://leetcode.cn/problems/path-sum/)

递归解法，先将$`targetSum`$减去根节点的数，如果$`targetSum==0`$并且当前节点是左右子树均为空（叶子节点）时说明找打了正确路径，直接返回$`true`$，否则递归的在左右子树判断更新后$`targetSum`$值。

$\\color{red}{\text{时间：写了较久。一开始逻辑没理顺。一开始应该先减去当前根节点的值再进行判断。}}$

#### [113. 路径总和 II](https://leetcode.cn/problems/path-sum-ii/)

这道题是[112. 路径总和](https://leetcode.cn/problems/path-sum/)的进阶版，还需要求出所有符合条件的路径。我的做法是使用一个数组$`path`$来记录路径，开始时将根节点的值加入路径，然后更新剩余目标，如果该节点左右子树均为空（叶子节点），将$`path`$加入到答案中。然后继续递归的遍历左右子树，只在递归完右子树后恢复现场。

$\\color{red}{\text{时间：思考了很久，一直找不到恢复现场的合适时机。不断调试才找出来。独立思考。}}$

### 11月10日

#### [3693. 爬楼梯 II](https://leetcode.cn/problems/climbing-stairs-ii/)

与[70. 爬楼梯](https://leetcode.cn/problems/climbing-stairs/)类似，这道题多了一步可以走3级台阶，成本计算方式也变了。这道题我使用的是刷表法，定义$`dp[i]`$表示从$`0`$爬到$`i`$的最小总成本，现在$`i`$的状态会影响$`i+1`$，$`i+2`$和$`i+3`$的状态。或者考虑最后一步爬了多少个台阶，则$`dfs[i]=min_{j=max(i-3,0)}^{i-1} dfs[j]+(i-j)^2+costs[i]`$

$\\color{red}{\text{时间：很快。是70题的进阶版}}$

#### [114. 二叉树展开为链表](https://leetcode.cn/problems/flatten-binary-tree-to-linked-list/)

方法一：先序遍历记录下每个节点，然后不断尾插在前一个节点的右指针上。这种方法用到了额外空间$`O(n)`$。其中先序遍历的方法和[94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)题类似，这里我使用的是morris遍历，和中序遍历不同的仅仅在加入答案的位置不同。

**方法二：反先序遍历。根据右左根的顺序遍历二叉树，在递归结束前按照头插法的思想将结果插入到头部。但是递归有额外的空间复杂度$`O(h)`$。**

**方法三：找到根节点的左子树的最右节点，其右指针指向根节点的右子树，然后根节点的左子树变为空，根节点的右子树变为原来根节点的左子树。然后根节点向右移动，不断循环这个过程。这样空间复杂度就是最优的$`O(1)`$。**

$\\color{red}{\text{时间：方法一很快。方法二和方法三没想到，看了题解。}}$

#### [115. 不同的子序列](https://leetcode.cn/problems/distinct-subsequences/)

动态规划题。定义$`dp[i][j]`$表示$`s[0:i]`$的子序列出现$`t[0:j]`$的个数。则可以得到下面的状态转移方程：当$`s[i]==t[j]`$时，$`dp[i][j]=dp[i-1][j-1]+dp[i-1][j]`$；当$`s[i]!=t[j]`$时，$`dp[i][j]=dp[i-1][j]`$。这里可以发现只和前一行的状态有关，所以可以使用空间优化，但是要注意应当和$`0-1`$背包一样，内层循环使用倒序枚举，防止值被覆盖。

$\\color{red}{\text{时间：很快。但是空间优化卡了一下，没有想到倒序枚举。}}$

#### [116. 填充每个节点的下一个右侧节点指针](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node/)

这道题使用的是层序遍历的思路，当当前元素出队列后，下一个队顶元素就是其右侧节点，不过需要注意的是每一层的最后一个元素右侧节点为$`NULL`$。所以可以在层序遍历的代码上，把加入结果部分修改为更新$`next`$的指向，注意只更新不是每层最后一个节点的元素。

$\\color{red}{\text{时间：很快。独立思考。层序遍历的思路。}}$

#### [117. 填充每个节点的下一个右侧节点指针 II](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node-ii/)

和[116. 填充每个节点的下一个右侧节点指针](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node/)解法一致，代码搬运过来就能$`AC`$。

$\\color{red}{\text{时间：很快。独立思考}}$

### 11月11日

#### [3789. 采购的最小花费](https://leetcode.cn/problems/minimum-cost-to-acquire-required-items/)

当$`costBoth \ge (cost1+cost2)`$时，购买类型$`3`$不会更优；反之，当$`costBoth \lt (cost1+cost2)`$时，不可能同时存在物品$`1`$和物品$`2`$。即先用物品$`3`$让其中一种类型先满足要求，对于不满足要求的类型，要么买物品$`3`$，要么买和类型对应的物品，两种情况取最小值即可。注意要用$`long ~ long`$数据类型防止溢出。

$\\color{red}{\text{时间：很快。独立思考。一开始以为第二种情况只需要买物品三，后来发现了错误。}}$

#### [118. 杨辉三角](https://leetcode.cn/problems/pascals-triangle/)

动态规划题。主要是想清楚状态转移方程：如果$`j==0||j==i`$，那么$`dp[i][j]=1`$，否则$`dp[i][j]=dp[i-1][j]+dp[i-1][j-1]`$。最后不要忘记使用$`resize`$函数把数组裁剪到合适的大小。

$\\color{red}{\text{时间：很快。独立思考}}$

#### [119. 杨辉三角 II](https://leetcode.cn/problems/pascals-triangle-ii/)

只需要返回[118. 杨辉三角](https://leetcode.cn/problems/pascals-triangle/)答案的最后一行即可。

$\\color{red}{\text{时间：很快。独立思考}}$

#### [120. 三角形最小路径和](https://leetcode.cn/problems/triangle/)

动态规划题。这道题的状态转移方程和[118. 杨辉三角](https://leetcode.cn/problems/pascals-triangle/)类似，为$`dp[i][j]=min(dp[i-1][j],dp[i-1][j-1])+triangle[i][j]`$。然后注意初始化第$`0`$列。还可以进行空间优化，不过需要注意的是内层循环应该从后往前遍历，防止覆盖。

$\\color{red}{\text{时间：很快。独立思考}}$

### 11月12日

#### [3105. 最长的严格递增或递减子数组](https://leetcode.cn/problems/longest-strictly-increasing-or-strictly-decreasing-subarray/)

这道题我使用两次遍历，一次遍历找最长严格递增非空子数组；另一次遍历找最长严格递减非空子数组。取两次遍历的最大值。找最长严格递增非空子数组的方法是使用一个变量记录符合要求的个数，如果遇到不符合要求的数，立即重新计算。看了题解发现还可以分组循环。

$\\color{red}{\text{时间：很快。独立思考}}$

#### [121. 买卖股票的最佳时机](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/)

方法一：贪心。存下数组中当前位置左边的最小元素，然后遍历数组的值减去当前位置左边的最小元素，得到最大利润。

方法二：动态规划：含义：$`dp[i][0]`$:表示第$`i`$天结束时未持有股票的最大利润；$`dp[i][1]`$:表示第$`i`$天结束时持有股票的最大利润。初始化：$`dp[0][1]=-1*price[0]`$，其余为$`0`$。状态转移方程：$`dp[i][0]=max(dp[i-1][0],dp[i-1][1]+price[i])`$ //什么都不做或者卖出。$`dp[i][1]=max(dp[i-1][1],-1*price[i])`$ //什么都不做或者买入。最后返回$`dp[n-1][0]`$。

$\\color{red}{\text{时间：较快。看了一点提示}}$

#### [122. 买卖股票的最佳时机 II](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)

方法一：贪心。遍历，如果当前元素比前一个元素大，则将利润加上他们的差值，否则不操作。

方法二：动态规划。含义：$`dp[i][0]`$:表示第$`i`$天结束时未持有股票的最大利润；$`dp[i][1]`$:表示第$`i`$天结束时持有股票的最大利润。初始化：$`dp[0][1]=-1*price[0]`$，其余为$`0`$。状态转移方程：$`dp[i][0]=max(dp[i-1][0],dp[i-1][1]+price[i])`$ //什么都不做或者卖出。$`dp[i][1]=max(dp[i-1][1],dp[i-1][0]-price[i])`$ //什么都不做或者买入。最后返回$`dp[n-1][0]`$。

$\\color{red}{\text{时间：较快。看了一点提示。}}$

#### [123. 买卖股票的最佳时机 III](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iii/)

动态规划题。详细内容见[笔记](https://github.com/wkwkevin123/leetcode/blob/main/note/stock%20problems.docx)。还做了这道题的进阶版[188. 买卖股票的最佳时机 IV](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-iv/)

$\\color{red}{\text{时间：较快。看了一点提示。}}$

### 11月13日

#### [3420. 统计 K 次操作以内得到非递减子数组的数目](https://leetcode.cn/problems/count-non-decreasing-subarrays-after-k-operations/)

> [!WARNING]
> 待做

#### [124. 二叉树中的最大路径和](https://leetcode.cn/problems/binary-tree-maximum-path-sum/)

**递归解法，$`dfs`$遍历到每个节点时，把其视为转折点计算经过这个点的最大路径和$`root \rightarrow val+max(0,dfs(root \rightarrow left))+max(0,dfs(root \rightarrow right))`$。返回的是单链的最大路径和$`max(dfs(root \rightarrow left),dfs(root \rightarrow right))+ root \rightarrow val`$**

$\\color{red}{\text{时间：看了题解。}}$

#### [125. 验证回文串](https://leetcode.cn/problems/valid-palindrome/)

我的做法是，只将小写字母，大写字母和数字写在一个字符串中，然后判断这个这个字符串是不是回文的。然后题解的做法是双指针，如果左指针不是三种之一，将左指针右移；如果右指针不是三种其中之一，将右指针左移；比较左指针和右指针小写化后是否相等，如果不相等直接返回$`false`$。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [126. 单词接龙 II](https://leetcode.cn/problems/word-ladder-ii/)

**这道题的思路是先用$`BFS`$建图，然后使用回溯法找所有符合条件的路径。找邻居单词的时候可以让单词的每个字母逐个改动，生成$`25`$个新单词，选出存在于字典中的就是邻居单词。然后出现过的单词要及时从$`set`$中删去，避免重复访问。最后回溯的时候从终点词开始回溯，最后将结果逆序即可。**

$\\color{red}{\text{时间：看了题解。主要考察将抽象问题建模，图的建立和回溯。}}$

#### [127. 单词接龙](https://leetcode.cn/problems/word-ladder/)

这道题简单一点，建立邻接表，然后从起点词开始做$`BFS`$找最短路径。这里我建立邻接表的方式是依次判断字典中的两个单词是否只差一个字母。看了题解发现可以将单词的每个字母逐个改动，然后判断改动后的单词是否在字典中以及是否被访问过来决定是否加入队列。

$\\color{red}{\text{时间：独立思考。以后看到小写字母的题要想到枚举每一个字母而不是根据长度枚举。}}$

### 11月16日

#### [2243. 计算字符串的数字和](https://leetcode.cn/problems/calculate-digit-sum-of-a-string/)

按照题意模拟即可。如果当前字符串的长度大于$`k`$，就$`k`$个一组计算每组的数字和，然后将所有组的数字和凭借在一起作为新的字符串。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [128. 最长连续序列](https://leetcode.cn/problems/longest-consecutive-sequence/)

将整个数组存在$`set`$中，然后遍历它，如果遍历到某个数$`x`$，如果它的前一个数$`x-1`$也在当中，说明这个数一定不是起点，可以直接跳过它。否则的话，把它当作起点，一直寻找$`x+1`$是否存在，然后更新答案。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [129. 求根节点到叶节点数字之和](https://leetcode.cn/problems/sum-root-to-leaf-numbers/)

我的做法是自顶向下，计算从根到当前节点的路径上所代表的数字。如果这个节点是叶子节点，就将这个数字加入到结果中。最后继续传递到左子树和右子树中。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [130. 被围绕的区域](https://leetcode.cn/problems/surrounded-regions/)

反向思维，从边界出发$`DFS`$，将所有与边界连通的$`O`$变成一个特殊字符。最后遍历整个图，将特殊字符全部变成$`O`$，不是特殊字符变成$`X`$。边界可以按照步长来划分，最后一行和第一行的步长是$`1`$，其余行的步长是$`m-1`$。

$\\color{red}{\text{时间：很快，独立思考。}}$

### 11月17日

#### [2911. 得到 K 个半回文串的最少修改次数](https://leetcode.cn/problems/minimum-changes-to-make-k-semi-palindromes/)

> [!WARNING]
> 待做

#### [131. 分割回文串](https://leetcode.cn/problems/palindrome-partitioning/)

我的做法是枚举分割的位置，选择$`[1:n-1]`$的所有子集，然后判断每一种情况是否都是回文子串。判断字串是否是回文子串可以动态规划预处理。$`dp[i][j]`$表示子串$`[i:j]`$是否是回文串。那么$`dp[i][j]=(s[i]==s[j])\&\&(dp[i+1][j-1])`$，注意遍历的时候$`i`$要逆向遍历，$`j`$要正向遍历，才能保证需要的状态已经提前得到。

$\\color{red}{\text{时间：较快，独立思考。}}$

#### [132. 分割回文串 II](https://leetcode.cn/problems/palindrome-partitioning-ii/)

动态规划题。$`dp[i]`$表示以$`s[0:i]`$需要的分割次数，如果$`s[l:i]`$是回文串，那么$`dp[i]=min(dp[l]+1)`$，其中$`l \lt i`$。判断子串是否是回文串的方法和[131. 分割回文串](https://leetcode.cn/problems/palindrome-partitioning/)相同。

$\\color{red}{\text{时间：较快，独立思考。}}$

#### [133. 克隆图](https://leetcode.cn/problems/clone-graph/)

**我的做法是使用哈希将值和节点映射起来。然后使用一个集合来存储访问过的顶点，使用另一个集合存储访问过的边。看了题解发现有种更简单的方式，使用哈希将原来的节点和克隆的节点映射起来。如果遍历到一个节点发现这个哈希表中没有找到，就克隆这个节点并存储在哈希表中。可以使用广度优先搜索和深度优先搜索两种遍历方式。**

$\\color{red}{\text{时间：做了很久，我的方法太复杂了。}}$

### 11月18日

#### [2914. 使二进制字符串变美丽的最少修改次数](https://leetcode.cn/problems/minimum-number-of-changes-to-make-binary-string-beautiful/)

因为美丽的子字符串长度都是偶数，且所有字符相同，所以全部都可以看成长度为$`2`$的美丽子字符串。两两一组判断是否需要修改即可。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [134. 加油站](https://leetcode.cn/problems/gas-station/)

这道题只要想清楚一个点，如果两个数组的差值总和小于$`0`$，一定没有解；而差值总和大于$`0`$的话，一定有解，只需要找到最低点，它的下一个就是答案的下标。

$\\color{red}{\text{时间：看了一下题解。}}$

#### [135. 分发糖果](https://leetcode.cn/problems/candy/)

从前往后遍历，让每个孩子和他的左孩子满足题目要求；从后往前遍历，让每个孩子和他的右孩子满足题目要求，最后取两个数的较大值即可。

$\\color{red}{\text{时间：看了一下题解。}}$

#### [136. 只出现一次的数字](https://leetcode.cn/problems/single-number/)

将全部数异或，出现两次的数异或结果为$`0`$，最后只剩下那个出现一次的数。

$\\color{red}{\text{时间：很快，独立思考。}}$

### 11月19日

#### [2567. 修改两个元素的最小分数](https://leetcode.cn/problems/minimum-score-by-changing-two-elements/)

这道题只可能有三种情况，第一种情况是修改下标$`0`$和下标$`1`$，此时最大得分为$`nums[n-1]-nums[2]`$，最小得分为$`0`$；第二种情况是修改下标$`n-1`$和下标$`n-2`$,此时最大得分是$`nums[n-3]-nums[0]`$，最小得分为$`0`$;第三种情况是修改下标$`0`$和下标$`n-1`$，此时最大得分是$`nums[n-2]-nums[1]`$，最小得分是$`0`$。最后取三种情况的最小值作为答案。

$\\color{red}{\text{时间：很快，看了一下题解。}}$

#### [137. 只出现一次的数字 II](https://leetcode.cn/problems/single-number-ii/)

这道题可以统计每个二进制位上$`1`$的数量，如果$`1`$的数量模$`3`$后为$`0`$，说明这个二进制位上是$`0`$；如果$`1`$的数量模$`3`$后为$`1`$，说明这个二进制位上是$`1`$。最后根据每个二进制位拼凑出这个只出现一次的数字。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [138. 随机链表的复制](https://leetcode.cn/problems/copy-list-with-random-pointer/)

方法一：类似[133. 克隆图](https://leetcode.cn/problems/clone-graph/)，使用一个哈希表来存储原节点和复制节点的映射关系。每次遍历到一个节点，如果在哈希表中找不到，先在哈希表中创建一个映射，然后再连接复制节点的$`next`$指针和$`random`$指针。

方法二：不使用哈希表，将复制后的节点直接连在原链表对应节点的后面。则之后连接$`random`$时，可以有$`cur \rightarrow next \rightarrow random=cur \rightarrow random \rightarrow next`$

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [139. 单词拆分](https://leetcode.cn/problems/word-break/)

方法一：这道题使用的是动态规划方法，定义状态$`dp[i]`$表示子字符串$`[0:i]`$能否利用字典中出现的一个或多个单词拼接出来。那么，$`dp[i]=dp[j]\&\&valid([j:i])`$，其中$`j \lt i`$。

方法二：用字典树，结合回溯+记忆化搜索。用一个数组记录以某个位置为起点是否符合要求。然后从开始位置进行回溯遍历，遇到一个单词的结束字符后可以向下递归的进行判断。如果不成立，那么继续向下遍历遇到下一个结束字符再向下递归。

$\\color{red}{\text{时间：很快，独立思考。}}$

### 11月20日

#### [3041. 修改数组后最大化数组中的连续元素数目](https://leetcode.cn/problems/maximize-consecutive-elements-in-an-array-after-modification/)

方法一：先排序。定义$`dp[i][0]`$表示以$`nums[i]`$结尾且$`nums[i]`$不加$`1`$的最长子序列。$`dp[i][1]`$表示以$`nums[i]`$结尾且$`nums[i]`$加$`1`$的最长子序列。然后使用二分查找找到第一个大于等于$`(nums[i]-2)`$的位置$`j`$。然后遍历$`j:i-1`$，如果$`nums[i]==nums[j]`$，那么$`dp[i][1]=max(dp[i][1],dp[j][0]+1)`$；如果$`nums[i]=(nums[j]+1)`$，那么$`dp[i][0]=max(dp[i][0],dp[j][0]+1)`$并且$`dp[i][1]=max(dp[i][1],dp[j][1]+1)`$；如果$`nums[i]=(nums[j]+2)`$，那么$`dp[i][0]=max(dp[i][0],dp[j][1]+1);`$

方法二：先排序。改一下数组的定义：$`dp[i][0]:nums[i]`$不加$`1`$时子数组$`(nums[0:i])`$的最大连续元素数目；$`dp[i][1]:nums[i]`$加$`1`$时子数组$`(nums[0:i])`$的最大连续元素数目。设$`j=i-1`$，如果$`nums[i]==nums[j]`$，那么$`dp[i][1]=max(dp[j][1],dp[j][0]+1)`$；如果$`nums[i]=(nums[j]+1)`$，那么$`dp[i][0]=max(dp[j][0]+1,dp[j][1])`$并且$`dp[i][1]=dp[j][1]+1`$；如果$`nums[i]=(nums[j]+2)`$，那么$`dp[i][0]=dp[j][1]+1`$。

方法三：先排序。使用哈希表作为数组，利用值域进行动态规划。$`dp[i]`$表示子序列最后一个数是$`x`$时，子序列的最大长度。那么$`dp[nums[i]+1]=dp[nums[i]]+1`$并且$`dp[nums[i]]=dp[nums[i]-1]+1`$。注意要先更新$`dp[nums[i]+1]`$，再更新$`dp[nums[i]]`$。

做了一道相似题目：

[1218. 最长定差子序列](https://leetcode.cn/problems/longest-arithmetic-subsequence-of-given-difference/)：也是使用值域动态规划。

$\\color{red}{\text{时间：看了一下题解。}}$

#### [140. 单词拆分 II](https://leetcode.cn/problems/word-break-ii/)

这道题要给出所有可能的句子，所以采用回溯法。从起始位置$`start`$开始回溯，如果到最终位置$`end`$了，说明可以将结果写入答案。否则的话，找到一个合适的位置$`i`$向下回溯。这里合适的位置是指子字符串$`s[start,i-1]`$在字典当中。判断是否在字典当中可以使用字典树或是$`set`$。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [141. 环形链表](https://leetcode.cn/problems/linked-list-cycle/)

使用快慢指针，慢指针走一步，快指针走两步。如果最后两个指针能相遇，就存在圈。证明如下：慢指针第一次进入圈中时，快指针肯定已经在圈中了。此时快慢指针的相对速度是$`1`$，所以保证不会一直跳过相遇位置。

$\\color{red}{\text{时间：很快，独立思考。}}$

#### [142. 环形链表 II](https://leetcode.cn/problems/linked-list-cycle-ii/)

Floyd 判圈算法。让另一个指针从头开始走，慢指针从相遇位置开始走，则两个指针相遇时就是环的入口。证明如下：设$`a`$为从链表头节点到环入口的距离；设$`b`$为从环入口沿着$`next`$方向到相遇点的距离；设$`c`$为从相遇点沿着$`next`$方向到环入口的距离。则环的总长度为$`L=b+c`$。慢指针走过的距离是：$`S_{slow}=a+b+mL`$，快指针走过的距离是$`S_{fast}=2S_{slow}`$。又因为快指针一定比慢指针多走$`k`$圈的环，所以$`S_{fast}-S_{slow}=S_{slow}=kL`$，所以$`a+b+mL=kL`$，化简得到$`a=(k-m-1)L+c`$。得证。

$\\color{red}{\text{时间：很快，独立思考。}}$
