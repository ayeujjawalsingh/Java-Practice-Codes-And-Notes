## Smaller on Left
Given an array arr[ ] of N positive integers, the task is to find the greatest element on the left of every element in the array which is strictly smaller than itself, if this element does not exist for an index print "-1".[🔗Goto](https://practice.geeksforgeeks.org/problems/smaller-on-left20360700/1#) 

```
Example 1:

Input:
N = 5
arr[] = {2, 3, 4, 5, 1}
Output: 
-1 2 3 4 -1
Explanation:
Greatest element on the left of 3 smaller 
than itself is 2, for 4 it is 3 and for 5 
it is 1. Since 2 is the first element and 
no element on its left is present, so it's 
greatest smaller element will be -1 and for 
1 no element smaller than itself is present 
on its left, so it's greatest smaller element 
is -1.

Example 2:

Input:
N = 3
arr[] = {1, 2, 3} 
Output:
-1 1 2 
```
<details>
<summary>Full Code</summary>

```java
import java.io.*;
import java.util.*;
class Array {
    
    // Driver code
	public static void main (String[] args) throws IOException{
		// Taking input using buffered reader
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
		int testcases = Integer.parseInt(br.readLine());
		
		// looping through all testcases
		while(testcases-- > 0){
		    int sizeOfArray = Integer.parseInt(br.readLine());
		    int arr [] = new int[sizeOfArray];
		    
		    String line = br.readLine();
		    String[] elements = line.trim().split("\\s+");
		    for(int i = 0;i<sizeOfArray;i++){
		        arr[i] = Integer.parseInt(elements[i]);
		    }
		    
		    Complete obj = new Complete();
		    arr = obj.Smallestonleft(arr, sizeOfArray);
		    for(int i=0; i< sizeOfArray;i++){
		        System.out.print(arr[i] + " ");
		    }
		    System.out.println();
		}
	}
}


// } Driver Code Ends


//User function Template for Java



class Complete{
    public static int[] Smallestonleft (int arr[], int n) {
        int res[] = new int[n];
         res[0]= -1;
         TreeSet<Integer> set = new TreeSet<Integer>();
         set.add(arr[0]);
         for(int i=0;i<n;i++){
             
             if(set.floor(arr[i]-1) != null){
                 res[i] = set.floor(arr[i] - 1);
             }
             else{
                 res[i] = -1;
             }
             
             set.add(arr[i]);
         }
        return res;
    }
}
```
</details>

```java
class Complete{
    public static int[] Smallestonleft (int arr[], int n) {
        int res[] = new int[n];
         res[0]= -1;
         TreeSet<Integer> set = new TreeSet<Integer>();
         set.add(arr[0]);
         for(int i=0;i<n;i++){
             
             if(set.floor(arr[i]-1) != null){
                 res[i] = set.floor(arr[i] - 1);
             }
             else{
                 res[i] = -1;
             }
             
             set.add(arr[i]);
         }
        return res;
    }
}
```
