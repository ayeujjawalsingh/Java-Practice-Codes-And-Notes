## Bitwise AND of the Array
Given an array A[ ] of N integers and an integer X. In one operation, you can change the ith element of the array to any integer value where 1 ≤ i ≤ N. Calculate minimum number of such operations required such that the bitwise AND of all the elements of the array is strictly greater than X. [🔗Goto](https://practice.geeksforgeeks.org/problems/5109f04a157ca54bbb373477b1afeec22e7f1812/1) 

```
Example 1:

Input:
N = 4, X = 2
A[] = {3, 1, 2, 7}
Output: 
2
Explanation: 
After performing two operations:
Modified array: {3, 3, 11, 7} 
Now, Bitwise AND of all the elements
is 3 & 3 & 11 & 7 = 3 

Example 2:

Input:
N = 3, X = 1
A[] = {2, 2, 2}
Output: 
0
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*; 
class GFG{
    public static void main(String args[]) throws IOException { 
        BufferedReader read = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());
        
        while(t-- > 0){
            String input_line[] = read.readLine().trim().split("\\s+");
            int N = Integer.parseInt(input_line[0]);
            int X = Integer.parseInt(input_line[1]);
            input_line = read.readLine().trim().split("\\s+");
            int A[]= new int[N];
            for(int i = 0; i < N; i++)
                A[i] = Integer.parseInt(input_line[i]);
            Solution ob = new Solution();
            int ans = ob.count(N, A, X); 
            System.out.println(ans);
        }
    } 
}// } Driver Code Ends


//User function Template for Java
class Solution 
{ 
    int count(int N, int A[], int X) 
    {   
        int ans = N;
        int mask = 0;
        
        for(int i=30;i>=0;i--){
            int bitVal = ((1 << i) & X);
            if(bitVal > 0){
                mask ^= (1<<i);
            }
            else{
                int count = 0;
                int greaterMask = (mask ^ (1 << i));
                for(int elem : A){
                    int val = (greaterMask & elem);
                    if(val != greaterMask){
                        count++;
                    }
                }
                ans = Math.min(ans, count);
            }
        }
        return ans;
    }
} 
```
</details>

```java
class Solution 
{ 
    int count(int N, int A[], int X) 
    {   
        int ans = N;
        int mask = 0;
        
        for(int i=30;i>=0;i--){
            int bitVal = ((1 << i) & X);
            if(bitVal > 0){
                mask ^= (1<<i);
            }
            else{
                int count = 0;
                int greaterMask = (mask ^ (1 << i));
                for(int elem : A){
                    int val = (greaterMask & elem);
                    if(val != greaterMask){
                        count++;
                    }
                }
                ans = Math.min(ans, count);
            }
        }
        return ans;
    }
}
```