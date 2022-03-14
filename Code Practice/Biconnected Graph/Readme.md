## Biconnected Graph
Given a graph with n vertices, e edges and an array arr[] denoting the edges connected to each other, check whether it is Biconnected or not.
Note: The given graph is Undirected. [🔗Goto](https://practice.geeksforgeeks.org/problems/biconnected-graph2528/1#) 

```
Example 1:

Input:
n = 2, e = 1
arr = {0, 1}
Output:
1
Explanation:
       0
      /
     1
The above graph is Biconnected.

Example 2:

Input:
n = 3, e = 2
arr = {0, 1, 1, 2}
Output:
0
Explanation:
       0
      /
     1
      \
       2
The above graph is not Biconnected.
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
            String S[] = read.readLine().split(" ");
            int n = Integer.parseInt(S[0]);
            int e = Integer.parseInt(S[1]);
            
            String S1[] = read.readLine().split(" ");
            int[] arr = new int[2*e];
            
            for(int i=0; i<2*e; i++)
                arr[i] = Integer.parseInt(S1[i]);

            Solution ob = new Solution();
            System.out.println(ob.biGraph(arr,n,e));
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution {
    static int biGraph(int[] arr, int n, int e) {
        // code here
        int dp[] = new int[n];
        //Special case where number of vertices are two and they are connected.
        if(e==1 && n==2){
            return 1;
        }
        int n_e = 2*e;
        for(int i = 0;i<n_e;i+=2){
            dp[arr[i]]++;
            dp[arr[i+1]]++;
        }
        for(int i = 0; i<n;i++){
            if(dp[i]<2) return 0;
        }
        return 1;
    }
};
```
</details>

```java
class Solution {
    static int biGraph(int[] arr, int n, int e) {
        // code here
        int dp[] = new int[n];
        //Special case where number of vertices are two and they are connected.
        if(e==1 && n==2){
            return 1;
        }
        int n_e = 2*e;
        for(int i = 0;i<n_e;i+=2){
            dp[arr[i]]++;
            dp[arr[i+1]]++;
        }
        for(int i = 0; i<n;i++){
            if(dp[i]<2) return 0;
        }
        return 1;
    }
};
```