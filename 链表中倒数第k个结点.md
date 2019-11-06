# 链表中倒数第k个结点

## 题目描述
输入一个链表，输出该链表中倒数第k个结点。

### 解题思路：
为了实现只遍历链表一次就能找到倒数第k 个结点,我们可以定义两个指针。第一个指针从链表的头指针开始遍历向前走k-1步,第二个指针保持不动;从第k 步开始,第二个指针也开始从链表的头指针开始遍历。由于两个指针的距离保持在k-1 , 当第一个(走在前面的)指针到达链表的尾结点时,第二个指针(走在后面的) 指针正好是倒数第k 个结点。


### 代码：

```
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        if(k<1 || head == null){
            return null;
        }
        ListNode pointer = head;
        
        for(int i=1;i<k;i++){
            if(pointer.next !=null){
                pointer = pointer.next;
            }else{
                return null;
            }
        }
        while(pointer.next != null){
            head = head.next;
            pointer = pointer.next;
        }
        
        return head;
    }
}
```