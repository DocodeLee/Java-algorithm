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
