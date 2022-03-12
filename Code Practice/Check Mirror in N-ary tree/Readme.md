## Check Mirror in N-ary tree 
Given two n-ary trees. Check if they are mirror images of each other or not. You are also given e denoting the number of edges in both trees, and two arrays, A[] and B[]. Each array has 2*e space separated values u,v denoting an edge from u to v for the both trees. [🔗Goto](https://practice.geeksforgeeks.org/problems/check-mirror-in-n-ary-tree1528/1#) 

```
Example 1:

Input:
n = 3, e = 2
A[] = {1, 2, 1, 3}
B[] = {1, 3, 1, 2}
Output:
1
Explanation:
   1          1
 / \        /  \
2   3      3    2 
As we can clearly see, the second tree
is mirror image of the first.
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
            String S2[] = read.readLine().split(" ");
            
            int[] A = new int[2*e];
            int[] B = new int[2*e];
            
            for(int i=0; i<2*e; i++)
            {
                A[i] = Integer.parseInt(S1[i]);
                B[i] = Integer.parseInt(S2[i]);
            }

            Solution ob = new Solution();
            System.out.println(ob.checkMirrorTree(n,e,A,B));
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution {
   static int checkMirrorTree(int n, int e, int[] A, int[] B) {
       HashMap<Integer,ArrayDeque<Integer>> h = new HashMap<Integer,ArrayDeque<Integer>>();
       
       for(int i=0;i<2*e;i+=2){
           if(h.containsKey(A[i])){
               h.get(A[i]).push(A[i+1]);
           }else{
               h.put(A[i], new ArrayDeque<Integer>());
               h.get(A[i]).push(A[i+1]);
           }
       }
       for(int i=0;i<2*e;i+=2){
           if(h.containsKey(B[i])){
               int t = h.get(B[i]).pop();
               if(t!=B[i+1]){
                   return 0;
               }
           }else{
               return 0;
           }
       }
       return 1;
   }
};
```
</details>

```java
class Solution {
   static int checkMirrorTree(int n, int e, int[] A, int[] B) {
       HashMap<Integer,ArrayDeque<Integer>> h = new HashMap<Integer,ArrayDeque<Integer>>();
       
       for(int i=0;i<2*e;i+=2){
           if(h.containsKey(A[i])){
               h.get(A[i]).push(A[i+1]);
           }else{
               h.put(A[i], new ArrayDeque<Integer>());
               h.get(A[i]).push(A[i+1]);
           }
       }
       for(int i=0;i<2*e;i+=2){
           if(h.containsKey(B[i])){
               int t = h.get(B[i]).pop();
               if(t!=B[i+1]){
                   return 0;
               }
           }else{
               return 0;
           }
       }
       return 1;
   }
};
```
