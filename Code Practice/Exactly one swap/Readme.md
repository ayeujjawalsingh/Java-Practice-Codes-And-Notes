## Rotate and delete
Given an array arr[] of N integers. Do the following operation n-1 times. For every Kth operation:[🔗Goto](https://practice.geeksforgeeks.org/problems/rotate-and-delete-1587115621/1/?page=2&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Strings&sortBy=accuracy#) 

Right rotate the array clockwise by 1.
Delete the (n-k+1)th last element.
Now, find the element which is left at last.

Input:
The first line of input contains an integer T denoting the number of test cases. Then T test cases follows. Each test case contains two lines. The first line of each test case contains an integer N. Then in the next line are N space separated values of the array arr[].

Output:
For each test case in a new line print the required result.

User Task:
The task is to complete the function rotateDelete() which does operations as per given query.

Constraints:
1 <= T <= 110
1 <= N <= 106
1 <= A[i] <= 107


```
Example:
Input:
2
4
1 2 3 4
6
1 2 3 4 5 6

Output:
2
3
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
            String S = read.readLine().trim();
            Solution ob = new Solution();
            long ans = ob.countStrings(S); 
            System.out.println(ans);
        }
    } 
} // } Driver Code Ends


//User function Template for Java
class Solution 
{ 
    long countStrings(String S) 
    { 
        // code here
        long a[] = new long[26];
        int y = 0;
        long l = S.length();
        for(int i = 0;i<l;i++){
            char ch = S.charAt(i);
            a[ch-'a']++;
        }
        long sum = 0;
        long ans = (l*(l-1))/2;
        for(int i =0;i<26;i++){
            if(a[i]>=2){
                long l1=(a[i]*(a[i]-1))/(long)2;
                sum+=l1;
                y++;
            }
        }
        ans -= sum;
        if(sum>0)
            ans+=1;
        return ans;
    }
}
```
</details>

```java
class Solution 
{ 
    long countStrings(String S) 
    { 
        // code here
        long a[] = new long[26];
        int y = 0;
        long l = S.length();
        for(int i = 0;i<l;i++){
            char ch = S.charAt(i);
            a[ch-'a']++;
        }
        long sum = 0;
        long ans = (l*(l-1))/2;
        for(int i =0;i<26;i++){
            if(a[i]>=2){
                long l1=(a[i]*(a[i]-1))/(long)2;
                sum+=l1;
                y++;
            }
        }
        ans -= sum;
        if(sum>0)
            ans+=1;
        return ans;
    }
}
```
