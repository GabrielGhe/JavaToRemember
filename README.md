JavaToRemember
=================
Things to remember for java

Credits to source article here... <a>http://www.programcreek.com/2012/11/top-10-algorithms-for-coding-interview/</a>

<h3 id="tableOfContent">Table of content</h3>
<ol>
  <li><a href="#1-string">String</a></li>
  <li><a href="#2-linked-list">Linked List</a></li>
  <li><a href="#3-tree">Tree</a></li>
  <li><a href="#4-graph">Graph</a></li>
  <li><a href="#5-sorting">Sorting</a></li>
  <li><a href="#6-recursion-and-iteration">Recursion and iteration</a></li>
  <li><a href="#7-dynamin-programming">Dynamic Programming</a></li>
  <li><a href="#8-bit-manipulation">Bit Manipulation</a></li>
  <li><a href="#9-probability">Probability</a></li>
  <li><a href="#10-combinations-and-permutations">Combinations and Permutations</a></li>
</ol>

<h3 id="string"><a href="#table-of-content">1. String</a></h3>
```java
toCharyArray()                //get char array of a String
Arrays.sort()                 //sort an array
Arrays.toString(char[] a)     //convert to string
charAt(int x)                 //get a char at the specific index
length()                      //string length
length                        //array size
```

<h3><a href="#table-of-content">2. Linked List</a></h3>

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

<h3><a href="#table-of-content">3. Tree</a></h3>
<p>The tree class here is for the binary tree</p>

```java
class TreeNode {
	int value;
	TreeNode parent;
	TreeNode left;
	TreeNode right;
}
```

<ol>
	<li>Binary Search Tree: for all nodes, left children <= current node <= right children</li>
	<li>Balanced vs. Unbalanced: In a balanced tree, the depth of the sibling tree's can differ max by 1</li>
	<li>Full Binary Tree: every node other than the leaves has two children.</li>
	<li>Perfect Binary Tree: a full binary tree + all leaves same depth + parents have 2 children</li>
	<li>Complete Binary Tree: a binary tree with only last lvl possibly incomplete. We add to lowest lvl and right most</li>
</ol>


<h3><a href="#table-of-content">4. Graph</a></h3>
<p>Graphs are use for many things, such as Netorking and games for example.The 2 most famous algorithms for graphs are Depth First Search and Breath First Search</p>

<p>GraphNode</p>
```java
class GraphNode{ 
	int val;
	GraphNode next;
	GraphNode[] neighbors;
	boolean visited;
 
 	/**
 	 *	Constructor with value
 	 */
	GraphNode(int x) {
		val = x;
	}
 	
 	/**
 	 *	Constructor with value
 	 *	and with neightbors
 	 */
	GraphNode(int x, GraphNode[] n){
		val = x;
		neighbors = n;
	}
 
 	/**
 	 *	toString method
 	 */
	public String toString(){
		return "value: "+ this.val; 
	}
}
```

<h3><a href="#table-of-content">5. Sorting</a></h3>
<p>Here is a table of sorting algorithms and their time complexity</p>

<table>
	<tr>
		<td>Algorithm</td>
	</tr>
	<tr>
		<td></td>
	</tr>
	<tr>
		<td></td>
	</tr>
	<tr>
		<td></td>
	</tr>
	<tr>
		<td></td>
	</tr>
	<tr>
		<td></td>
	</tr>
	<tr>
		<td></td>
	</tr>
</table>

