## Get minimum element from stack 
You are given N elements and your task is to Implement a Stack in which you can get minimum element in O(1) time. [🔗Goto](https://practice.geeksforgeeks.org/problems/get-minimum-element-from-stack/1/?page=1) 

<details>
<summary>Full Code</summary>

```
import java.util.*;



class Get_Min_From_Stack
{
	public static void main(String args[])
	{
		Scanner sc = new Scanner(System.in);
		int T = sc.nextInt();
		while(T>0)
		{
			int q = sc.nextInt();
			GfG g = new GfG();
			while(q>0)
			{
				int qt = sc.nextInt();
				
				if(qt == 1)
				{
					int att = sc.nextInt();
					g.push(att);
					//System.out.println(att);
				}
				else if(qt == 2)
				{
					System.out.print(g.pop()+" ");
				}
				else if(qt == 3)
				{
					System.out.print(g.getMin()+" ");
				}
			
			q--;
			}
			System.out.println();
		T--;
		}
		
	}
}


// } Driver Code Ends


class GfG
{
    int minEle;
    Stack<Integer> s = new Stack<Integer>();

    /*returns min element from stack*/
    int getMin()
    {
        if(s.isEmpty()){
	        return -1;
	    }
	    else{
    	    return minEle;
	    }
    }
    
    /*returns poped element from stack*/
    int pop()
    {
        if(s.isEmpty())
	        return -1;
	    int y=s.peek();
	    s.pop();
	    if(y>=minEle)
	        return y;
	    else{
	        minEle=2*minEle-y;
	        return (y+minEle)/2;
	    }
    }

    /*push element x into the stack*/
    void push(int x)
    {
        if(s.isEmpty()){
    	    s.push(x);
    	    minEle=x;
    	}
	    else{
	        if(x>=minEle) 
	            s.push(x);
	        else{
    	        s.push(2*x-minEle);
    	        minEle=x;
    	    } 
	    }  
    }	
}
```
</details>

```
class GfG
{
    int minEle;
    Stack<Integer> s = new Stack<Integer>();

    /*returns min element from stack*/
    int getMin()
    {
        if(s.isEmpty()){
	        return -1;
	    }
	    else{
    	    return minEle;
	    }
    }
    
    /*returns poped element from stack*/
    int pop()
    {
        if(s.isEmpty())
	        return -1;
	    int y=s.peek();
	    s.pop();
	    if(y>=minEle)
	        return y;
	    else{
	        minEle=2*minEle-y;
	        return (y+minEle)/2;
	    }
    }

    /*push element x into the stack*/
    void push(int x)
    {
        if(s.isEmpty()){
    	    s.push(x);
    	    minEle=x;
    	}
	    else{
	        if(x>=minEle) 
	            s.push(x);
	        else{
    	        s.push(2*x-minEle);
    	        minEle=x;
    	    } 
	    }  
    }	
}
```