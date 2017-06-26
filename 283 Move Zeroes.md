


<h1>题意<h1>
<p>比较明确，就是把所有非0的数字，移动到最左边，并且保持数字的相对顺序<p>

<h1>题解<h1>
<p>实际上就是将所有的非0数向前尽可能的压缩，最后把没压缩的那部分全置0就行了。
比如103040，先压缩成134，剩余的3为全置为0。过程中需要一个指针记录压缩到的位置。<p>


```python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """

        
        pos = 0
        length = len(nums)
        for i in range(length):
            if nums[i] != 0:
                nums[pos] = nums[i]
                pos += 1
        
        while pos < length:
            nums[pos] = 0
            pos += 1
```
