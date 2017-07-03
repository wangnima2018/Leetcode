
<h3>题意<h3>
<p>给出一组数，把这组数的所有排列可能性，都例举出来<p>


<h3>解题<h3>
<p>一个典型的循环递归法，解决问题，每次循环下，进行下一层递归<p>


<h3>细节<h3>
<p>每次往resL里面加入list的时候，list需要单独进行一次copy: newL = curL[:]
    在每次循环最后，减去list里面最后一个元素：del curL[-1] <p>


```python
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        resL = []
        curL = []
        self.helper(nums,curL,resL)
        return resL
    
    def helper(self,nums,curL,resL):
        if len(curL) == len(nums):
            newL = curL[:]
            resL.append(newL)
            return
        for i in range(len(nums)):
            if nums[i] not in curL:
                curL.append(nums[i])
                self.helper(nums,curL,resL)
                del curL[-1]
```
