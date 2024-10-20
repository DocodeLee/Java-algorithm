# Java-algorithm


## stack
stack : last in first out
Stack<String> stack = new Stack<String>();
push();
pop();
stack.peek(); // can check the first data to come out

String myFavgame = stack.pop(); // you can set data in new attributes

## queue
queue: first in first out data structure / linear datastructure
enqueue : offer()
dequeue : poll()

System.out.println(queue.isEmpty());
queue.size(); // can check queue size
queue.contains("variable"); //boolean

queue is used for keyboard buffer. printer queue, used in linkedlists, 
priorityqueues, breadth-first search

## priority queue
priority queue : FIFO data structure, highest priorites first before lower priority

Queue<Double> queue = new PriorityQueue(Collections.reverseOrder()); //reverse order

queue.offer(); // add contents

while( !queue.isEmpty()){
	System.out.println(queue.poll());
} // the smallest number becomes highest priority

// when the string is variable, A will be the high priority,


## LinkedLists   
   
Each data has several index(address)   

Each node has address which is clue for where the next node is   

We need to start from the head until the data will be founded   
   
### doubly linked list   
use more memory but can traverse between linked list  

LinkedList<String> linkedList = new LinkedList<String>();   

LinkedList.push("A"); // [A]   
LinkedList.push("B");  // same with offer();  
LinkedList.push("C");   
LinkedList.push("D");    
LinkedList.push("F");  
LinkedList.pop(); // F willl be pop / same with poll();   

linkedList.add(4,"E"); [A,B,C,D,E,F]   
linkedList.remove("E"); [A,B,C,D,F]   
// .indexof("B"); find the index   
linkedList.peekFisrt(); [A]   
linkedList.peekLast(); [F]   
addFirst & addLast ();    
removeFirst();   
removeLast();   

LinkedList = stores node in 2 parts data + address   

singly linked list  [data| address] - > one direction   
doubly linked list = [address | data | address ] <-> double direction   
adv:   
allocates needed memory while running   
editing list is O(1)   
low memory waste   

disadv:
Greater memory usage   
No random access of elements   
accessing searching elements is more time consuming

use:
Stack,Queue
GPS, music playlist


## Dynamic Array   
Array with re-sizeable capacity
Static Array : new String[capacity]

we can't increase capacity when we fix   
   
dynamic array : new String[capacity *2]

advantage:   
random access of elements o(1)constant   
good locality of reference and data cache utilization   
easy to insert/delete   

disadvan:    
wastes more memory   
shifting elemtns is time consuming O(n)   
expanding/shrinking the array is time consuming O(n)   
    
//ArrayList<String> arrayList = new ArrayList();

   
   
int size;
int capacity = 10;
Objcet[] array;

public DynamicArray(){
	this.array = new Object[capacity];
}    
public DynamicArray(int capacity){
	this.capacity = capacity
	this.array = new Object[capacity];
}   

public void add(Object data){
	if (size >= capacity){
		grow();
	}
	array[size] = data;
	size++;
}   
public void insert(int index, Object data){
	if(size >= capacity){
	grow();
	}
	for(int i = size; i > index; i--){
	array[i] = array[i - 1];
	}
	array[index] = data;
	size++;
}   
public void delete(Object data){
	for (int i =0; i < size; i++){
	if(array[i] == data){
		for(int j =0; j< (size - 1 -1); j++{
		array[i + j] = array[i + j + 1];
		}
		array[size -1] = null;
		size --;
		if(size <= (int) (capacity/3)){
		shrink();
			}
		break;
	}
	}
}   
public int search(Object data){
	
	for(int i =0; i < size; i++){
	if(array[i] == data){
		return i;	
}
	}
	return -1;
}   
public void grow(){
	int newCapacity =(int) (capacity *2)
	Object[] newArray = new Object[newCapacity];
	
	for(int i = 0; i < size; i ++ ){
	newArray[i] = array[i];
	} 
	capacity = newCapacity;
	array = newArray;
}   
public void shirnk(){
	int newCapacity =(int) (capacity / 2)
	Object[] newArray = new Object[newCapacity];
	
	for(int i = 0; i < size; i ++ ){
	newArray[i] = array[i];
	} 
	capacity = newCapacity;
	array = newArray;
}
public boolean isEmpty(){
	return size ==0;
}    
public String toString(){
	String string = "";
	for(int i = 0; i < capacity; i++){ // size or capacity capacity show all list
	string += array[i] + ", ";
}
	if(string != ""){
		string = "[" + string.substring(0, string.length() - 2) + "]";
	}
	else{
	string = "[]";
	}
	return string;
} 

public static Void main(String[] args] {
	Dynamic Array dynamicArray = new DynamicArray(5);

	dynamicArray.add("A");
	dynamicArray.add("B");
	
	dynamicArray.insert(0,"X"); //size change and put in index
	dynamicArray.delete("A"); // size change and capacity does not change
	dynamicArray.search("B"); // find location

	System.out.println("size: " + dynamicArray.size);
	System.out.println("capacity: " + dynamicArray.capacity);		
}

## linkedList, ArrayList
ArrayList is faster a little bit.   // when i use get()
### Because LinkedList is doubly linked
ArrayList is slower when i use remove(0);
### Because we need to shift elements after remove
#### but when the number becomes bigger LinkekdList becomes Slower

## Big O notation
"how code slows as data grows"   
### performance of an algorithm as the amount of data increases
machine independent, igonre smaller operations

### O(n) : takes the same steps with volume of num
### O(1) : the input size doesn't matter take only same steps
![image](https://github.com/user-attachments/assets/df0379d0-4fe5-471a-936d-8cf2b6defe72)

## Linear Search
### Iterate through a collection one element at a time    
### run time complexity : 0    
### disadvantages: slow for large data     
### adv: fast for searches of small to medium / does not need to sorted/ useful for data structures that do not have random access
public class Main {

	public static void main(String[] ags){
		
		int[] array = {9,2,3,5,1,7,3,5};
		
		int index = linearSearch(array,4);
		
		if(index != -1) {
			System.out.println("Element found at index: " + index);
		}else {
			System.out.println("Element not found");
		}
		
	}

	private static int linearSearch(int[] array, int value) {
		
		for(int i = 0; i < array.length; i++) {
			if(array[i] == value) {
				return i;
			}
		}
		return -1;
	}
}
## Binary Search
### search algorithm that finds the position of a target value within a sorted array. Half of the array is eliminated during each step
### O(log N) type

value = "H";    
index = ?'     

public class Main {

	public static void main(String[] ags){
		int array[] = new int[1000000];
		int target = 42333;
		
		for(int i = 0; i < array.length; i++) {
			array[i] = i;
		}
		// int index = Arrays.binarySearch(array, target);
		int index = binarySearch(array, target);
		
		if(index == -1) {
			System.out.println(target + " not found");
		}
		else {
			System.out.println("Element found at " + index);
		}
	}

	private static int binarySearch(int[] array, int target) {
		// TODO Auto-generated method stub
		int low = 0;
		int high = array.length -1;
		
		while(low <= high) {
			int middle = low + (high - low) /2;
			int value = array[middle];
			
			System.out.println("middle: " + value);
			
			if(value < target) {
				low = middle + 1;
			}
			else if(value > target){
				high = middle -1;
			}else {
				return middle; // target found
			}
		}
		
		return -1;
	}
}

## Interpolation search
public class Main {

	public static void main(String[] ags){
		
		// interpolation search: improvement over binary search best used for uniformally distributed data
		// "Guesses" where a value might be based on calculated probe results
		// if probe is incorrect, search area is narrowed and a new probe is calculated
		
		// average case : O(log(log(n))) / worst : O(n)
		
		
		int[] array = {1,2,5,16,32,64,128,256,512};
		
		int index = interpolationSearch(array, 256);
		
		if(index != -1) {
			System.out.println("Element found at index: " + index);
		}else {
			System.out.println("Element not found");
		}
	}

	private static int interpolationSearch(int[] array, int value) {
		
		int high = array.length -1;
		int low = 0;
		
		while(value >= array[low] && value <= array[high] && low <= high) {
			int probe = low + (high - low) * (value - array[low]) / 
					(array[high] - array[low]);
			
			System.out.println("Probe : " + probe);
			
			if(array[probe] == value) {
				return probe;
			}
			else if(array[probe] < value) {
				low = probe +1;
			}else {
				high = probe -1;
			}
		}
		
		return -1;
	}
}
## Bubble sort
public class Main {

	public static void main(String[] ags){
	
		// Bubble sort : used when sort, compare between two and use temp store to temporary
		// ineffective because compare one by one until the end
		// O(n^2)
		
		int array[] = {9,1,2,3,8,7,5,4,6};
		
		bubbleSort(array);
		
		for(int i : array) {
			System.out.print(i);
		}
	
	}

	private static void bubbleSort(int array[]) {
		
		for(int i = 0; i < array.length -1; i++) {
			for(int j = 0; j < array.length -1; j++) {
			
				if(array[j]> array[j+1]) {
					int temp = array[j];
					array[j] = array[j+1];
					array[j+1] = temp;
				}
			}
		}
		
	}
	
 }
 ## Selection sort
 public class Main {

	public static void main(String[] ags){
	
		//Selection sort : search through an array and keep track of the minimum value during iteration
		// at the end. we swap variables
		//O(n^2)
		
		int array[] = {8,7,9,2,1,3,5,4,6};
	
		selectionSor(array);
		
		for(int i : array) {
			System.out.print(i);
		}
		
	}

	private static void selectionSor(int[] array) {
		for(int i = 0; i<array.length -1; i++) {
			int min = i;
			
			for(int j = i+1; j < array.length -1; j++) {
				if(array[min] > array[j]) {
					min = j;
				}
			}
			int temp = array[i];
			array[i] = array[min];
			array[min] = temp;
		}
		
	}
	
 }

## Insertion sort
public class Main {

	public static void main(String[] ags){
		
		//insertion sort : after comparing elements to left shift elements to right
		// O(n^2)
		// less steps than bubble , best case is O(n)
	
		int array[] = {9,1,8,2,7,3,6,5,4};
		
		insertionSrot(array);
		
		for(int i : array) {
			System.out.print(i + " ");
		}
	}

	private static void insertionSrot(int[] array) {
		
		for(int i = 1; i < array.length; i++) {
			int temp = array[i];
			int j = i-1;
			
			while(j >= 0 && array[j] > temp) {
				array[j + 1] = array[j];
				j--;
			}
			array[ j + 1] =temp;
		}
		
	}
	
 }
## Recursion
public class Main {
	//Recursion : when a thing is defined in terms of itself
			// apply the result of procedure to a procedure
			// recursive method calls itself, can be a substitute for iteration
			// divide a problem into sub problems of the same type as the original
			// commonly used with advanced sorting algorithms and navigating trees
			
			// advantage: easier to read/ debug
			// disadvantage : sometimes slower/use more memory

	public static void main(String[] ags){
				
		System.out.println(power(2,4));
		
		
	
	}

	private static int power(int base, int exponent) {
	
		if(exponent <1) return 1; //base case
		return base * power(base, exponent -1); //recursive case
		
	}
		
 }
## Merge sort
public class Main {


	public static void main(String[] ags){
	
		//Merge sort: 
		//O(n logn)
		
		int[] array = {8,2,5,4,3,6,7,1};
		mergeSort(array);
		
		for(int i =0; i < array.length; i++) {
			System.out.print( array[i] + " ");
		}
		
	}

	private static void mergeSort(int[] array) {
		
		int length = array.length;
		if(length <= 1) return; //base case
		
		int middle = length / 2;
		int[] leftArray = new int[middle];
		int[] rightArray = new int[length -middle];
		
		int i =0; //left array
		int j = 0; //right array
		
		for(; i < length; i ++) {
			if(i < middle) {
				leftArray[i] = array[i];
			}
			else {
				rightArray[j] = array[i];
				j++;
			}
		}
		mergeSort(leftArray);
		mergeSort(rightArray);
		merge(leftArray, rightArray, array);
		
	}
	private static void merge(int[] leftArray, int[]rightArray, int[] array) {
		int leftSize = array.length /2;
		int rightSize = array.length - leftSize;
		int i = 0, l =0, r= 0; //indices
		
		//check the conditions for merging
		while(l < leftSize && r < rightSize) {
			if(leftArray[l] < rightArray[r]) {
				array[i] = leftArray[l];
				i++;
				l++;
			}
			else {
				array[i] = rightArray[r];
				i++;
				r++;
			}
		}
		while(l < leftSize) {
			array[i] = leftArray[l];
			i++;
			l++;
		}
		while(r < rightSize) {
			array[i] = rightArray[r];
			i++;
			r++;
		}
	}
		
 }

## Quick Sort
public class Main {


	public static void main(String[] ags){
	
		int[] array = {8,2,5,3,7,9,4,6,1};
		
		quickSort(array, 0, array.length -1);
		
		for (int i : array) {
			System.out.print(i + " ");
		}
	}

	private static void quickSort(int[] array, int start, int end) {
		
		if(end <= start) return; //base case
		int pivot = partition(array,start, end);
		quickSort(array, start, pivot -1);
		quickSort(array, pivot + 1, end);
		
	}
	private static int partition(int[] array, int start, int end) {
		
		int pivot = array[end];
		int i = start -1;
		for(int j = start; j <= end - 1; j++) {
			if(array[j] < pivot) {
				i++;
				int temp = array[i];
				array[i] = array[j];
				array[j] = temp;
			}
		}
		i++;
		int temp = array[i];
		array[i] = array[end];
		array[end] = temp;
		
		return i;
	}
		
 }
## Hash Table
public class Main {


	// hashing : takes a key and computes an integer
	
	// In hash table we use the hash % capacity to calculate an index number
	// key.hasCode() % capacity = index
	// collision : hash function generates the same index for more than one key
	// less collision = more efficiency
	// Run time complexity: Best case O(1)
	public static void main(String[] ags){
	
		Hashtable<String, String> table = new Hashtable<>(10,0.5f);//<key,Vlaue>
		
		table.put("100", "SpongeBob");
		table.put("123", "Patrick");
		table.put("321", "Sandy");
		table.put("555", "Squidward");
		table.put("777", "Gary");
		
		//table.remove(777);
	
		for(String key : table.keySet()) {
			System.out.println(key.hashCode() %10 + "\t"+ key + "\t" + table.get(key));
			// different key has different hascode
			// we have two collision as 5 and 0 appears two time
			// if we increase capacity of hashtable collision will be disappear
			
		}
  }
  }
## graphs intro
	// undirected graph: do not contains a direction   
	//directed graph : have access on another   
	// if adjacency have adjacency shows 1   
	// time complexity = O(1) / space complexity O(n^2)    
	    
	//adjacency list : array or array list has header and node find the direction   
	// time : O(n) / space : O(n +e number of adjancey)   
	// model of network   
 
 ## adjacency matrix
 public class Main {
	
	public static void main(String[] ags){
		// adjacency matrix : an array to store 1's/0's to represents edges
		//						# of rows = # of unique nodes
		//						# of columns = # of unique nodes
		
		// runtime complexity to check an edge : O(1);
		// 		space complexity : O(v^2)
		
		Graph graph = new Graph(5);
		
		graph.addNode(new Node('A'));
		graph.addNode(new Node('B'));
		graph.addNode(new Node('C'));
		graph.addNode(new Node('D'));
		graph.addNode(new Node('E'));
		
		graph.addEdge(0,1);
		graph.addEdge(1,2);
		graph.addEdge(2,3);
		graph.addEdge(2,4);
		graph.addEdge(4,0);
		graph.addEdge(4,2);
		
		graph.print();
		System.out.println(graph.checkEdge(3,2));
		
		
	}
		
 }
public  class Graph{
	
	ArrayList<Node> nodes;
	int[][] matrix; //2Darray
	
	Graph(int size){
		nodes = new ArrayList<>();
		matrix = new int[size][size];
	}
	public void addNode(Node node) {
		nodes.add(node);
	}
	public void addEdge(int src, int dst) {
		matrix[src][dst] = 1;
	}
	public boolean checkEdge(int src, int dst) {
		if(matrix[src][dst] == 1) {
			return true;
		}
		else {
			return false;
		}
		
	}
	public void print() {
		System.out.print("  ");
		for(Node node : nodes) {
			System.out.print(node.data + " ");
		}
		System.out.println();
		
		for(int i = 0 ; i < matrix.length; i++){
			System.out.print(nodes.get(i).data + " ");
			for(int j = 0; j < matrix[i].length; j++) {
				System.out.print(matrix[i][j] + " ");
			}
			System.out.println();
			}
		}

}
public class Node {
	
	char data;
	
	Node(char data){
		this.data = data;
	}

}
## adjacency list
public class Main {
	
	public static void main(String[] ags){
		// adjacency List: an array/arrayList maed of linkedlists
		// Each linkedlist has a unique node at the head.
		// ALl adjacent neighbors to taht node are added to that node's linkedlist
	
		// run time : O(n)
		// space : O(n +e)
		
		
		Graph graph = new Graph(5);
		
		graph.addNode(new Node('A'));
		graph.addNode(new Node('B'));
		graph.addNode(new Node('C'));
		graph.addNode(new Node('D'));
		graph.addNode(new Node('E'));
		
		graph.addEdge(0,1);
		graph.addEdge(1,2);
		graph.addEdge(1,4);
		graph.addEdge(2,3);
		graph.addEdge(2,4);
		graph.addEdge(4,0);
		graph.addEdge(4,2);
		
		graph.print();
		
		
		
	}
		
 }
 public  class Graph{
	
	ArrayList<LinkedList<Node>> alist;
	
	Graph(int size){
		alist = new ArrayList<>();
	
		}
	public void addNode(Node node) {
		LinkedList<Node> currentList = new LinkedList<>();
		currentList.add(node);
		alist.add(currentList);
	}
	public void addEdge(int src, int dst) {
		LinkedList<Node> currentList = alist.get(src);
		Node dstNode = alist.get(dst).get(0);
		currentList.add(dstNode);
	}
	public boolean checkEdge(int src, int dst) {
		LinkedList<Node> currentList = alist.get(src);
		Node dstNode = alist.get(dst).get(0);
		
		for (Node node : currentList) {
			if(node == dstNode) {
				return true;
			}
		}
		return false;
	}
	public void print() {
		for(LinkedList<Node> currentList : alist) {
			for(Node node : currentList) {
				System.out.print(node.data + " = >  ");
			}
			System.out.println(" ");
		}
		
	}

}
public class Node {
	
	char data;
	
	Node(char data){
		this.data = data;
	}

}
