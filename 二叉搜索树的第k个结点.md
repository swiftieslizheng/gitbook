# 二叉搜索树的第k个结点

## 题目描述
给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）    中，按结点数值大小顺序第三小结点的值为4。

### 解题思路：
二叉搜索树按照中序遍历的顺序打印出来正好就是排序好的顺序。 所以，按照中序遍历顺序找到第k个结点就是结果。


### 代码：


```java
public class Solution {
    int count = 0;
    TreeNode KthNode(TreeNode pRoot, int k)
    {
        if(count>k || pRoot == null) return null;
        TreeNode temp = pRoot;
        Stack<TreeNode> stack = new Stack<>();
        TreeNode ans = null;
        while(temp != null || !stack.isEmpty()){
            while(temp !=null){
                stack.push(temp);
                temp = temp.left;
            }
            TreeNode node =  stack.pop();
            count++;
            if(count == k){
                ans = node;
            }
            temp = node.right;
        }
        return ans;
    }
}
```