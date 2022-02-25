## Insertion Sort for Singly Linked List
Given a singly linked list, sort the list (in ascending order) using insertion sort algorithm. [🔗Goto](https://practice.geeksforgeeks.org/problems/insertion-sort-for-singly-linked-list/1) 

<details>
<summary>Full Code</summary>

```java
import java.util.*;
class Node
    {
        int data;
        Node next;
        Node(int d) {data = d; next = null; }
    }
class insertion
{
    Node head;  
    Node tail;
	public void addToTheLast(Node node) 
	{
	  if (head == null) 
	  {
	   head = node;
	   tail = node;
	  } 
	  else 
	  {
	   tail.next = node;
	   tail = node;
	  }
	}
      void printList(Node head)
    {
        Node temp = head;
        while (temp != null)
        {
           System.out.print(temp.data+" ");
           temp = temp.next;
        }  
        System.out.println();
    }
	/* Drier program to test above functions */
	public static void main(String args[])
    {
         Scanner sc = new Scanner(System.in);
		 int t=sc.nextInt();
		 while(t>0)
         {
			int n = sc.nextInt();
			insertion llist = new insertion(); 
			int a1=sc.nextInt();
			Node head= new Node(a1);
            llist.addToTheLast(head);
            for (int i = 1; i < n; i++) 
			{
				int a = sc.nextInt(); 
				llist.addToTheLast(new Node(a));
			}
			
        Solution ob = new Solution();
		head = ob.insertionSort(llist.head);
		llist.printList(head);
		
        t--;		
        }
    }}// } Driver Code Ends


//User function Template for Java

/*class Node
    {
        int data;
        Node next;
        Node(int d) {data = d; next = null; }
    }
    */
class Solution
{
    public static Node insertionSort(Node head)
    {
        
        if(head.next==null){
            return head;
        }
        Node dm = new Node(0);
        while(head!= null){
            Node temp = dm;
            Node next = head.next;
            while(temp.next != null && temp.next.data < head.data)temp = temp.next;
            head.next = temp.next;
            temp.next = head;
            head = next;
        }
        return dm.next;
    }
}
```
</details>

```java
class Solution
{
    public static Node insertionSort(Node head)
    {
        
        if(head.next==null){
            return head;
        }
        Node dm = new Node(0);
        while(head!= null){
            Node temp = dm;
            Node next = head.next;
            while(temp.next != null && temp.next.data < head.data)temp = temp.next;
            head.next = temp.next;
            temp.next = head;
            head = next;
        }
        return dm.next;
    }
}
```