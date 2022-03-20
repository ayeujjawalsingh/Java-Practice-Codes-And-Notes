## Minimum times A has to be repeated such that B is a substring of it
Given two strings A and B. Find minimum number of times A has to be repeated such that B is a Substring of it. If B can never be a substring then return -1.[🔗Goto](https://practice.geeksforgeeks.org/problems/5ef42ba605fff6cd60b1b2dd2ee230ade1fa25b0/1#) 

```
Example 1:

Input:
A = "abcd"
B = "cdabcdab"
Output:
3
Explanation:
Repeating A three times (“abcdabcdabcd”),
B is a substring of it. B is not a substring
of A when it is repeated less than 3 times.

Example 2:
Input:
A = "ab"
B = "cab"
Output :
-1
Explanation:
No matter how many times we repeat A, we can't
get a string such that B is a substring of it.

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
            String A = read.readLine();
            String B = read.readLine();

            Solution ob = new Solution();
            System.out.println(ob.minRepeats(A,B));
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution 
{
    
    private static int func(String A, String B, int i)
    {
        //i is the starting index from which A will begin from.
        
        int n1 = A.length();
        int n2 = B.length();
        
        //Invalid case.
        if(n2<n1) return -1;
        
        int j=0, count = 0;
        
        int fs = -1, le = -1;
        //Here fs stands for first index and le starts for last index.
        
        
        while(j<n2)
        {
            if(fs==-1 && i==0)
            {
                //Store the first index of occurance of A from start.
                fs = j;
            }
            
            if(A.charAt(i)==B.charAt(j))
            {
                
                if(i==n1-1)
                {
                    //Store the last index of full occurence of A.
                    le = j;
                }
                
                i = (i+1)%n1;
                
                j++;
            }
            else
            {
                /*Characters don't match so no need to check
                  further as the sequence is not matching*/
                return -1;
            }
        }
        
        
        int x = le-fs+1;
        
        //Add the number counts where the A string occurs fully.
        count += x/n1;
        
        
        
        if(fs!=0)
        {
            /*If some starting elements are there then we
            need to add another A in the beginning*/
            count++;
        }
        if(le!=n2-1)
        {
            /*If some ending elements are there then we need to increment
             the count by one to cover them too*/
            count++;
        }
        
        
        return count;
    }
    
    static int minRepeats(String A, String B)
    {
        char ch = B.charAt(0);
        int n = A.length();
        
        for(int i=0; i<n; i++)
        {
            if(A.charAt(i)==ch)
            {
                //We do this as there can be multiple starting points in string A.
                int ans = func(A, B, i);
                if(ans!=-1) return ans;
            }
        }
        
        //No match found.
        return -1;
        
    }
};
```
</details>

```java
class Solution 
{
    
    private static int func(String A, String B, int i)
    {
        //i is the starting index from which A will begin from.
        
        int n1 = A.length();
        int n2 = B.length();
        
        //Invalid case.
        if(n2<n1) return -1;
        
        int j=0, count = 0;
        
        int fs = -1, le = -1;
        //Here fs stands for first index and le starts for last index.
        
        
        while(j<n2)
        {
            if(fs==-1 && i==0)
            {
                //Store the first index of occurance of A from start.
                fs = j;
            }
            
            if(A.charAt(i)==B.charAt(j))
            {
                
                if(i==n1-1)
                {
                    //Store the last index of full occurence of A.
                    le = j;
                }
                
                i = (i+1)%n1;
                
                j++;
            }
            else
            {
                /*Characters don't match so no need to check
                  further as the sequence is not matching*/
                return -1;
            }
        }
        
        
        int x = le-fs+1;
        
        //Add the number counts where the A string occurs fully.
        count += x/n1;
        
        
        
        if(fs!=0)
        {
            /*If some starting elements are there then we
            need to add another A in the beginning*/
            count++;
        }
        if(le!=n2-1)
        {
            /*If some ending elements are there then we need to increment
             the count by one to cover them too*/
            count++;
        }
        
        
        return count;
    }
    
    static int minRepeats(String A, String B)
    {
        char ch = B.charAt(0);
        int n = A.length();
        
        for(int i=0; i<n; i++)
        {
            if(A.charAt(i)==ch)
            {
                //We do this as there can be multiple starting points in string A.
                int ans = func(A, B, i);
                if(ans!=-1) return ans;
            }
        }
        
        //No match found.
        return -1;
        
    }
};
```
