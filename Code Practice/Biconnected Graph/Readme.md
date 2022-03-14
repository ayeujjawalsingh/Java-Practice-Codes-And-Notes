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