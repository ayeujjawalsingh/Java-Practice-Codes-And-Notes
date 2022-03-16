## Nodes at given distance in binary tree
Find the number of unique words consisting of lowercase alphabets only of length N that can be formed with at-most K contiguous vowels. [🔗Goto](https://practice.geeksforgeeks.org/problems/7b9d245852bd8caf8a27d6d3961429f0a2b245f1/1#) 

```
Example 1:

Input:
N = 2
K = 0
Output:
441
Explanation:
Total of 441 unique words are possible
of length 2 that will have K( =0) vowels
together, e.g. "bc", "cd", "df", etc are
valid words while "ab" (with 1 vowel) is
not a valid word.

Example 2:

Input:
N = 1
K = 1
Output:
26
Explanation:
All the english alphabets including
vowels and consonants; as atmost K( =1)
vowel can be taken.
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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        while(t-- > 0)
        {
            int N = sc.nextInt();
            int K = sc.nextInt();

            Solution ob = new Solution();
            int ans = ob.kvowelwords(N,K);
            System.out.println(ans);
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution{
   public int kvowelwords(int N,int K){
       // code here
        double[][] dp = new double[N+1][K+1];
        double MOD = 1e9;
        MOD = MOD + 7;
        for(int i =0;i <= N;i++){
           
            for(int j = 0;j <= K;j++){
                if(i == 0){
                    dp[i][j] = 1;
                }else{
                    dp[i][j] = dp[i-1][K]*21%MOD;
                   
                    if(j > 0){
                        dp[i][j] = (dp[i][j] + dp[i-1][j-1]*5%MOD) % MOD;
                    }
                }
               
            }
       
        }
        return (int)dp[N][K];
    }
}
```
</details>

```java
class Solution{
   public int kvowelwords(int N,int K){
       // code here
        double[][] dp = new double[N+1][K+1];
        double MOD = 1e9;
        MOD = MOD + 7;
        for(int i =0;i <= N;i++){
           
            for(int j = 0;j <= K;j++){
                if(i == 0){
                    dp[i][j] = 1;
                }else{
                    dp[i][j] = dp[i-1][K]*21%MOD;
                   
                    if(j > 0){
                        dp[i][j] = (dp[i][j] + dp[i-1][j-1]*5%MOD) % MOD;
                    }
                }
               
            }
       
        }
        return (int)dp[N][K];
    }
}
```
