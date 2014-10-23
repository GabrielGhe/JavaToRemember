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
  <li><a href="#7-dynamic-programming">Dynamic Programming</a></li>
  <li><a href="#8-bit-manipulation">Bit Manipulation</a></li>
  <li><a href="#9-probability">Probability</a></li>
  <li><a href="#10-combinations-and-permutations">Combinations and Permutations</a></li>
  <li><a href="#11-files">Files</a></li>
  <li><a href="#12-sockets">Sockets</a></li>
  <li><a href="#13-regex">Regex</a></li>
  <li><a href="#14-formating">Formating</a></li>
  <li><a href="#15-hashmap">HashMap</a></li>
</ol>

<!-- 
#########################################
#					#
#		String			#
#					#
#########################################
-->
<h3 id="string"><a href="#table-of-content">1. String</a></h3>
```java
toCharArray()                //get char array of a String
Collections.sort()            //sorts a LIST
Arrays.sort()                 //sort an array
Collections.reverse()	      //reverses a LIST
Arrays.toString(char[] a)     //convert to string
charAt(int x)                 //get a char at the specific index
length()                      //string length
length                        //array size
```

<!-- 
#########################################
#					#
#	Linked list			#
#					#
#########################################
-->
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

<!-- 
#########################################
#										#
#				Tree					#
#										#
#########################################
-->
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


<!-- 
#########################################
#										#
#				Graph					#
#										#
#########################################
-->
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

<p>
	Breath First Search (live implementation from MIT <a href="http://www.youtube.com/watch?v=s-CYnVz-uh4&t=2055">here</a>)
</p>

```java
public static Node bfs(Node root, int value) {
	// Queue is abstract, use an implementation of queue
	Queue<Node> q = new Queue<Node>();
	Node returnValue;
	q.enqueue(root);
	
	while (!q.isEmpty()) {
		Node temp = q.dequeue();
		if (temp.value == value) {
			returnValue = temp;
			break;
		}
		for (Node adj : temp.adjecent) {
			q.enqueue(adj);
		}
	}
	return returnValue;
}
```

<p>
	Depth First Search
</p>
```java
public static Node dfs(Node root, int value) {
	Stack<Node> s = new Stack<Node>();
	Node returnValue;
	s.push(root);
	
	while (!q.isEmpty()) {
		Node temp = s.pop();
		if (temp.value == value) {
			returnValue = temp;
			break;
		}
		for (Node adj : temp.adjecent) {
			s.push(adj);
		}
	}
	return returnValue;
}
```


<!-- 
#########################################
#										#
#				SORTING					#
#										#
#########################################
-->
<h3><a href="#table-of-content">5. Sorting</a></h3>
<p>Here is a table of comparison sorting algorithms and their time complexity</p>

<table>
	<tr>
		<td>Algorithm</td>
		<td>Average Time</td>
		<td>Worst Time</td>
		<td>Space</td>
		<td>Comments</td>
	</tr>
	<tr>
		<td>Bubble sort</td>
		<td>n^2</td>
		<td>n^2</td>
		<td>1</td>
		<td>It's easy to implement</td>
	</tr>
	<tr>
		<td>Insertion sort</td>
		<td>n^2</td>
		<td>n^2</td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Selection sort</td>
		<td>n^2</td>
		<td>n^2</td>
		<td>1</td>
		<td></td>
	</tr>
	<tr>
		<td>Heap sort</td>
		<td>n log(n)</td>
		<td>n log(n)</td>
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td>Merge sort</td>
		<td>n log(n)</td>
		<td>n log(n)</td>
		<td>a lot</td>
		<td></td>
	</tr>
	<tr>
		<td>Quick sort</td>
		<td>n log(n)</td>
		<td>n^2</td>
		<td></td>
		<td>In practice, is fastest</td>
	</tr>
</table>

<p>Here is a table of algorithms that do not use comparison</p>
<table>
	<tr>
		<td>Algorithm</td>
		<td>Average Time</td>
		<td>Worst Time</td>
		<td>Space</td>
		<td>Comments</td>
	</tr>
	<tr>
		<td>Bucket sort</td>
		<td>n</td>
		<td>n + N</td>
		<td></td>
		<td>n is the range of keys, N is size of array</td>
	</tr>
	<tr>
		<td>Radix sort</td>
		<td>n</td>
		<td>m(n + N)</td>
		<td></td>
		<td>m is the number of keys</td>
	</tr>
</table>


<!-- 
#########################################
#										#
#		Recursion and Iteration			#
#										#
#########################################
-->
<h3><a href="#table-of-content">6. Recursion and Iteration</a></h3>
<p>Recursion is easy to understand and implement. However, it's worse than iteration and can cause stackoverflows</p>

<p>Fibonacci using bad recursion</p>
```java
public static int fib(int n){
	if(n <= 1)
		return n;					//base case
	else
		return fib(n-1) + fib(n-2);	//recursive case
}
```

<p>Fibonacci using tail recursion</p>
```java
public static int fibHelper(int start, int end, int prev, int current){
	if(start == end)
		return current;
	else
		return fibHelper(++start, end, current, current + prev);
}

public static int fib(int n){
	if(n <= 1)
		return n;
	else 
		return fibHelper(1,n,0,1);
}
```

<p>Fibonacci using iteration</p>
```java
public static int fib(int n) {
	if (n <= 1){
		return n;
	}
	int current = 1;
	int prev = 0;
	int temp = 0;
 
	for (int i = 2; i <= n; i++) {
		temp = current + prev;	//compute fib at pos n
		prev = current;			//old current is now prev
		current = temp;			//current is temp
	}
	return current;
}
```

<!-- 
#########################################
#										#
#		DYNAMIC PROGRAMMING				#
#										#
#########################################
-->
<h3><a href="#table-of-content">7. Dynamic programming</a></h3>
<p>Dynamic programming is a technique for solving problems with the following properties:</p>

<ol>
	<li>An instance is solved using the solutions for smaller instances.</li>
	<li>The solution for a smaller instance might be needed multiple times.</li>
	<li>The solutions to smaller instances are stored in a table, so that each smaller instance is solved only once.</li>
	<li>Additional space is used to save time.</li>
</ol>
<p>The problem of climbing steps perfectly fit those 4 properties. Therefore, it can be solve by using dynamic programming.</p>

```java
public static int[] Steps = new int[100];
 
public static int f3(int n) {
	if (n <= 2)
		A[n]= n;
 
	if(A[n] > 0)
		return A[n];
	else
		A[n] = f3(n-1) + f3(n-2);	//store results so only calculate once!
	return A[n];
}
```


<!-- 
#########################################
#										#
#			Bit Manipulation			#
#										#
#########################################
-->
<h3><a href="#table-of-content">8. Bit Manipulation</a></h3>
<p>Bit operators</p>

<table>
	<!-- Header -->
	<tr>
		<td>Operation name</td>
		<td>Java symbol</td>
		<td>Example</td>
		<td>Result</td>
		<td>Explanation</td>
	</tr>
	<!-- Row 1 -->
	<tr>
		<td>AND</td>
		<td>&</td>
		<td>7 & 5</td>
		<td>5</td>
		<td>111 & 101 = 101</td>
	</tr>
	<!-- Row 2 -->
	<tr>
		<td>OR</td>
		<td>|</td>
		<td>8 | 3</td>
		<td>11</td>
		<td>1000 | 0011 = 1011</td>
	</tr>
	<!-- Row 3 -->
	<tr>
		<td>XOR</td>
		<td>^</td>
		<td>15 ^ 5</td>
		<td>10</td>
		<td>1111 ^ 0101 = 1010</td>
	</tr>
	<!-- Row 5 -->
	<tr>
		<td>Right Shift</td>
		<td>>></td>
		<td>7 >> 1</td>
		<td>3</td>
		<td>111 >> 1 = 011</td>
	</tr>
	<!-- Row 6 -->
	<tr>
		<td>Not</td>
		<td>~</td>
		<td>~0</td>
		<td>-1</td>
		<td>~000 = 111 which is 2's complement -1</td>
	</tr>
</table>


<!-- 
#########################################
#										#
#			Probability					#
#										#
#########################################
-->
<h3><a href="#table-of-content">9. Probability</a></h3>
<p>There are 50 people in a room, what’s the probability that two people have the same birthday? (Ignoring the fact of leap year, i.e., 365 day every year)</p>

```java
public static double caculateProbability(int n){
	double x = 1; 
 
	for(int i=0; i<n; i++){
		x *=  (365.0-i)/365.0;
	}
 
	double pro = Math.round((1-x) * 100);
	return pro/100;
}
```

<!-- 
#########################################
#										#
#			Probability					#
#										#
#########################################
-->
<h3><a href="#table-of-content">10. Combinations and Permutations</a></h3>
<ul>
	<li>If the order doesn't matter, it is a Combination... 1234 same as 4321</li>
	<li>If the order matters, it is a Permutation... 1234 != 2134</li>
</ul>


<h3><a href="#table-of-content">11. Files</a></h3>

<p>Writing to a file.</p>
```java
//java7... appends to file
try(Formatter f = new Formatter("myText.txt")) {
	f.format("this is output text", null);
} catch(IOException ioe){
	ioe.printStackTrace();
}

//older java
Formatter f;
try {
	f = new Formatter("myText.txt");
	f.format("this is output text", null);
} catch(IOException ioe){
	ioe.printStackTrace();
} finally {
	f.close();
}
```

<p>Reading from a file</p>
```java
//read all the lines in a file
try(Scanner scan = new Scanner(new File("myText.txt") ) ){
	ArrayList<String> x = new ArrayList<String>();
	while(scan.hasNext()){
		x.add(scan.nextLine());
	}
} catch (FileNotFoundException e) {
	e.printStackTrace();
}
```

<h3><a href="#table-of-content">12. Sockets</a></h3>

<p>Server that listens for a connection, writes the date and closes connection</p>
```java
//Server
ServerSocket listener = new ServerSocket(9090);
try {
    while (true) {
        Socket socket = listener.accept();
        try {
            ObjectOutputStream out =
                new ObjectOutputStream(socket.getOutputStream());
            out.writeObject("Hi there");
        } finally {
            socket.close();
        }
    }
}
finally {
    listener.close();
}


//Client the data is sent through serialization
//to send objects, they must be serializable
Socket s = new Socket(serverAddress, 9090);
try{
	ObjectInputStream input = new ObjectInputStream(s.getInputStream());
	String answer = (String)input.readObject();
} catch(ClassCastException cce){
	cce.printStackTrace();
} finally {
	s.close();
}

//On mac, you can open a terminal and write "nc localhost 9090" to connect to server socket
```

<h3><a href="#table-of-content">13. Regex</a></h3>
<p>
The full documentation can be found here 
<a href="http://docs.oracle.com/javase/7/docs/api/java/util/regex/Pattern.html">
Docs
</a>
</p>

```java

//Long way, that can be reused
Pattern p = Pattern.compile("a*b");
Matcher m = p.matcher("aaaab");
boolean b = m.matches();

//shorthand
boolean b = Pattern.matches("a*b", "aaaaab");
```

<p><b>Regular-expression constructs</b></p>
<table>
	<tr>
		<td>[abc]</td>
		<td>a, b, or c (simple class)</td>
	</tr>
	
	<!-- 2 -->
	<tr>
		<td>
			[^abc]
		</td>
		<td>
			Any character except a, b, or c (negation)
		</td>
	</tr>
	
	<!-- 3 -->
	<tr>
		<td>
			[a-zA-Z]
		</td>
		<td>
			a through z or A through Z, inclusive (range)
		</td>
	</tr>
	
	<!-- 4 -->
	<tr>
		<td>
			[a-d[m-p]]
		</td>
		<td>
			a through d, or m through p: [a-dm-p] (union)
		</td>
	</tr>
	
	<!-- 5 -->
	<tr>
		<td>
			[a-z&&[def]]
		</td>
		<td>
			d, e, or f (intersection)
		</td>
	</tr>
	
	<!-- 6 -->
	<tr>
		<td>
			[a-z&&[^bc]]
		</td>
		<td>
			a through z, except for b and c: [ad-z] (subtraction)
		</td>
	</tr>
	
	<!-- 7 -->
	<tr>
		<td>
			[a-z&&[^m-p]]
		</td>
		<td>
			a through z, and not m through p: [a-lq-z](subtraction)
		</td>
	</tr>
</table>

<p><b>Predefined character classes</b></p>
<table>
	<!-- 1 -->
	<tr>
		<td>
			.
		</td>
		<td>
			Any character (may or may not match line terminators)
		</td>
	</tr>
	
	<!-- 2 -->
	<tr>
		<td>
			\d
		</td>
		<td>
			A digit: [0-9]
		</td>
	</tr>
	
	<!-- 3 -->
	<tr>
		<td>
			\D
		</td>
		<td>
			A non-digit: [^0-9]
		</td>
	</tr>
	
	<!-- 4 -->
	<tr>
		<td>
			\s
		</td>
		<td>
			A whitespace character: [ \t\n\x0B\f\r]
		</td>
	</tr>
	
	<!-- 5 -->
	<tr>
		<td>
			\S
		</td>
		<td>
			A non-whitespace character: [^\s]
		</td>
	</tr>
	
	<!-- 6 -->
	<tr>
		<td>
			\w
		</td>
		<td>
			A word character: [a-zA-Z_0-9]
		</td>
	</tr>
	
	<!-- 7 -->
	<tr>
		<td>
			\W
		</td>
		<td>
			A non-word character: [^\w]
		</td>
	</tr>
</table>


<p><b>Greedy quantifiers</b></p>

<table>
	<!-- 1 -->
	<tr>
		<td>
			X?
		</td>
		<td>
			X, once or not at all
		</td>
	</tr>
	
	<!-- 2 -->
	<tr>
		<td>
			X*
		</td>
		<td>
			X, zero or more times
		</td>
	</tr>
	
	<!-- 3 -->
	<tr>
		<td>
			X+
		</td>
		<td>
			X, one or more times
		</td>
	</tr>
	
	<!-- 4 -->
	<tr>
		<td>
			X{n}
		</td>
		<td>
			X, exactly n times
		</td>
	</tr>
	
	<!-- 5 -->
	<tr>
		<td>
			X{n,}
		</td>
		<td>
			X, at least n times
		</td>
	</tr>
	
	<!-- 6 -->
	<tr>
		<td>
			X{n,m}
		</td>
		<td>
			X, at least n but not more than m times
		</td>
	</tr>
</table>

<h3><a href="#table-of-content">14. Formating</a></h3>

<p>
	Full article can be found <a href="http://examples.javacodegeeks.com/core-java/lang/string/java-string-format-example/"> here</a>
</p>

<p>
	<b>Strings</b>
</p>

<table>
	<tr>
		<td>Code</td>
		<td>Description</td>
	</tr>
	<tr>
		<td>%s</td>
		<td>will print the string as it is.</td>
	</tr>
	<tr>
		<td>%15s</td>
		<td>will print the string as it is. If the string has less than 15 characters, the output will be padded on the left.</td>
	</tr>
	<tr>
		<td>%-6s</td>
		<td>will print the string as it is. If the string has less than 6 characters, the output will be padded on the left.</td>
	</tr>
	<tr>
		<td>%.8s</td>
		<td>will print maximum 8 characters of the string.</td>
	</tr>
</table>


```java
// Padding left
System.out.printf("%10s %10s\n", "hello", "world");

// Padding right
System.out.printf("%-10s %-10s\n", "hello", "world");

// As is
System.out.printf("%s %s\n", "hello", "world");

// Max 2 characters
System.out.printf("%.2s %.2s\n", "hello", "world");

/*
     hello      world
hello      world     
hello world
he wo    
*/
```

<p>
	<b>Integers</b>
</p>


<table>
	<tr>
		<td>Code</td>
		<td>Description</td>
	</tr>
	<tr>
		<td>%d</td>
		<td>will print the integer as it is.</td>
	</tr>
	<tr>
		<td>%6d</td>
		<td>will print the integer as it is. If the number of digits is less than 6, the output will be padded on the left.</td>
	</tr>
	<tr>
		<td>%-6d</td>
		<td>will print the integer as it is. If the number of digits is less than 6, the output will be padded on the right.</td>
	</tr>
	<tr>
		<td>%06d</td>
		<td>will print the integer as it is. If the number of digits is less than 6, the output will be padded on the left with zeroes.</td>
	</tr>
</table>

```java
// Padding left
System.out.printf("%10d %10d\n", 12345, 54321);

// Padding right
System.out.printf("%-10d %-10d\n", 12345, 54321);

// As is
System.out.printf("%d %d\n", 12345, 54321);

// fill rest of 10 digits with 0s
System.out.printf("%010d %010d\n", 12345, 54321);

/*
     12345      54321
12345      54321     
12345 54321
0000012345 0000054321
*/
```

<p>
	<b>Floats</b>
</p>


<table>
	<tr>
		<td>Code</td>
		<td>Description</td>
	</tr>
	<tr>
		<td>%f</td>
		<td>will print the number as it is.</td>
	</tr>
	<tr>
		<td>%15f</td>
		<td>will print the number as it is. If the number has less than 15 digits, the output will be padded on the left.</td>
	</tr>
	<tr>
		<td>%.8f</td>
		<td>will print maximum 8 decimal digits of the number.</td>
	</tr>
	<tr>
		<td>%9.4f</td>
		<td>will print maximum 4 decimal digits of the number. The output will occupy 9 characters at least. If the number of digits is not enough, it will be padded</td>
	</tr>
</table>

```java
// Padding left
System.out.printf("%14f %14f\n", 123.456789, 987.654321);

// Padding right
System.out.printf("%-14f %-14f\n", 123.456789, 987.654321);

// As is
System.out.printf("%f %f\n", 123.456789, 987.654321);

// 3 digit Precision + left padding 
System.out.printf("%14.3f %14.3f\n", 123.456789, 987.654321);

/*
    123.456789     987.654321
123.456789     987.654321    
123.456789 987.654321
       123.457        987.654
*/
```

<h3><a href="#table-of-content">15. HashMap</a></h3>

<p>
HashMaps & HashTables allow inserts, deletes and gets at O(1).
HashTables are synchronized while HashMaps are not. HashTables do not allow null keys or values.
HashMaps allows 1 null key and unlimited null values.
Source: <a href="http://stackoverflow.com/questions/40471/differences-between-hashmap-and-hashtable">here</a>
</p>

```java
HashMap<String, Integer> map = new HashMap<String, Integer>();
map.put("a", 1); // { a:1 }
map.put("b", 2); // { a:1, b:2 }
map.put("c", 3); // { a:1, b:2, c:3 }

map.get("a");    // 1
map.containsKey("d"); // false
map.values();    // [1, 2, 3]
map.keySet();    // ["a", "b", "c"]
map.remove("a"); // { b:2, c:3 }
map.clear();     // {}
```
