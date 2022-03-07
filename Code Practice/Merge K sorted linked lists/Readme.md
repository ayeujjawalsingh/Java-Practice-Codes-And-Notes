## Merge K sorted linked lists
Given K sorted linked lists of different sizes. The task is to merge them in such a way that after merging they will be a single sorted linked list.[🔗Goto](https://practice.geeksforgeeks.org/problems/merge-k-sorted-linked-lists/1#) 

```
Example 1:

Input:
K = 4
value = {{1,2,3},{4 5},{5 6},{7,8}}
Output: 1 2 3 4 5 5 6 7 8
Explanation:
The test case has 4 sorted linked 
list of size 3, 2, 2, 2
1st    list     1 -> 2-> 3
2nd   list      4->5
3rd    list      5->6
4th    list      7->8
The merged list will be
1->2->3->4->5->5->6->7->8.

Example 2:

Input:
K = 3
value = {{1,3},{4,5,6},{8}}
Output: 1 3 4 5 6 8
Explanation:
The test case has 3 sorted linked
list of size 2, 3, 1.
1st list 1 -> 3
2nd list 4 -> 5 -> 6
3rd list 8
The merged list will be
1->3->4->5->6->8.
```
<details>
<summary>Full Code</summary>

```java
import java.util.*;

class Node
{
    int data;
    Node next;
    
    Node(int key)
    {
        data = key;
        next = null;
    }
}


class GfG
{
    public static void printList(Node node)
    {
        while(node != null)
        {
            System.out.print(node.data + " ");
            node = node.next;
        }
    }
    
    public static void main (String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int t = sc.nextInt();
        while(t-- > 0)
        {   
            int N = sc.nextInt();
            
            Node []a = new Node[N];
            
            for(int i = 0; i < N; i++)
            {
                int n = sc.nextInt();
                
                Node head = new Node(sc.nextInt());
                Node tail = head;
                
                for(int j=0; j<n-1; j++)
                {
                    tail.next = new Node(sc.nextInt());
                    tail = tail.next;
                }
                
                a[i] = head;
            }
            
            Solution g = new Solution();
             
            Node res = g.mergeKList(a,N);
            if(res!=null)
                printList(res);
            System.out.println();
        }
    }
}// } Driver Code Ends


/*class Node
{
    int data;
    Node next;
    
    Node(int key)
    {
        data = key;
        next = null;
    }
}
*/

// a is an array of Nodes of the heads of linked lists
// and N is size of array a


class Solution
{
    //Function to merge K sorted linked list.
    Node mergeKList(Node[]arr,int k)
    {
        return divideAndMerge(0, k-1, arr);
    }
    Node divideAndMerge(int s, int e, Node arr[]){
      if(s<=e){
        if(s==e)return arr[s];
        
        int mid = (s+e)/2;
        Node left = divideAndMerge(s, mid, arr);
        Node right = divideAndMerge(mid+1, e, arr);
        return mergeLists(left, right);
        
      }
      return null;
    }
    Node mergeLists(Node list1, Node list2){
      Node temp1 = list1, temp2 = list2;
      Node head = new Node(-1);
      Node curr = head;
      while(temp1 != null && temp2 != null){
         if(temp1.data < temp2.data){
           curr.next = temp1;
           curr = curr.next;
           temp1 = temp1.next;
         }
         else{
           curr.next = temp2;
           curr = curr.next;
           temp2 = temp2.next; 
         }
      }
        
      while(temp1 != null){
         curr.next = temp1;
         curr = curr.next;
         temp1 = temp1.next;  
      }
        
      while(temp2 != null){
         curr.next = temp2;
         curr = curr.next;
         temp2 = temp2.next;  
      } 
     
      curr.next = null;   
      return head.next;    
    }
}
```
</details>

```java
class Solution
{
    //Function to merge K sorted linked list.
    Node mergeKList(Node[]arr,int k)
    {
        return divideAndMerge(0, k-1, arr);
    }
    Node divideAndMerge(int s, int e, Node arr[]){
      if(s<=e){
        if(s==e)return arr[s];
        
        int mid = (s+e)/2;
        Node left = divideAndMerge(s, mid, arr);
        Node right = divideAndMerge(mid+1, e, arr);
        return mergeLists(left, right);
        
      }
      return null;
    }
    Node mergeLists(Node list1, Node list2){
      Node temp1 = list1, temp2 = list2;
      Node head = new Node(-1);
      Node curr = head;
      while(temp1 != null && temp2 != null){
         if(temp1.data < temp2.data){
           curr.next = temp1;
           curr = curr.next;
           temp1 = temp1.next;
         }
         else{
           curr.next = temp2;
           curr = curr.next;
           temp2 = temp2.next; 
         }
      }
        
      while(temp1 != null){
         curr.next = temp1;
         curr = curr.next;
         temp1 = temp1.next;  
      }
        
      while(temp2 != null){
         curr.next = temp2;
         curr = curr.next;
         temp2 = temp2.next;  
      } 
     
      curr.next = null;   
      return head.next;    
    }
}

```
