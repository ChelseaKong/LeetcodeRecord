## 1768. Merge Strings Alternately - easy

You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return the merged string.

Example 1:

`Input: word1 = "ab", word2 = "pqrs"`

`Output: "apbqrs"`

`Explanation: Notice that as word2 is longer, "rs" is appended to the end.`

`word1:  a   b `

`word2:    p   q   r   s`

`merged: a p b q   r   s`

Constraints:

- 1 <= word1.length, word2.length <= 100
- word1 and word2 consist of lowercase English letters.

### Just Go - Java

```
class Solution {
    public String mergeAlternately(String word1, String word2) {
        char[] c1 = word1.toCharArray();
        char[] c2 = word2.toCharArray();
        int n1 = c1.length, n2 = c2.length;
        char[] ret = new char[n1+n2];
        int index = 0, i = 0, j = 0;
        int sameLength = 0;
        boolean flag = false;

        if ( n1 >= n2 ) {
            sameLength = n2;
        } else {
            sameLength = n1;
            flag = true;
        }

        for (i=0; i<sameLength; i++) {
            ret[index] = c1[i];
            index += 2;
        }
        index = 1;
        for (j=0; j<sameLength; j++) {
            ret[index] = c2[j];
            index += 2;
        }
        index --;

        while ( index < n1+n2 ) {
            if ( flag ) {
                ret[index] = c2[j++];
            } else {
                ret[index] = c1[i++];
            }
            index ++;
        }
        return new String(ret);
    }
}
```

#### Problems:
- Too long, not beautiful

#### Learned:
- Java: String to Char[]: use **toCharArray();**
- Java: Char[] to String: use **new String(char[] name);**
- Java: new char[]: use **char[] array = new char[length];** 

### Learning & Improvement




