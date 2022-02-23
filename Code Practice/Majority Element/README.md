## Majority Element
Given an array A of N elements. Find the majority element in the array. A majority element in an array A of size N is an element that appears more than N/2 times in the array. [🔗Goto](https://practice.geeksforgeeks.org/problems/majority-element-1587115620/1) 

<details>
<summary>Full Code</summary>

```
import java.util.*;
import java.io.*;
import java.lang.*;

class Geeks
{
    public static void main(String args[])
    {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while(t-- > 0)
        {
            int n =sc.nextInt();
            int arr[] = new int[n];
            
            for(int i = 0; i < n; i++)
             arr[i] = sc.nextInt();
             
           System.out.println(new Solution().majorityElement(arr, n)); 
        }
    }
}// } Driver Code Ends


//User function Template for Java

class Solution
{
    static int majorityElement(int a[], int size)
    {
        HashMap <Integer,Integer> map=new HashMap<>();
        for(int i=0;i<size;i++)
        {
            map.put(a[i],map.getOrDefault(a[i],0)+1);
        }
       
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if(entry.getValue()>size/2)
                return entry.getKey();
        }
        return -1;    
    }
}
```
</details>

```
class Solution
{
    static int majorityElement(int a[], int size)
    {
        HashMap <Integer,Integer> map=new HashMap<>();
        for(int i=0;i<size;i++)
        {
            map.put(a[i],map.getOrDefault(a[i],0)+1);
        }
       
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if(entry.getValue()>size/2)
                return entry.getKey();
        }
        return -1;    
    }
}
```