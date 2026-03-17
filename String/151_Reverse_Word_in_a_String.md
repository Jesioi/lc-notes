# 151. Reverse Words in a String

---
## Code
```java
class Solution {
    //remove extra space
    //reverse string
    //reverse vocab
    public String reverseWords(String s) {
        StringBuilder sb = removeSpace(s);
        reverse(sb, 0, sb.length() - 1);
        word(sb);
        return sb.toString();
    }

    //remove extra space
    private StringBuilder removeSpace(String s) {
        int i = 0;
        int j = s.length() - 1;
        while (s.charAt(i) == ' ') i++;
        while (s.charAt(j) == ' ') j--;
        StringBuilder sb = new StringBuilder();
        while (i <= j) {
            //如果当前字符不是空格 ｜｜ 当前字符是空格但 sb 末尾不是空格
            if (s.charAt(i) != ' ' || sb.charAt(sb.length() - 1) != ' '){
                sb.append(s.charAt(i));  
            }
            i++;
        }
        return sb;
    }

    //reverse string
    public void reverse(StringBuilder sb, int i, int j) {
        while (i <= j) {
            char temp = sb.charAt(i);
            sb.setCharAt(i, sb.charAt(j));
            sb.setCharAt(j, temp);
            i++;
            j--;
        }
    }

    private void word(StringBuilder sb) {
        int i = 0;
        int j = 0;
        while (i < sb.length()) {
            while (j < sb.length() && sb.charAt(j) != ' ') {
                j++;
            }
            reverse(sb, i, j - 1);
            i = j + 1;
            j = i;
        }
    }
}

```
### Time and Space Complexity
- time: O(n)
- space: O(n)

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




