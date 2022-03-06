## Compute Before Matrix
For a given 2D Matrix before, the corresponding cell (x, y) of the after matrix is calculated as follows: 


Given an N*M 2D-Matrix after, your task is to find the corresponding before matrix for the given matrix.[🔗Goto](https://practice.geeksforgeeks.org/problems/85781966a9db2a1ac17eaaed26a947eba5740d56/1#) 

```
Example 1:

Input:
N = 2, M = 3
after[][] = {{1, 3, 6},
            {3, 7, 11}}
Output:
1 2 3
2 2 1
Explanation:
The before matrix for the given after matrix
matrix is {{1, 2, 3}, {2, 2, 1}}.

Example 2:

Input: 
N = 1, M = 3
after[][] = {{1, 3, 5}}
Output:
1 2 2
Explanation: 
The before matrix for the given after matrix
is {{1, 2, 2}}.
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
        PrintWriter out = new PrintWriter(System.out);
        int t = Integer.parseInt(read.readLine());
        while (t-- > 0) {
            String S[] = read.readLine().split(" "); 
            int N = Integer.parseInt(S[0]);
            int M = Integer.parseInt(S[1]);
            
            int[][] mat = new int[N][M];
            for(int i=0; i<N; i++)
            {
                String St[] = read.readLine().split(" "); 
                for(int j=0; j<M; j++)
                {
                    mat[i][j] = Integer.parseInt(St[j]);
                }
            }
            
            Solution ob = new Solution();
            int[][] before = ob.computeBeforeMatrix(N,M,mat);
            for(int i=0; i<N;i++){
                for(int j = 0; j<M;j++){
                    out.print(before[i][j]);
                    out.print(' ');
                    
                }
                out.println();
            }
        }
        out.flush();
    }
}// } Driver Code Ends


//User function Template for Java

class Solution{
    public int[][] computeBeforeMatrix(int N, int M,int[][] after ){
        // Code here
        int res[][] = new int[N][M];
        for(int i = 0;i<N;i++){
            for(int j = 0;j<M;j++){
                if(i==0 && j==0){
                    res[i][j] = after[i][j];
                }
                else if(i ==0 && j>=0){
                    res[i][j] = after[i][j] - after[i][j-1];
                }
                else if(i>=0 && j==0){
                    res[i][j] = after[i][j] - after[i-1][j];
                }
                else{
                    res[i][j] = after[i][j] - after[i][j-1] - after[i-1][j] + after[i-1][j-1];
                }
            }
        }
        return res;
    }
}
```
</details>

```java
class Solution{
    public int[][] computeBeforeMatrix(int N, int M,int[][] after ){
        // Code here
        int res[][] = new int[N][M];
        for(int i = 0;i<N;i++){
            for(int j = 0;j<M;j++){
                if(i==0 && j==0){
                    res[i][j] = after[i][j];
                }
                else if(i ==0 && j>=0){
                    res[i][j] = after[i][j] - after[i][j-1];
                }
                else if(i>=0 && j==0){
                    res[i][j] = after[i][j] - after[i-1][j];
                }
                else{
                    res[i][j] = after[i][j] - after[i][j-1] - after[i-1][j] + after[i-1][j-1];
                }
            }
        }
        return res;
    }
}
```
