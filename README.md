JavaToRemember
=================
Things to remember for java

Taken from here... <a>http://www.programcreek.com/2012/11/top-10-algorithms-for-coding-interview/</a>

<h3 id="tableOfContent">Table of content</h3>
<ul>
  <li><a href="#string">String</a></li>
  <li><a href="#linked-list">Linked List</a></li>
  <li>Tree</li>
  <li>Graph</li>
  <li>Sorting</li>
  <li>Recursion and iteration</li>
  <li>Dynamic Programming</li>
  <li>Bit Manipulation</li>
  <li>Probability</li>
  <li>Combinations and Permutations</li>
</ul>

<h3 id="string"><a href="#table-of-content">String</a></h3>
```java
toCharyArray()                //get char array of a String
Arrays.sort()                 //sort an array
Arrays.toString(char[] a)     //convert to string
charAt(int x)                 //get a char at the specific index
length()                      //string length
length                        //array size
```

<h3><a href="#table-of-content">Linked List</a></h3>

<p>The node class which is the "element" of a linked list</p>
```java
class Node {
  int val;
  Node next;
  
  Node(int x) {
    val = x;      //value
    next = null;  //next element
  }
}
```

<p>Stack implementation using the Linked List data structure</p>
```java
class Stack{
  Node top; 
  
  /**
   *  Default constructor
   */
  public Stack(){}    
  

  /**
   *  Method that returns top node
   *  without removing it
   */
  public Node peek(){
    if(top != null){
      return top;
    }
    return null;
  }
  
  /**
   *  Method used to remove and
   *  return top node
   */
  public Node pop(){
    if(top == null){
      return null;
    } else {
      Node temp = new Node(top.val);
      top = top.next;
      return temp;	
    }
  }
  
  /** 
   *  Method to add Node
   *  to the top of the Stack
   */
  public void push(Node n){
    if(n != null){
      n.next = top;
      top = n;
    }
  }
}
```

<p>Queue implementation using the Linked List data structure</p>

```java
class Queue {
	Node first, last;
  
  /**
   *  Push an element to the back
   *  of the queue
   */
  public void enqueue(Node n){
    if(first == null){
      first = n;
      last = first;
    } else {
      last.next = n;
      last = n;
    }
  }
 
  
  /**
   *  Remove element at the front
   */
  public Node dequeue(){
    if(first == null){
      return null;
    } else {
      Node temp = new Node(first.val);
      first = first.next;
      return temp;
    }	
  }
}
```

