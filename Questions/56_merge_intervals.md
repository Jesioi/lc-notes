# 56. Merge Intervals

🔗 Link：https://leetcode.com/problems/merge-intervals/description/?envType=company&envId=amazon&favoriteSlug=amazon-thirty-days

---

## Approach

-
-

### Complexity

time: O(n log n) -> bottle neck: sorting
space: O(n)

## Input variation

- int[][] intervals
- streaming intervals: use treemap

---

## Code

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        List<int[]> res = new ArrayList<>();
        int[] cur = intervals[0];

        for (int i = 1; i < intervals.length; i++) {
            int[] interval = intervals[i];

            if (interval[0] <= cur[1]) {
                cur[1] = Math.max(cur[1], interval[1]);
            } else {
                res.add(cur);
                cur = interval;
            }
        }

        res.add(cur);

        return res.toArray(new int[res.size()][]);
    }
}



```
