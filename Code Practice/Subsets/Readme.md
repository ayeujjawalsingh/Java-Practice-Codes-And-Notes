## Subsets
Given a set of positive integers, find all its subsets.[🔗Goto](https://practice.geeksforgeeks.org/problems/subsets-1613027340/1#) 

```
Example 1 :

Input : 
array = {1, 2, 3}
Output :
// this space denotes null element. 
1
1 2
1 2 3
1 3
2
2 3
3
Explanation: 
The following are the subsets 
of the array {1, 2, 3}.

Example 2 :

Input :
array = {1, 2}
Output :

1 
1 2
2
Explanation :
The following are the 
subsets of {1, 2}.
```
<details>
<summary>Full Code</summary>

```java
import java.util.*;
import java.lang.*;
import java.io.*;

class GFG {
    
    
	public static void main (String[] args) {
		Scanner sc = new Scanner(System.in);
		int testCases = sc.nextInt();
		for(int t=0;t<testCases;t++){
		    int n = sc.nextInt();
		    int arr[] = new int[n];
		    ArrayList<Integer> A = new ArrayList<Integer>();
		    for(int i=0;i<n;i++){
		        arr[i] = sc.nextInt();
		        A.add(arr[i]);
		        
		    }
		   
		   
		    
		    ArrayList <ArrayList<Integer>> res = new Solution().subsets(A);
		    for (int i = 0; i < res.size (); i++)
		    {
		        for (int j = 0; j < res.get(i).size (); j++)
		        {
		          System.out.print(res.get(i).get(j)+" ");
		        }
		        System.out.println();
		      
		    }
		    //System.out.println();
		}
	}
}// } Driver Code Ends


class Solution
{
    static int size=0;
    public static ArrayList<ArrayList<Integer>> subsets(ArrayList<Integer> A)
    {
        ArrayList<ArrayList<Integer>> a=new ArrayList<ArrayList<Integer>>();
        
        int l=A.size();
    int length=1;
    for(int i=0;i<l;i++)
    length*=2;
    size=l;
        for(int i=0;i<length;i++)
        {
            int y[]=convert(i);
            ArrayList<Integer> b=new ArrayList<Integer>();
            
            for(int j=0;j<l;j++)
            {
                if(y[j]!=0)
                b.add(A.get(j));
                
            }
            a.add(b);
            
           // System.out.println(Arrays.toString(y));
        }
        Collections.sort(a,new Comparator<ArrayList<Integer>>(){
            @Override
            public int compare(ArrayList<Integer> o1,ArrayList<Integer> o2)
            {
                int p=0;
                while(p<o1.size() && p<o2.size())
                {
                    if(o1.get(p)>o2.get(p))
                    return 1;
                    else if(o1.get(p)==o2.get(p))
                    p++;
                    else
                    return -1;
                    
                }
                if(p>=o1.size())
                return -1;
                return 1;
                
            }
            
        });
        return a;
    }
    public static int[] convert(int num)
    {
        int y[]=new int[size];
        int c=size-1;
        StringBuilder S=new StringBuilder();
        while(num>0)
        {
            int rem=num%2;
            y[c--]=rem;
            num/=2;
        }
        return y;
        
        
    }
}
```
</details>

```
Used a comparator to sort,
Used bit to get all combinations, if you want combination of three digits,

then 000,001,010,011,100,101,110,111 are the possible combinations , where there is ‘0’ ignore, where there is ‘1’ put character in the original array at that position,
like 101--→ 1,3 here

like 011--→ 2,3 here 

thats it.
```

```java
class Solution
{
    static int size=0;
    public static ArrayList<ArrayList<Integer>> subsets(ArrayList<Integer> A)
    {
        ArrayList<ArrayList<Integer>> a=new ArrayList<ArrayList<Integer>>();
        
        int l=A.size();
    int length=1;
    for(int i=0;i<l;i++)
    length*=2;
    size=l;
        for(int i=0;i<length;i++)
        {
            int y[]=convert(i);
            ArrayList<Integer> b=new ArrayList<Integer>();
            
            for(int j=0;j<l;j++)
            {
                if(y[j]!=0)
                b.add(A.get(j));
                
            }
            a.add(b);
            
           // System.out.println(Arrays.toString(y));
        }
        Collections.sort(a,new Comparator<ArrayList<Integer>>(){
            @Override
            public int compare(ArrayList<Integer> o1,ArrayList<Integer> o2)
            {
                int p=0;
                while(p<o1.size() && p<o2.size())
                {
                    if(o1.get(p)>o2.get(p))
                    return 1;
                    else if(o1.get(p)==o2.get(p))
                    p++;
                    else
                    return -1;
                    
                }
                if(p>=o1.size())
                return -1;
                return 1;
                
            }
            
        });
        return a;
    }
    public static int[] convert(int num)
    {
        int y[]=new int[size];
        int c=size-1;
        StringBuilder S=new StringBuilder();
        while(num>0)
        {
            int rem=num%2;
            y[c--]=rem;
            num/=2;
        }
        return y;
        
        
    }
}
```