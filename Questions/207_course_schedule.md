# 207. Course Schedule

🔗 Link：https://leetcode.com/problems/course-schedule/description/?envType=company&envId=amazon&favoriteSlug=amazon-thirty-days

---

## Approach

- bfs
- dfs
  - check if it has cycle by dfs, graph dfs with state

### Complexity

time: O(V + E)
space: O(V + E)

## Input variation

- int[][] prerequisites
- Map<String, List<String>> prereq

---

## Code

```java
//dfs 版
//input Map<String, List<String>>

class CheckCourse {
    public boolean course(Map<String, List<String>> courses) {
        Map<String, Integer> state = new HashMap<>();

        // 把所有 node 都放进去：key + value 里的 course
        for (String course : courses.keySet()) {
            state.putIfAbsent(course, 0);

            for (String next : courses.get(course)) {
                state.putIfAbsent(next, 0);
            }
        }

        for (String course : state.keySet()) {
            if (dfs(courses, state, course)) {
                return false;
            }
        }

        return true;
    }

    private boolean dfs(Map<String, List<String>> courses, Map<String, Integer> state, String course) {
        if (state.get(course) == 1) return true;   // cycle
        if (state.get(course) == 2) return false;  // already checked

        state.put(course, 1);

        //getOrDefault: prevent null pointer exception
        for (String next : courses.getOrDefault(course, new ArrayList<>())) {
            if (dfs(courses, state, next)) {
                return true;
            }
        }

        state.put(course, 2);
        return false;
    }
}



```
