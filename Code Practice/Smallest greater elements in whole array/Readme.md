## Smallest greater elements in whole array
Given an array A of N length. We need to calculate the next greater element for each element in a given array. If the next greater element is not available in a given array then we need to fill -10000000 at that index place. [🔗Goto](https://practice.geeksforgeeks.org/problems/smallest-greater-elements-in-whole-array2751/1) 

```
Example 1:

Input : arr[] = {13, 6, 7, 12}
Output : _ 7 12 13 
Explanation:
Here, at index 0, 13 is the greatest value 
in given array and no other array element 
is greater from 13. So at index 0 we fill 
'-10000000'.

Example 2:

Input : arr[] = {6, 3, 9, 8, 10, 2, 1, 15, 7} 
Output :  7 6 10 9 15 3 2 _ 8
Explanation: Here, at index 7, 15 is the greatest
value in given array and no other array element is
greater from 15. So at index 7 we fill '-10000000'.
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
		    arr = obj.greaterElement(arr, sizeOfArray);
		    for(int i=0; i< sizeOfArray;i++){
		        if(arr[i] == -10000000)
		            System.out.print("_ ");
		        else
		            System.out.print(arr[i] + " ");
		    }
		    System.out.println();
		}
	}
}


// } Driver Code Ends


//User function Template for Java

//User function Template for Java

//User function Template for Java

            

class Complete{
    
   
    // Function for finding maximum and value pair
    public static int[] greaterElement (int arr[], int n) {
        Integer[] nums = Arrays.stream( arr ).boxed().toArray( Integer[]::new );
        TreeSet<Integer> set = new TreeSet<>(Arrays.asList(nums));
        int[] res = new int[n];
        for(int i=0; i< n;i++){
            if(set.higher(arr[i]) != null){
                res[i] = set.higher(arr[i]);
            }
            else{
                res[i] = -10000000;
            }
        }
        return res;
    }
    
    
}
```
</details>

```java
class Complete{
    
   
    // Function for finding maximum and value pair
    public static int[] greaterElement (int arr[], int n) {
        Integer[] nums = Arrays.stream( arr ).boxed().toArray( Integer[]::new );
        TreeSet<Integer> set = new TreeSet<>(Arrays.asList(nums));
        int[] res = new int[n];
        for(int i=0; i< n;i++){
            if(set.higher(arr[i]) != null){
                res[i] = set.higher(arr[i]);
            }
            else{
                res[i] = -10000000;
            }
        }
        return res;
    }
    
    
}

```
