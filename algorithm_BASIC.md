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




