## Longest substring to form a Palindrome
Given a string S which only contains lowercase alphabets. Find the length of the longest substring of S such that the characters in it can be rearranged to form a palindrome. [🔗Goto](https://practice.geeksforgeeks.org/problems/longest-substring-whose-character-rearranged-can-form-a-palindrome/1#) 

```Example 1:

Input:
S = "aabe"
Output:
3
Explanation:
The substring "aab" can be rearranged to
"aba" which is the longest palindrome
possible for this String.

Example 2:
Input:
S = "adbabd"
Output:
6
Explanation:
The whole string “adbabd” can be
rearranged to form a palindromic substring.
One possible arrangement is "abddba".
Thus, output length of the string is 6. 

```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

class GFG {
    public static void main(String args[]) throws IOException {
        BufferedReader read =
            new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        while (t-- > 0) {
            String S = read.readLine();
            
            Solution ob = new Solution();
            System.out.println(ob.longestSubstring(S));
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution {
    static int longestSubstring(String s) {
        HashMap<Integer, Integer> index = new HashMap<>();

        int answer = 0;

        int mask = 0;
        index.put(mask, -1);

        for (int i = 0; i < s.length(); i++) {

            int temp = (int) s.charAt(i) - 'a';

            mask ^= (1 << temp);

            if (index.containsKey(mask)) {
                answer = Math.max(answer, i - index.get(mask));
            } else {
                index.put(mask, i);
            }

            for (int j = 0; j < 26; j++) {
                int mask2 = mask ^ (1 << j);
                if (index.containsKey(mask2)) {
                    answer = Math.max(answer, i - index.get(mask2));
                }
            }
        }
        return answer;
    }
};
```
</details>

```java
class Solution {
    static int longestSubstring(String s) {
        HashMap<Integer, Integer> index = new HashMap<>();

        int answer = 0;

        int mask = 0;
        index.put(mask, -1);

        for (int i = 0; i < s.length(); i++) {

            int temp = (int) s.charAt(i) - 'a';

            mask ^= (1 << temp);

            if (index.containsKey(mask)) {
                answer = Math.max(answer, i - index.get(mask));
            } else {
                index.put(mask, i);
            }

            for (int j = 0; j < 26; j++) {
                int mask2 = mask ^ (1 << j);
                if (index.containsKey(mask2)) {
                    answer = Math.max(answer, i - index.get(mask2));
                }
            }
        }
        return answer;
    }
};
```
