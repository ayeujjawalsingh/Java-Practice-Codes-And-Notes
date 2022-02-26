## Escape the Forbidden Forest
Penelope and her classmates are lost in the Forbidden Forest and the Devil is out to get them. But Penelope has magical powers that can build bridges across the dangerous river and take her friends to safety. The only bridges that can withstand the Devil's wrath are the ones built between two similar trees in the forest. 
Given str1 and str2 denoting the order of trees on either side of the river, find the maximum number of bridges that Penelope can build and save everyone from the Devil. 
Note: Each tree in the forest belongs to one of the 3 categories represented by * or # or @. [🔗Goto](https://practice.geeksforgeeks.org/problems/a4f19ea532cee502aabec77c07e0d0a45b76ecf9/1#) 

<details>
<summary>Full Code</summary>

```java

```
</details>

```java
// Dynamic programming(LCS)
// Approach1: Recursion
// Time Complexity: O(2^n)
// Result: TLE
class Sol
{
    public static int solve(String str1, int n1, String str2, int n2, int i, int j){
        if(i >= n1 || j >= n2){
            return 0;
        }
        if(str1.charAt(i) == str2.charAt(j)){
            return solve(str1, n1, str2, n2, i+1, j+1) + 1;
        }
        return Math.max(solve(str1, n1, str2, n2, i+1, j), solve(str1, n1, str2, n2, i, j+1));
    }
    public static int build_bridges(String str1 , String str2){
        return solve(str1, str1.length(), str2, str2.length(), 0, 0);
    }
}
```

```java
// Approach2: Top-Down
// Time Complexity:  O(N1 * N2), where N1 and N2 are lengths of the first and second string respectively. 
// Result: Accepted
class Sol
{
    public static int solve(String str1, int n1, String str2, int n2, int i, int j, int[][] dp){
        if(i >= n1 || j >= n2){
            return 0;
        }
        if(dp[i][j] != -1){
            return dp[i][j];
        }
        if(str1.charAt(i) == str2.charAt(j)){
            dp[i][j] = solve(str1, n1, str2, n2, i+1, j+1, dp) + 1;
            return dp[i][j];
        }
        dp[i][j] = Math.max(solve(str1, n1, str2, n2, i+1, j, dp), solve(str1, n1, str2, n2, i, j+1, dp));
        return dp[i][j];
    }
    public static int build_bridges(String str1 , String str2)
    {
       int n1 = str1.length();
       int n2 = str2.length();
       
       int[][] dp = new int[n1 + 1][n2 + 1];
       for(int[] row : dp){
           Arrays.fill(row, -1);
       }
       return solve(str1, n1, str2, n2, 0, 0, dp);
    }
}
```

```java
// Approach3: Bottom Approach
// Time Complexity:  O(N1 * N2), where N1 and N2 are lengths of the first and second string respectively.
// Result: Accepted
class Sol
{
    public static int build_bridges(String str1 , String str2)
    {
       int n1 = str1.length();
       int n2 = str2.length();
       
       int[][] dp = new int[n1 + 1][n2 + 1];
       for(int[] row : dp){
           Arrays.fill(row, -1);
       }
       for(int i = 0; i <= n1; i++){
           for(int j = 0; j <= n2; j++){
               if(i == 0 || j == 0){
                   dp[i][j] = 0;
               }
               else if(str1.charAt(i-1) == str2.charAt(j-1)){
                   dp[i][j] = dp[i-1][j-1] + 1;
               } else {
                   dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
               }
           }
       }
       return dp[n1][n2];
    }
}
```