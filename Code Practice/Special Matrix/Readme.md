## Special Matrix
You are given a matrix having n rows and m columns. The special property of this matrix is that some of the cells of this matrix are blocked i.e. they cannot be reached. Now you have to start from the cell (1,1) and reach the end (n,m) provided during the journey you can move horizontally right from the current cell or vertically down from the current cell. Can you answer the number of ways you can traverse the matrix obeying the above constraints starting from (1,1) and ending at (n,m). [🔗Goto](https://practice.geeksforgeeks.org/problems/special-matrix4201/1#) 

```
Example 1:

Input: n = 3, m = 3, k = 2,
blocked_cells = {{1,2},{3,2}}.
Output: 1
Explanation: There is only one path from
(1,1) to(3,3) which is (1,1)->(2,1)->(2,2)->
(2,3)->(3,3).

Example 2:

Input: n = 5, m = 5, k = 1,
blocked_cells = {{5,5}}
Output: 0
Explanation: There is no path to reach at 
(5,5) beacuse (5,5) is blocked.
```
<details>
<summary>Full Code</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;
class GFG
{
    public static void main(String[] args) throws IOException
    {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int T = Integer.parseInt(br.readLine().trim());
        while(T-->0)
        {
            String[] s = br.readLine().trim().split(" ");
            int n = Integer.parseInt(s[0]);
            int m = Integer.parseInt(s[1]);
            int k = Integer.parseInt(s[2]);
            int[][] blocked_cells = new int[k][2];
            for(int i = 0; i < k; i++){
                String[] s1 = br.readLine().trim().split(" ");
                for(int j = 0; j < 2; j++){
                    blocked_cells[i][j] = Integer.parseInt(s1[j]);
                }
            }
            Solution obj = new Solution();
            int ans = obj.FindWays(n, m, blocked_cells);
            System.out.println(ans);

        }
    }
}
// } Driver Code Ends


//User function Template for Java

class Solution
{
    public int FindWays(int n, int m, int[][] blockedCell)
    {
        int mod = 1000000007;
        int matrix[][] = new int[n+1][m+1];
        //marketing invalid cell in dp matrix
        for(int i = 0;i<blockedCell.length;i++){
            matrix[blockedCell[i][0]][blockedCell[i][1]] = -1;
        }
        //initial fill
        for(int i = 0;i<=n;i++){
            if(matrix[i][1]!=-1) matrix[i][1] = 1;
        }
        for(int j = 0;j<= m;j++){
            if(matrix[1][j]!=-1) matrix[0][1] = 1;
        }
        //DP Work
        for(int i = 1;i<=n;i++){
            for(int j=1;j<=m;j++){
                if(matrix[i][j] == -1){
                    continue;
                }
                if(matrix[i-1][j] != -1 && matrix[i][j-1] != -1){
                    matrix[i][j] = (matrix[i-1][j] + matrix[i][j-1])%mod;
                }
                else if(matrix[i-1][j] != -1){
                    matrix[i][j] = matrix[i-1][j];
                }
                else if(matrix[i][j-1] != -1){
                    matrix[i][j] = matrix[i][j-1];
                }
                else{
                    matrix[i][j] = -1;
                }
            }
        }
        //handling 1 base condition
        if(matrix[n][m] < 0){
            return 0;
        }else{
            return matrix[n][m];
        }
    }
}
```
</details>

```java
class Solution
{
    public int FindWays(int n, int m, int[][] blockedCell)
    {
        int mod = 1000000007;
        int matrix[][] = new int[n+1][m+1];
        //marketing invalid cell in dp matrix
        for(int i = 0;i<blockedCell.length;i++){
            matrix[blockedCell[i][0]][blockedCell[i][1]] = -1;
        }
        //initial fill
        for(int i = 0;i<=n;i++){
            if(matrix[i][1]!=-1) matrix[i][1] = 1;
        }
        for(int j = 0;j<= m;j++){
            if(matrix[1][j]!=-1) matrix[0][1] = 1;
        }
        //DP Work
        for(int i = 1;i<=n;i++){
            for(int j=1;j<=m;j++){
                if(matrix[i][j] == -1){
                    continue;
                }
                if(matrix[i-1][j] != -1 && matrix[i][j-1] != -1){
                    matrix[i][j] = (matrix[i-1][j] + matrix[i][j-1])%mod;
                }
                else if(matrix[i-1][j] != -1){
                    matrix[i][j] = matrix[i-1][j];
                }
                else if(matrix[i][j-1] != -1){
                    matrix[i][j] = matrix[i][j-1];
                }
                else{
                    matrix[i][j] = -1;
                }
            }
        }
        //handling 1 base condition
        if(matrix[n][m] < 0){
            return 0;
        }else{
            return matrix[n][m];
        }
    }
}
```
