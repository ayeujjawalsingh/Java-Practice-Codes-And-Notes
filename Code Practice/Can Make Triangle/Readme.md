## Can Make Triangle 
Given an array A[] of N elements, You'd like to know how many triangles can be formed with side lengths equal to adjacent elements from A[].

Construct an array of integers of length N - 2 where ith element is equal to 1 if it is possible to form a triangle with side lengths A[i], A[i+1], and A[i+2]. otherwise 0.

Note: A triangle can be formed with side lengths a, b and c if a+b>c and a+c>b and b+c>a. [🔗Goto](https://practice.geeksforgeeks.org/problems/51b7f8fb8b33d657a857f230361b7dad6565ce62/1#) 

```
Example 1:

Input:
N = 4
A[] = {1, 2, 2, 4}
Output:
1 0
Explanation:
output[0] = 1 because we can form a 
triangle with side lengths 1,2 and 2.
output[1] = 0 because 2+2<4 so, we cannot 
form a triangle with side lengths 2,2 and 4.
Example 2:

Input: 
N = 5
A[] = {2, 10, 2, 10, 2}
Output:
0 1 0
Explanation:
output[0] = 0 because 2+2<10 so, we cannot
form a triangle with side lengths 2, 10 and 2. 
output[1] = 1 we can form a triangle with 
side lengths 10,2 and 10. 
output[1] = 0 because 2+2<10 so, we can
form a triangle with side lengths 2, 10 and 2. 
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*; 

class FastReader{ 
    BufferedReader br; 
    StringTokenizer st; 

    public FastReader(){ 
        br = new BufferedReader(new InputStreamReader(System.in)); 
    } 

    String next(){ 
        while (st == null || !st.hasMoreElements()){ 
            try{ st = new StringTokenizer(br.readLine()); } catch (IOException  e){ e.printStackTrace(); } 
        } 
        return st.nextToken(); 
    } 

    String nextLine(){ 
        String str = ""; 
        try{ str = br.readLine(); } catch (IOException e) { e.printStackTrace(); } 
        return str; 
    } 
    
    Integer nextInt(){
        return Integer.parseInt(next());
    }
}

class GFG{
    public static void main(String args[]) throws IOException { 
        FastReader read = new FastReader();
        int t = read.nextInt();
        PrintWriter out = new PrintWriter(System.out);
        while(t-- > 0){
            int N = read.nextInt();
            int A[]= new int[N];
            for(int i = 0; i < N; i++)
                A[i] = read.nextInt();

            Solution ob = new Solution();
            int ans[] = ob.canMakeTriangle(A, N); 
            for (int i=0;i<ans.length;i++) 
                out.print(ans[i]+" "); 
            out.println();
        }
        out.flush();
    } 
} // } Driver Code Ends


//User function Template for Java
class Solution 
{ 
    int[] canMakeTriangle(int A[], int N) 
    { 
        int []res=new int [N-2];
        for (int i = 0; i < N-2; i++) {
            if(A[i]+A[i+1]>A[i+2] && A[i]+A[i+2]>A[i+1] && A[i+1]+A[i+2]>A[i])
                res[i]=1;
            else res[i]=0;
        }
        return res;
    }
}
```
</details>

```java
class Solution 
{ 
    int[] canMakeTriangle(int A[], int N) 
    { 
        int []res=new int [N-2];
        for (int i = 0; i < N-2; i++) {
            if(A[i]+A[i+1]>A[i+2] && A[i]+A[i+2]>A[i+1] && A[i+1]+A[i+2]>A[i])
                res[i]=1;
            else res[i]=0;
        }
        return res;
    }
}
```
