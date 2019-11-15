# 和为S的两个数字

## 题目描述
输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

### 解题思路：
同样利用双指针法，找到的第一个符合的两个数就是乘积最小的。


### 代码：


```java
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> FindNumbersWithSum(int [] array, int sum) {
        ArrayList<Integer> list = new ArrayList<>();
        if(array == null || array.length<2) return list;
        int p1 =0,p2 = array.length-1;
        while(p1<p2){
            if(array[p1]+array[p2] == sum){
                list.add(array[p1]);
                list.add(array[p2]);
                return list;
            }else if(array[p1]+array[p2] < sum){
                p1++;
            }else{
                p2--;
            }
        }
        return list;
    }
}
```