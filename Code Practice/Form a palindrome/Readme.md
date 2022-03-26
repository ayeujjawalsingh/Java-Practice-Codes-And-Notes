## Form a palindrome
Given a string, find the minimum number of characters to be inserted to convert it to palindrome.
For Example:
ab: Number of insertions required is 1. bab or aba
aa: Number of insertions required is 0. aa
abcd: Number of insertions required is 3. dcbabcd [🔗Goto](https://practice.geeksforgeeks.org/problems/form-a-palindrome2544/1#) 

```
Example 1:

Input:
abcd
Output:
3
Explanation:
Here we can append 3 characters in the 
beginning,and the resultant string will 
be a palindrome ("dcbabcd").
Example 2:

Input:
aba
Output:
0
Explanation:
Given string is already a pallindrome hence
no insertions are required.
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
        BufferedReader read = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        while(t-- > 0)
        {
            
            String S = read.readLine().trim();
            Solution ob = new Solution();
            System.out.println(ob.findMinInsertions(S));
        }
    }
}// } Driver Code Ends


//User function Template for Java

/*
->To find Longest Common Subseqence
https://youtu.be/-zI4mrF2Pb4 
->Minimum Insertion to make Palindrome
https://youtu.be/xPBLEj41rFU
->Minimum number of characters to be inserted to convert it to palindrome is equal to
->ans = length of String - Longest Common Subsequence (S, S.reverse())
*/
class Solution{
   int[][] arr;
   int findMinInsertions(String S){
       // code here
       arr = new int[S.length()][S.length()];
       String S2 = new StringBuilder(S).reverse().toString();
       
       return S.length()-lcs(S, S2, S.length()-1, S2.length()-1);
   }
   
   int lcs(String s1, String s2, int i, int j)
   {
       if(i<0 || j<0) return 0;
       if(arr[i][j] != 0) return arr[i][j];
       if(s1.charAt(i)==s2.charAt(j)) 
       {
           return arr[i][j] = (1 + lcs(s1, s2, i-1, j-1));
       }
       
       return arr[i][j] = Math.max(lcs(s1, s2, i-1, j), lcs(s1, s2, i, j-1));
   }
}
```
</details>

```java
/*
->To find Longest Common Subseqence
https://youtu.be/-zI4mrF2Pb4 
->Minimum Insertion to make Palindrome
https://youtu.be/xPBLEj41rFU
->Minimum number of characters to be inserted to convert it to palindrome is equal to
->ans = length of String - Longest Common Subsequence (S, S.reverse())
*/
class Solution{
   int[][] arr;
   int findMinInsertions(String S){
       // code here
       arr = new int[S.length()][S.length()];
       String S2 = new StringBuilder(S).reverse().toString();
       
       return S.length()-lcs(S, S2, S.length()-1, S2.length()-1);
   }
   
   int lcs(String s1, String s2, int i, int j)
   {
       if(i<0 || j<0) return 0;
       if(arr[i][j] != 0) return arr[i][j];
       if(s1.charAt(i)==s2.charAt(j)) 
       {
           return arr[i][j] = (1 + lcs(s1, s2, i-1, j-1));
       }
       
       return arr[i][j] = Math.max(lcs(s1, s2, i-1, j), lcs(s1, s2, i, j-1));
   }
}
```