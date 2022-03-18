## Rank The Permutations
Given a string, find the rank of the string amongst its permutations sorted lexicographically.  [🔗Goto](https://practice.geeksforgeeks.org/problems/rank-the-permutations2229/1#) 

```
Example 1:

Input:
S = "abc"
Output:
1
Explanation:
The order permutations with letters 
'a', 'c', and 'b' : 
abc
acb
bac
bca
cab
cba

Example 2:

Input:
S = "acb"
Output:
2
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
            String str = br.readLine().trim();
            Solution obj = new Solution();
            long ans = obj.findRank(str);
            System.out.println(ans);
        }
    }
}
// } Driver Code Ends


//User function Template for Java

class Solution
{
    public long findRank(String str)
    {
        long ans=0;
        ArrayList<Integer>li=new ArrayList<Integer>();
        for(int i=0;i<str.length();i++)
            li.add((int)str.charAt(i));
        for(int i=0;i<str.length();i++){
            int rank=findIndex(li,(int)str.charAt(i));
            ans+=(rank)*(factorial(str.length()-i-1));
            li.remove(rank);
        }
        return(ans+1);
    }//findRank
    
    public int findIndex(ArrayList<Integer>li,int num){
        Collections.sort(li);
        for(int i=0;i<li.size();i++){
            if(li.get(i)==num)
                return(i);
        }
        return(-1);
    }//findindex
    
    public long factorial(int n){
        if(n==0)
            return(1);
        return(n*factorial(n-1));
    }//factorial
}//Solution
```
</details>

```java
class Solution
{
    public long findRank(String str)
    {
        long ans=0;
        ArrayList<Integer>li=new ArrayList<Integer>();
        for(int i=0;i<str.length();i++)
            li.add((int)str.charAt(i));
        for(int i=0;i<str.length();i++){
            int rank=findIndex(li,(int)str.charAt(i));
            ans+=(rank)*(factorial(str.length()-i-1));
            li.remove(rank);
        }
        return(ans+1);
    }//findRank
    
    public int findIndex(ArrayList<Integer>li,int num){
        Collections.sort(li);
        for(int i=0;i<li.size();i++){
            if(li.get(i)==num)
                return(i);
        }
        return(-1);
    }//findindex
    
    public long factorial(int n){
        if(n==0)
            return(1);
        return(n*factorial(n-1));
    }//factorial
}//Solution
```
