## Swap Kth nodes from ends
Given a singly linked list of size N, and an integer K. You need to swap the Kth node from the beginning and Kth node from the end of the linked list. Swap the nodes through the links. Do not change the content of the nodes. [🔗Goto](https://practice.geeksforgeeks.org/problems/swap-kth-node-from-beginning-and-kth-node-from-end-in-a-singly-linked-list/1#) 

```
Example 1:

Input:
N = 4,  K = 1
value[] = {1,2,3,4}
Output: 1
Explanation: Here K = 1, hence after
swapping the 1st node from the beginning
and end thenew list will be 4 2 3 1.
 

Example 2:

Input:
N = 5,  K = 7
value[] = {1,2,3,4,5}
Output: 1
Explanation: K > N. Swapping is invalid. 
Return the head node as it is.
```
<details>
<summary>Full Code</summary>

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node
{
    int data;
    Node next;
    
    Node(int data)
    {
        this.data = data;
        next = null;
    }
}

class LinkedList
{
    static  Node head;  
    static  Node lastNode;
    
    public static void addToTheLast(Node node)
    {

        if (head == null)
        {
            head = node;
            lastNode = node;
        }
        else
        {
            Node temp = head;
            lastNode.next = node;
            lastNode = node;
        }
    }
    
    public static void main(String args[])
    {
        Scanner sc=  new Scanner(System.in);
        int t = sc.nextInt();
        
        while(t-- > 0)
        {
            int n, K;
            n = sc.nextInt();
            K = sc.nextInt();
            
            Node head = null;
            int val = sc.nextInt();
            head = new Node(val);
            addToTheLast(head);
            
            for(int i = 1; i< n; i++)
            {
                val = sc.nextInt();
                addToTheLast(new Node(val));
            }
            
            Node before[] = new Node[n];
            addressstore(before, head);
            GFG obj = new GFG();
            
            head = obj.swapkthnode(head, n, K);
        
           Node after[] = new Node[n];
          addressstore(after, head);
        
        if(check(before, after, n, K) == true)
            System.out.println("1");
        else
            System.out.println("0");
        
        }
    }
    
    static boolean check(Node before[], Node after[], int num, int K)
    {
          if(K > num)
           return true;
           
           return (before[K-1] == after[num - K]) && (before[num-K] == after[K-1]);
              
       
    }
    
    static void addressstore(Node arr[], Node head)
  {
      Node temp = head;
      int i = 0;
      while(temp != null){
        arr[i] = temp;
        i++;
        temp = temp.next;
    }
}
    
}// } Driver Code Ends


//User function Template for Java


/* Linked List Node class
   class Node  {
     int data;
     Node next;
     Node(int data)
     {
         this.data = data;
         next = null;
     }
  }
*/
class GFG
{
    //Function to swap Kth node from beginning and end in a linked list.
    Node swapkthnode(Node head, int n, int K)
    {
        if(K>n) return head;
       Node first=head,prev1=null,second=head,prev2=null;
       for(int i=1;i<K;i++)
       {
           prev1=first;
           first=first.next;
       }
       for(int i=1;i<n-K+1;i++)
       {
           prev2=second;
           second=second.next;
       }
       if(prev1!=null) prev1.next=second;
       if(prev2!=null) prev2.next=first;
       Node temp=first.next;
       first.next=second.next;
       second.next=temp;
       if(K==1) head= second;
       if(K==n) head=first;
       return head;
    }
}

```
</details>

```java
class GFG
{
    //Function to swap Kth node from beginning and end in a linked list.
    Node swapkthnode(Node head, int n, int K)
    {
        if(K>n) return head;
       Node first=head,prev1=null,second=head,prev2=null;
       for(int i=1;i<K;i++)
       {
           prev1=first;
           first=first.next;
       }
       for(int i=1;i<n-K+1;i++)
       {
           prev2=second;
           second=second.next;
       }
       if(prev1!=null) prev1.next=second;
       if(prev2!=null) prev2.next=first;
       Node temp=first.next;
       first.next=second.next;
       second.next=temp;
       if(K==1) head= second;
       if(K==n) head=first;
       return head;
    }
}
```
