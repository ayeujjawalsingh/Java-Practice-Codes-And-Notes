## Kadane's Algorithm 
Given an array Arr[] of N integers. Find the contiguous sub-array(containing at least one number) which has the maximum sum and return its sum. [🔗Goto](https://practice.geeksforgeeks.org/problems/kadanes-algorithm-1587115620/1) 

<details>
<summary>Full Code</summary>

```java
import java.io.*;

class Main {
    
	public static void main (String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		int t = Integer.parseInt(br.readLine().trim()); //Inputting the testcases
		while(t-->0){
		    //size of array
		    int n = Integer.parseInt(br.readLine().trim());
		    int arr[] = new int[n];
		    String inputLine[] = br.readLine().trim().split(" ");
		    
		    //adding elements
		    for(int i=0; i<n; i++){
		        arr[i] = Integer.parseInt(inputLine[i]);
		    }
		    
		    Solution obj = new Solution();
		    
		    //calling maxSubarraySum() function
		    System.out.println(obj.maxSubarraySum(arr, n));
		}
	}
}

// } Driver Code Ends


class Solution{
    // arr: input array
    // n: size of array
    //Function to find the sum of contiguous subarray with maximum sum.
    long maxSubarraySum(int arr[], int n){
       int c = 0;
        long a =Long.MIN_VALUE;
        long sum =0;
        for(int i =0;i<=n-1;i++){
            sum+=arr[i];
            if(sum>a){
                a=sum;
            }
            if(sum<0){
                sum=0;
            }
        }
       return a;
    }
}
```
</details>

```java
class Solution{
    // arr: input array
    // n: size of array
    //Function to find the sum of contiguous subarray with maximum sum.
    long maxSubarraySum(int arr[], int n){
       int c = 0;
        long a =Long.MIN_VALUE;
        long sum =0;
        for(int i =0;i<=n-1;i++){
            sum+=arr[i];
            if(sum>a){
                a=sum;
            }
            if(sum<0){
                sum=0;
            }
        }
       return a;
    }
}
```