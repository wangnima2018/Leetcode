<h3>
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
<h3>

<h3>题意<h3>
<p>给一个数组，找到一组数，他们的和为给定的target<p>


<h3>解题<h3>
<p>brute force方法，需要用O(N^N) time，为了节省时间，使用dict存储扫描过得数字。key为数字，value为位置
如果target减去当前数字刚好在dict里面，则找到了一组满足条件的数字<p>



```python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        d = {}
        for i in range(len(nums)):
            if target - nums[i] in d:
                return [d[target-nums[i]],i]
            else:
                d[nums[i]] = i
                
```
