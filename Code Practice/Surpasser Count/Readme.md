## Surpasser Count
An element Y is said to be the surpasser of element X if it is a greater element on the right of X. ie, if X = arr[i] and Y = arr[j], i<j and Arr[i] < Arr[j]. 
Given an array of size N containing distinct integers, find the number of surpassers for each of its elements. [🔗Goto](https://practice.geeksforgeeks.org/problems/8dcd25918295847b4ced54055eae35a8501181c1/1/?page=1&difficulty[]=1&status[]=unsolved&company[]=Microsoft&category[]=Arrays&category[]=Strings&sortBy=accuracy#) 

```
Example 1:

Input:
N = 5
Arr[] = {4, 5, 1, 2, 3}

Output: 1 0 2 1 0

Explanation: There are no elements greater 
than 3 at the right of 3. There is one 
element at right of 2 and greater than 2. 
There are 2 elements greater than 1 at the 
right of 1. And so on.

Example 2:

Input:
N = 6
Arr[] = {2, 7, 5, 3, 8, 1}

Output: 4 1 1 1 0 0
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;

public class GFG {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int tc = Integer.parseInt(br.readLine().trim());
        while (tc-- > 0) {
            String[] inputLine;
            inputLine = br.readLine().trim().split(" ");
            int n = Integer.parseInt(inputLine[0]);
            int[] arr = new int[n];
            inputLine = br.readLine().trim().split(" ");
            for (int i = 0; i < n; i++) {
                arr[i] = Integer.parseInt(inputLine[i]);
            }
            int[] ans = new Solution().findSurpasser(arr, n);
            for (int xx : ans) {
                System.out.print(xx + " ");
            }
            System.out.println();
        }
    }
}

// } Driver Code Ends


//User function Template for Java

//NLogN JAVA SOLN
class Solution{
    int ans[]=new int[0];
    HashMap<Integer,Integer>map=new HashMap<Integer,Integer>();
    int[] findSurpasser(int[] arr, int n){
        ans=new int [arr.length];
        for(int i=0;i<arr.length;i++)
            map.put(arr[i],i);
            
        mergeSort(arr,0,arr.length-1);
        
            
        return(ans);
    }//findSurpasser
    public void  mergeSort(int arr[],int l,int r){
        if(l==r)
            return;
        int m=(l+r)>>1;
        mergeSort(arr,l,m);
        mergeSort(arr,m+1,r);
        merge(arr,l,m,r);
    }//totalCount
    public void merge(int arr[],int l,int m,int r){
        int nrr1[]=new int [m-l+1];
        int nrr2[]= new int [r-m];
        
        for(int i=l;i<=m;i++)
            nrr1[i-l]=arr[i];
        for(int j=m+1;j<=r;j++)
            nrr2[j-m-1]=arr[j];
        
        int i=0;
        int j=0;
        int index=l;
        while(i<nrr1.length && j<nrr2.length){
            if(nrr1[i]<nrr2[j]){
                ans[map.get(nrr1[i])]+=nrr2.length-j;
                arr[index]=nrr1[i];
                i++;
            }
            else{
                arr[index]=nrr2[j];
                j++;
            }
            index++;
        }
        while(i<nrr1.length){
            arr[index]=nrr1[i];
            index++;
            i++;
        }
        while(j<nrr2.length){
            arr[index]=nrr2[j];
            index++;
            j++;
        }
    }//merge
}//Solution
```
</details>

```java
//NLogN JAVA SOLN
class Solution{
    int ans[]=new int[0];
    HashMap<Integer,Integer>map=new HashMap<Integer,Integer>();
    int[] findSurpasser(int[] arr, int n){
        ans=new int [arr.length];
        for(int i=0;i<arr.length;i++)
            map.put(arr[i],i);
            
        mergeSort(arr,0,arr.length-1);
        
            
        return(ans);
    }//findSurpasser
    public void  mergeSort(int arr[],int l,int r){
        if(l==r)
            return;
        int m=(l+r)>>1;
        mergeSort(arr,l,m);
        mergeSort(arr,m+1,r);
        merge(arr,l,m,r);
    }//totalCount
    public void merge(int arr[],int l,int m,int r){
        int nrr1[]=new int [m-l+1];
        int nrr2[]= new int [r-m];
        
        for(int i=l;i<=m;i++)
            nrr1[i-l]=arr[i];
        for(int j=m+1;j<=r;j++)
            nrr2[j-m-1]=arr[j];
        
        int i=0;
        int j=0;
        int index=l;
        while(i<nrr1.length && j<nrr2.length){
            if(nrr1[i]<nrr2[j]){
                ans[map.get(nrr1[i])]+=nrr2.length-j;
                arr[index]=nrr1[i];
                i++;
            }
            else{
                arr[index]=nrr2[j];
                j++;
            }
            index++;
        }
        while(i<nrr1.length){
            arr[index]=nrr1[i];
            index++;
            i++;
        }
        while(j<nrr2.length){
            arr[index]=nrr2[j];
            index++;
            j++;
        }
    }//merge
}//Solution

```
