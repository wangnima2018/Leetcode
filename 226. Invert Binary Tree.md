
<h1>题意<h1>
<p>把整颗树的每个节点，的左右子树都相互调换下<p>

<h1>解题<h1>
<p>使用递归法，把每层的左右子数先保存，然后左右调换下，然后递归到下一层<p>



```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        self.helper(root)
        return root
    
    def helper(self,root):
        if root is not None:
            left = root.left
            right = root.right
            root.left = right
            root.right = left
            self.helper(root.left)
            self.helper(root.right)
 ```
