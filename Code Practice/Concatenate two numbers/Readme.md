## Concatenate two numbers
Given an array numbers[] of N positive integers and a positive integer X, The task is to find the number of ways that X can be obtained by writing pair of integers in the array numbers[] next to each other. In other words, find the number of ordered pairs (i,j) such that i != j and X is the concatenation of numbers[i] and numbers[j] [🔗Goto](https://practice.geeksforgeeks.org/problems/1df2447c003940512562d766cf0583bbdc7a75ed/1#) 

```
Example 1:

Input:
N = 4 
numbers[] = {1, 212, 12, 12}
X = 1212
Output:
3
Explanation:
We can obtain X=1212 by concatenating:
numbers[0] = 1 with numbers[1] = 212
numbers[2] = 12 with numbers[3] = 12
numbers[3] = 12 with numbers[2] = 12

Example 2:

Input: 
N = 3
numbers[] = {11, 11, 110}
X = 11011
Output:
2
Explanation:
We can obtain X=11011 by concatenating:
numbers[2] = 110 with numbers[0] = 11
numbers[2] = 110 with numbers[1] = 11
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
            
            String input_line[] = read.readLine().trim().split("\\s+");
            int N = Integer.parseInt(input_line[0]);
            int X = Integer.parseInt(input_line[1]);
            
            input_line = read.readLine().trim().split("\\s+");
            int numbers[]= new int[N];
            for(int i = 0; i < N; i++)
                numbers[i] = Integer.parseInt(input_line[i]);

            Solution ob = new Solution();
            long ans = ob.countPairs(N, X, numbers); 
            System.out.println(ans);
        }
    } 
} // } Driver Code Ends


// here im converting the x into string and i'm making substrings into left and right and then i'm adding it to answer by checking the availability of pairs . if that substring is not present in map it will return 0 ; and as i was doing multiplication the net will become zero and if left == right then it will be n*n-1 because we are not including the i==j case (12) here we cant use 12 two times to produce 1212. 
class Solution 
{ 
    long countPairs(int N, int X, int numbers[]) 
    { 
        long c = 0;
        Map<String,Integer> a = new HashMap<String,Integer>();
        for(int i = 0;i<N;i++){
            String h = numbers[i]+"";
            a.put(h,a.getOrDefault(h,0)+1);
        }
        String l = X + "";
        int len = l.length();
        for(int i = 1;i<len;i++){
            String h1 = l.substring(0,i);
            String h2 = l.substring(i,len);
            if(a.containsKey(h1) && a.containsKey(h2)){
                if(h1.equals(h2)){
                    int y = a.get(h1);
                    c += y*(y-1);
                }
                else{
                    c+=a.get(h1)*a.get(h2);
                }
            }
        }
        return c;
    }
} 
```
</details>

```java
class Solution { 
    long countPairs(int N, int X, int numbers[]){ 
        long c = 0;
        Map<String,Integer> a = new HashMap<String,Integer>();
        for(int i = 0;i<N;i++){
            String h = numbers[i]+"";
            a.put(h,a.getOrDefault(h,0)+1);
        }
        String l = X + "";
        int len = l.length();
        for(int i = 1;i<len;i++){
            String h1 = l.substring(0,i);
            String h2 = l.substring(i,len);
            if(a.containsKey(h1) && a.containsKey(h2)){
                if(h1.equals(h2)){
                    int y = a.get(h1);
                    c += y*(y-1);
                }
                else{
                    c+=a.get(h1)*a.get(h2);
                }
            }
        }
        return c;
    }
} 
```
