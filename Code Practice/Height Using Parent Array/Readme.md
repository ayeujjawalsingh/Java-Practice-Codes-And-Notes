## Height Using Parent Array
Given a parent array arr[] of a binary tree of N nodes. Element at index i in the array arr[] represents the parent of ith node, i.e, arr[i] = parent(i). Find the height of this binary tree.
Note: There will be a node in the array arr[], where arr[i] = -1, which means this node is the root of binary tree. [🔗Goto](https://practice.geeksforgeeks.org/problems/height-using-parent-array4103/1#) 

```
Example 1:

Input: N = 7
arr = {-1, 0, 0, 1, 1, 3, 5}
Output: 5
Explanation: Tree formed is:
                    0
                   / \
                  1   2
                 / \
                3   4
               /
              5
             /
            6      Height of the tree= 5
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

class GFG{
    public static void main(String args[])throws IOException
    {
        BufferedReader in = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(in.readLine());
        while(t-- > 0){
            int N = Integer.parseInt(in.readLine());
            String a[] = in.readLine().trim().split("\\s+");
            int arr[] = new int[N];
            for(int i = 0;i < N;i++)
                arr[i] = Integer.parseInt(a[i]);
            
            Solution ob = new Solution();
            System.out.println(ob.findHeight(N, arr));
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution{
    static int findHeight(int n, int arr[]){
        int height = 1;
        int i=n-1;
        while(i>=0){
            i = arr[i];
            height++;
        }
        return --height;
    }
}
```
</details>

```java
class Solution{
    static int findHeight(int n, int arr[]){
        int height = 1;
        int i=n-1;
        while(i>=0){
            i = arr[i];
            height++;
        }
        return --height;
    }
}
```
