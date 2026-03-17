# 202. Happy Number
---
## Code
```java
class Solution {
    public boolean isHappy(int n) {
        Set<Integer> list = new HashSet<>(); //用set因为出现重复的话说明就已经进入无限循环了，不用再做下去了

        while (n != 1 && !list.contains(n)){
            list.add(n); 
            // 先写add，不是记录数据，而是为了检查当前状态，如果先写getNumber 那最开始的数据就少记入一次
            n = getNumber(n);
        }
        return n == 1;   
        //return n ==1 根据上面while的结果进行对比，hapy的话 n会等于1，返回true，进入循环的话，n ！=1 返回false
    }

    public int getNumber(int n){ //计算当前的sum
        int sum = 0;
        int temp = 0;
        while (n > 0){
            temp = n % 10; //记个位数
            sum += temp * temp;
            n = n /10; //每次只处理个位数，/ 10 更新数字，直到没有个位数需要处理
        }
        return sum;
    }
}

```
### Time and Space Complexity
- time: O(log n)
  - Happy Number 每次需要把数字按位拆分计算平方和，处理的位数与数字的位数成正比，
  - 而一个数的位数是 log₁₀(n)，因此每次计算是 O(log n)，整体时间复杂度也是 O(log n)。
- space: O(1)

## Approach
1)
2)


### Interview
1) Clarify the problem，define input, output and edge cases.
2) Approaches
3) Why it works
4) Time and space complexity
-
- 