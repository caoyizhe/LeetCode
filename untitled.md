# 刷题笔记

**236. Lowest Common Ancestor of a Binary Tree**

[**https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/discuss/158060/Python-DFS-tm**](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/discuss/158060/Python-DFS-tm)

**Given a binary tree, find the lowest common ancestor \(LCA\) of two given nodes in the tree.**

**According to the** [**definition of LCA on Wikipedia**](https://en.wikipedia.org/wiki/Lowest_common_ancestor)**: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants \(where we allow a node to be a descendant of itself\).”**

**Example 1:**

![](https://lh6.googleusercontent.com/He3p15wxOgz5uIsjykJggAoEEos4foBPbQLw-VoSI6xwNbkkm29JjNPuKiiXWmyxQ297WzFodoeDW5ueTQk9BY1sy4Qw6i6-_PPUf78Ppy2aPn6W8xeK2HPX7sdpxUAORNFLc1f-=s0)

**Input: root = \[3,5,1,6,2,0,8,null,null,7,4\], p = 5, q = 1**

**Output: 3**

**Explanation: The LCA of nodes 5 and 1 is 3.**

**解法：DFS+recursive找p和q，一旦找到了任意p或q或null（null说明已经走到底了）直接返回这个node，如果在某个parent node发现左右各返回一个 not null node，说明该parent就是LCA，如果一直回到root都只有单边node是not null，那这个单边的node一定是LCA（因为root的另一边根本找不到另一个node，说明剩下那个node一定在这个单边node的child里面）**  


**230. Kth Smallest Element in a BST**  
[**https://leetcode.com/problems/kth-smallest-element-in-a-bst/**  
](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)**Given the root of a binary search tree, and an integer k, return the kth \(1-indexed\) smallest element in the tree.**

**Example 1:**

![](https://lh5.googleusercontent.com/PI6eDAcgbug4kqzkxXE-mXZaD7ZLRwgCqn-KVKC3GFPp1oXIb9go5I6EZxJUTeQgUVyQEpXd9G76zooKU0GYV5mX-UT6sFYLLezsrR4fVwZqZCowjj6FvrMBbU5GB9QX-Dd-CRpC=s0)

**Input: root = \[3,1,4,null,2\], k = 1**

**Output: 1**

**解法：这题核心是BST，所以通过in-order traverse能从最小数到第k小的node。可以recursively数，也可以借助一个stack来实现 in-order数数。**

**581. Shortest Unsorted Continuous Subarray**

[**https://leetcode.com/problems/shortest-unsorted-continuous-subarray/**](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)

**Given an integer array nums, you need to find one continuous subarray that if you only sort this subarray in ascending order, then the whole array will be sorted in ascending order.**

**Return the shortest such subarray and output its length.**

**Example 1:**

**Input: nums = \[2,6,4,8,10,9,15\]**

**Output: 5**

**Explanation: You need to sort \[6, 4, 8, 10, 9\] in ascending order to make the whole array sorted in ascending order.**

**核心思想：从左边看的话，正常递增数字肯定会越来越大，如果突然看到一个比前一个小的，就表示当前访问的元素位置错了，需要往前找到它应该在的正确位置，我需要找到这样一个最小的“错误”数字， 应该在的正确位置即为L;**

**类似的，从右边看，正常数字应该会递减，如果突然看到一个比前一个大的，就是位置错了，我要找到一个最大的“错误”数字，应该在的正确位置即为R；**

**最后R - L + 1就是要找的subarray，这里要注意并不是找整个数组的max和min，而是出现错误以后的max和min，因为有可能真正的max和min已经在头尾了。**

**解法1：可以用stack实时跟踪当前错误的max或min应该在的位置**

**解法2：直接先遍历两遍array找到错误的max 和 min，再从左往右找到min应该在的位置，从右往左找到max应该在的位置。**  


**124. Binary Tree Maximum Path Sum**

[**https://leetcode.com/problems/binary-tree-maximum-path-sum/discuss/603423/Python-Recursion-stack-thinking-process-diagram**  
](https://leetcode.com/problems/binary-tree-maximum-path-sum/discuss/603423/Python-Recursion-stack-thinking-process-diagram)**A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.**

**The path sum of a path is the sum of the node's values in the path.**

**Given the root of a binary tree, return the maximum path sum of any path.**

**Example 1:**

![](https://lh6.googleusercontent.com/N_L_XRUR7HPsWahi4o0ipMKqFmQCPz6Y1hRsNqfV8FKVa3zGr26YMewz_nLlaEEn4sKEVgINM2D2Buvvx1U7HXK1LCwHLTrPj97hHRjNpdOLwcu7lD7Gk-Vh2UlXle2vBaFu6nwc=s0)

**Input: root = \[1,2,3\]**

**Output: 6**

**Explanation: The optimal path is 2 -&gt; 1 -&gt; 3 with a path sum of 2 + 1 + 3 = 6.**

**解法：用DFS+recursive做，核心思想是把任意一个node当做root时，找left branch的max path sum和right branch的max path sum，当走到空node（leaf）时， 返回0. 找到的结果和0比大小（小于0代表这个branch根本没有利用价值，可以当做0，也就是不用）然后update result = max\(result, current val + max left + max right\). return只能返回单边 （因为对于上面的parent node，你只能走左边或者右边，不可能两边都取）。  
  
39. Combination Sum**  
[**https://leetcode.com/problems/combination-sum/**  
](https://leetcode.com/problems/combination-sum/)**40. Combination Sum II**  
[**https://leetcode.com/problems/combination-sum-ii/**  
](https://leetcode.com/problems/combination-sum-ii/)**216. Combination Sum III**  
[**https://leetcode.com/problems/combination-sum-iii/**  
](https://leetcode.com/problems/combination-sum-iii/)**46. Permutations**  
[**https://leetcode.com/problems/permutations/**  
](https://leetcode.com/problems/permutations/)**都用backtrack 回溯解，注意for loop选择下一个candidate如果可以重复选，那下一个function的for loop起点是当前位置，如果不能重复选，下一个function的for loop起点需要跳到（排序后的）数列的下一个不重复的新数字。**  
  


**48. Rotate Image**  
[**https://leetcode.com/problems/rotate-image/**  
](https://leetcode.com/problems/rotate-image/)**把一个方形2D矩阵翻转90度，要求inplace移动数字。  
顺时针90度：array先从上至下纵向reverse，再沿左上角到右下角的对角线Matrix\[i\]\[j\] 和 Matrix\[j\]\[i\]对换  
逆时针90度：先从左至右横向reverse，再沿左上角到右下角的对角线对换  
  
49. Group Anagrams**  
[**https://leetcode.com/problems/group-anagrams/**  
](https://leetcode.com/problems/group-anagrams/)**anagram就是字母一样排序不同，先for loop一遍input把每个string sort以后插入到map&lt;string, vector&lt;string&gt;&gt;里，key是sorted过的string（方便对比找anagram），value就是需要group的anagrams了  
  
62. Unique Paths**

[**https://leetcode.com/problems/unique-paths/**](https://leetcode.com/problems/unique-paths/)

**64. Minimum Path Sum**  
[**https://leetcode.com/problems/minimum-path-sum/**  
](https://leetcode.com/problems/minimum-path-sum/)**经典DP，一个m\*n矩阵，从左上角走到右下角，只能向下或向右，有几种走法。因为每个格子可到达的方式只能从它左边或者从它上面，所以dp\[i\]\[j\] = dp\[i\]\[j-1\] + dp\[i-1\]\[j\]。dp也可以节约到1维数组，因为横向从左到右遍历dp\[j\] = dp\[j\] + dp\[j-1\] dp\[j\]相当于当前cell的上面，dp\[j-1\]相当于当前cell的左边。  
  
72. Edit Distance**  
[**https://leetcode.com/problems/edit-distance/**  
](https://leetcode.com/problems/edit-distance/)**比较两个字符串用最少多少步operation可以变成一样的字符串。DP解，初始解法是2维DP，DP\[i\]\[j\]代表word1\[0...i-1\] 变成 word2\[0...j-1\]的最少步数。每次看下一个字母对比i和j两种情况：  
1. word\[i\]==word\[j\], 那么直接DP\[i+1\]\[j+1\] = DP\[i\]\[j\];  
2. 新的字母不同，那就要考虑replace\(DP\[i-1\]\[j-1\]\), delete\(DP\[i-1\]\[j\]\) or insert\(DP\[i\]\[j-1\]\)，取其中最小的，加1步新的操作：  
DP\[i\]\[j\] = min\(DP\[i-1\]\[j-1\], DP\[i-1\]\[j\], DP\[i\]\[j-1\]\) + 1  
  
4. Median of Two Sorted Arrays**  
[**https://leetcode.com/problems/median-of-two-sorted-arrays/**  
](https://leetcode.com/problems/median-of-two-sorted-arrays/)**详细解法看：**[**https://zhuanlan.zhihu.com/p/70654378**  
](https://zhuanlan.zhihu.com/p/70654378)**简单说是从nums1\[\] 找出m1个元素，从nums2\[\]找出m2个元素，满足一下条件：  
1. m1 + m2 = \(nums1.size + nums2.size + 1\)/2 （这里加1是省去考虑odd/even**

**2. max\(nums1\[m1-1\], nums2\[m2-1\]\) &lt;= min\(nums1\[m1\], nums2\[m2\]\)**

**有一些边界注意点：最好nums1.size &lt;= nums2.size，可以把数组对换  
考虑到m1-1, m2-1, m1, m2可能会出边界的情况，筛选valid index去比较**  


