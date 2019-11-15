# 和为S的连续正数序列

## 题目描述
小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!

##### 输出描述:
    输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序

### 解题思路：
双指针技术，就是相当于有一个窗口，窗口的左右两边就是两个指针，我们根据窗口内值之和来确定窗口的位置和宽度。


### 代码：


```java
import java.util.ArrayList;
public class Solution {
    public ArrayList<ArrayList<Integer>> FindContinuousSequence(int sum) {
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        int p1 = 1,p2 = 2;
        while(p1<p2){
            //由于是连续的，差为1的一个序列，那么求和公式是(a0+an)*n/2
            int n = (p1+p2)*(p2-p1+1)/2;
            if(n == sum){
                ArrayList<Integer> list = new ArrayList<>();
                for(int i=p1;i<=p2;i++){
                    list.add(i);
                }
                res.add(list);
                p1++;

            }else if(n>sum){
                //如果当前窗口内的值之和大于sum，那么左边窗口右移一下
                p1++;
            }else{
                //如果当前窗口内的值之和小于sum，那么右边窗口右移一下
                p2++;
            }
        }
        return res;
    }
}
```