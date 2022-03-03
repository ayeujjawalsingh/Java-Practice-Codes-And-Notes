## The Fibonacci-prime number
Given a number N, the task is to find if N is Fibonacci-prime number or not. A Fibonacci-prime is any number that is both a prime and a Fibonacci number.[🔗Goto](https://practice.geeksforgeeks.org/problems/the-fibonacci-prime-number1150/1/?page=4&difficulty[]=1&status[]=unsolved&category[]=Arrays&category[]=Strings&sortBy=accuracy#) 

```
Example 1:

Input: N = "5"
Output: 1
Explanation: 5 is a Fibonacci number and
prime too

Example 2:

Input: N = "8"
Output: 0
Explanation: 8 is a Fibonacci number but, 
not a prime. 
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
            String input = read.readLine();
            
            Solution ob = new Solution();
            int result = ob.fibonacciPrime(input);
            
            System.out.println(result);
        }
    }
}// } Driver Code Ends
//User function Template for Java
class Solution {
    int fibonacciPrime(String N) {
        // code here
        ArrayList<String> list =new ArrayList<String>();
        list.add("2");
        list.add("3");
        list.add("5");
        list.add("13");
        list.add("89");
        list.add("233");
        list.add("1597");
        list.add("28657");
        list.add("514229");
        list.add("433494437");
        list.add("2971215073");
        list.add("99194853094755497");
        list.add("1066340417491710595814572169");
        list.add("19134702400093278081449423917");
        list.add("475420437734698220747368027166749382927701417016557193662268716376935476241");
    
        for(int i = 0;i<list.size();i++){
            if(N.equals(list.get(i)))
                return 1;
        }
        return 0;
    }
}
```
</details>

```java
class Solution {
    int fibonacciPrime(String N) {
        // code here
        ArrayList<String> list =new ArrayList<String>();
        list.add("2");
        list.add("3");
        list.add("5");
        list.add("13");
        list.add("89");
        list.add("233");
        list.add("1597");
        list.add("28657");
        list.add("514229");
        list.add("433494437");
        list.add("2971215073");
        list.add("99194853094755497");
        list.add("1066340417491710595814572169");
        list.add("19134702400093278081449423917");
        list.add("475420437734698220747368027166749382927701417016557193662268716376935476241");
    
        for(int i = 0;i<list.size();i++){
            if(N.equals(list.get(i)))
                return 1;
        }
        return 0;
    }
}
```
