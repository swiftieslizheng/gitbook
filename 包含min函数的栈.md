# 包含min函数的栈

## 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。


### 解题思路：
把每次的最小元素(之前的最小元素和新压入战的元素两者的较小值)都保存起来放到另外一个辅助栈里。

如果每次都把最小元素压入辅助栈, 那么就能保证辅助栈的栈顶一直都是最小元素.当最小元素从数据栈内被弹出之后,同时弹出辅助栈的栈顶元素,此时辅助栈的新栈顶元素就是下一个最小值。


### 代码：


```
import java.util.Stack;

    public class Solution {
        private Stack<Integer> stack = new Stack<Integer>();
        private Stack<Integer> minStack = new Stack<Integer>();

        public void push(int node) {
            stack.push(node);

            if(minStack.size() == 0 || node<minStack.peek()){
                minStack.push(node);
            }else{
                minStack.add(minStack.peek());
            }
        }

        public void pop(){
            if(stack.size() == 0){
                try {
                    throw new Exception("null");
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
            stack.pop();
            minStack.pop();
        }

        public int top() {
            int data = stack.pop();
            stack.push(data);
            return data;
        }

        public int min(){
            if(minStack.size() == 0){
                try {
                    throw new Exception("null");
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
            return minStack.peek();
        }
    }

```