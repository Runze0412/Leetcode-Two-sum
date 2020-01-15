# #leetcode-Two sum  Python向#
## 为人不识two sum, 刷尽leetcode也枉然。  ##
进入leetcode，开篇第一题Two sum。给出一组数字，若其中有两个数字之和为目标target，则返回这两个数字的索引号码。乍一看很简单，两个循环搞定。可是我不喜欢循环套循环的结构。太浪费时间还容易出错。先试一下，用target减去一个数，再判断结果是否在数列中。OK，先试试。  
    

	class Solution:
	    def twoSum(self, nums: List[int], target: int) -> List[int]:
	        k = 0 #设置一个计数器
	        for i in nums: #在nums数组中循环起来
	            k += 1  #循环一次计数器加一
	            if (target-i) in nums[k:]:  #判断target-i在不在数组nums中，以k来重新计数
	                return ( k-1, nums[k:].index(target-i)+k )#返回k-1,k初始为0. nums[k:].index(target-i)+k,因为在K中重新开始计数，所以最后加上k。
