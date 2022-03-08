## Reverse a string using Stack
You are given a string S, the task is to reverse the string using stack.[🔗Goto](https://practice.geeksforgeeks.org/problems/reverse-a-string-using-stack/1#) 

```
Example 1:

Input: S="GeeksforGeeks"
Output: skeeGrofskeeG
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

class GFG {
	public static void main (String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while(t-- > 0){
            Solution obj = new Solution();
            System.out.println(obj.reverse(sc.next()));
        }
	}
}
// } Driver Code Ends


class Solution {
    public String reverse(String S){
        Stack<Character> stack=new Stack<>();
        for(int i=0;i<S.length();i++){
            stack.push(S.charAt(i));
        }
        StringBuilder ans =new StringBuilder();
        while(!stack.empty())
            ans.append(stack.pop());
        return ans.toString();
    }
}
```
</details>

```java
class Solution {
    public String reverse(String S){
        Stack<Character> stack=new Stack<>();
        for(int i=0;i<S.length();i++){
            stack.push(S.charAt(i));
        }
        StringBuilder ans =new StringBuilder();
        while(!stack.empty())
            ans.append(stack.pop());
        return ans.toString();
    }
}
```
