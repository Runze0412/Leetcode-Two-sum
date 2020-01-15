# #leetcode-Two sum-python向#
## 为人不识two sum, 刷尽leetcode也枉然。  ##
进入leetcode，开篇第一题Two sum。给出一组数字，若其中有两个数字之和为目标target，则返回这两个数字的索引号码。乍一看很简单，两个循环搞定。可是我不喜欢循环套循环的结构。太浪费时间还容易出错。先试一下，用target减去一个数，再判断结果是否在数列中。OK，先试试。  
    

	class Solution:
	    def twoSum(self, nums: List[int], target: int) -> List[int]:
	        k = 0 #设置一个计数器
	        for i in nums: #在nums数组中循环起来
	            k += 1  #循环一次计数器加一
	            if (target-i) in nums[k:]:  #判断target-i在不在数组nums中，以k来重新计数
	                return ( k-1, nums[k:].index(target-i)+k )#返回k-1,k初始为0. nums[k:].index(target-i)+k,因为在K中重新开始计数，所以最后加上k。
  

这个本质还是两次循环，用一个If语句方便理解。其实时间复杂度还是 O(n^2)。  
运行结果是：	Accepted	856 ms	13.7 MB	python3。  

  
接下来优化一下，让循环只进行一次，降低时间复杂度。用哈希表。  
哈希表是一个存放键值对的地方。我们可以把一个数字存放在哈希表中，然后用其他的数字和哈希表对应，这样就只用了一次循环。 再试一次。  
  
	class Solution:
	    def twoSum(self, nums: List[int], target: int) -> List[int]:
	        hash_table={} #建立一个哈希表
	        for i in range(len(nums)):  #循环跑起来
	            hash_table[nums[i]]=i  #把nums数组存到哈希表中
	            
	        for i in range(len(nums)):  #循环跑起来
	            if target-nums[i] in hash_table:  #用target-nums[i]和哈希表中的数字对应
	                if hash_table[target-nums[i]] != i: #同一个数不能用两次
	                    return[i, hash_table[target-nums[i]]]

这样就时间复杂度就变成了O(n)，而只多了一点点存放哈希表的内存。  
运行结果是：Accepted	48 ms	14.8 MB	python3。  
多用了8%的内存，是运行速度增快了17.8倍。  
这是个很典型的用空间换时间的策略，很划算！
