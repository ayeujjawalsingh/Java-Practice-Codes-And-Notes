## Choose and Swap
You are given a string s of lower case english alphabets. You can choose any two characters in the string and replace all the occurences of the first character with the second character and replace all the occurences of the second character with the first character. Your aim is to find the lexicographically smallest string that can be obtained by doing this operation at most once.[🔗Goto](https://practice.geeksforgeeks.org/problems/choose-and-swap0531/1) 

```
Example 1:

Input:
A = "ccad"
Output: "aacd"
Explanation:
In ccad, we choose a and c and after 
doing the replacement operation once we get, 
aacd and this is the lexicographically
smallest string possible. 
 
Example 2:

Input:
A = "abba"
Output: "abba"
Explanation:
In abba, we can get baab after doing the 
replacement operation once for a and b 
but that is not lexicographically smaller 
than abba. So, the answer is abba. 

```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

class GFG
{
    public static void main(String args[])throws IOException
    {
        
        Solution obj = new Solution();
        BufferedReader read = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        while(t-- > 0)
        {
            String A = read.readLine().trim();
            
            String ans = obj.chooseandswap(A);
            System.out.println(ans);
        }
    }
}

// } Driver Code Ends


//User function Template for Java



class Solution{
    String chooseandswap(String A){
        // Code Here
        char[] a = A.toCharArray();
        
        boolean[] isPresent = new boolean[26];
        boolean[] visited = new boolean[26];
        
        int n = A.length();
        for (char currentChar: a) {
            isPresent[currentChar - 'a'] = true;
        }
        
        for (char currentChar: a) {
            for (int j = 0 ; j < currentChar - 'a' ; j++) {
                if (isPresent[j] && !visited[j]) {
                    return swap(a, currentChar, (char)(j+'a'));
                }
            }
            visited[currentChar - 'a'] = true;
        }
        
        return A;
    }
    
    private String swap(char[] a, char x, char y) {
        for (int i = 0 ; i < a.length ; i++) {
            if (a[i] == x) {
                a[i] = y;
            } else if (a[i] == y) {
                a[i] = x;
            }
        }
        return new String(a);
    }
}
```
</details>

```java
class Solution{
    String chooseandswap(String A){
        // Code Here
        char[] a = A.toCharArray();
        
        boolean[] isPresent = new boolean[26];
        boolean[] visited = new boolean[26];
        
        int n = A.length();
        for (char currentChar: a) {
            isPresent[currentChar - 'a'] = true;
        }
        
        for (char currentChar: a) {
            for (int j = 0 ; j < currentChar - 'a' ; j++) {
                if (isPresent[j] && !visited[j]) {
                    return swap(a, currentChar, (char)(j+'a'));
                }
            }
            visited[currentChar - 'a'] = true;
        }
        
        return A;
    }
    
    private String swap(char[] a, char x, char y) {
        for (int i = 0 ; i < a.length ; i++) {
            if (a[i] == x) {
                a[i] = y;
            } else if (a[i] == y) {
                a[i] = x;
            }
        }
        return new String(a);
    }
}
```
