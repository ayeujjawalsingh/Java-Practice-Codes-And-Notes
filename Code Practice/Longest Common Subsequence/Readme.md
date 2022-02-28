## Longest Common Subsequence
Given two sequences, find the length of longest subsequence present in both of them. Both the strings are of uppercase. [🔗Goto](https://practice.geeksforgeeks.org/problems/longest-common-subsequence-1587115620/1/?page=2&difficulty[]=1&status[]=unsolved&sortBy=submissions#) 

```
Example 1:

Input:
A = 6, B = 6
str1 = ABCDGH
str2 = AEDFHR
Output: 3
Explanation: LCS for input Sequences
“ABCDGH” and “AEDFHR” is “ADH” of
length 3.

Example 2:

Input:
A = 3, B = 2
str1 = ABC
str2 = AC
Output: 2
Explanation: LCS of "ABC" and "AC" is
"AC" of length 2.
```
<details>
<summary>Full Code</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class GFG {
	public static void main (String[] args) {

		Scanner sc=new Scanner(System.in);
		int test=sc.nextInt();
		while(test-- > 0){
		    int p=sc.nextInt();             // Take size of both the strings as input
		    int q=sc.nextInt();
		    
		    String s1=sc.next();            // Take both the string as input
	        String s2=sc.next();
		    
		    Solution obj = new Solution();
		    
		    System.out.println(obj.lcs(p, q, s1, s2));
		}
	}
}// } Driver Code Ends


class Solution
{
    //Function to find the length of longest common subsequence in two strings.
    static int lcs(int x, int y, String s1, String s2)
    {
        // your code here
        int dp[][]=new int[s1.length()+1][s2.length()+1];
        for(int i=s1.length()-1;i>=0;i--){
           for(int j=s2.length()-1;j>=0;j--){
               if(s1.charAt(i)==s2.charAt(j)){
                   dp[i][j]=1+dp[i+1][j+1];
               }else{
                   int ans1=dp[i][j+1];
                   int ans2=dp[i+1][j];
                   dp[i][j]=Math.max(ans1,ans2);
               }
           }
       }
       return dp[0][0];
    }
    
}
```
</details>

```java
class Solution
{
    //Function to find the length of longest common subsequence in two strings.
    static int lcs(int x, int y, String s1, String s2)
    {
        // your code here
        int dp[][]=new int[s1.length()+1][s2.length()+1];
        for(int i=s1.length()-1;i>=0;i--){
           for(int j=s2.length()-1;j>=0;j--){
               if(s1.charAt(i)==s2.charAt(j)){
                   dp[i][j]=1+dp[i+1][j+1];
               }else{
                   int ans1=dp[i][j+1];
                   int ans2=dp[i+1][j];
                   dp[i][j]=Math.max(ans1,ans2);
               }
           }
       }
       return dp[0][0];
    }
    
}
```
