
**Java Collection Framework**

A Java Collection is group of individual objects represented as a Single Unit. The Collection interface (java.util.Collection) and Map interface (java.util.Map) are two main root interfacess of Java Collection classess. 

                                   **Hierarchy of Collection Framework**

![alt text](https://github.com/imhimanshu/booknotes/blob/master/01-Collection-framework-hierarchy-in-java.png)

Collection : Root interface with basic methods like add(), remove(), 
             contains(), isEmpty(), addAll(), ... etc.
 
**Set :** 
interface which extends Collection, unordered collection of object and it doesn't allow duplicates. Example implementations of Set interface are HashSet (Hashing based), LinkedSet and TreeSet (balanced BST based). Note that TreeSet implements SortedSet.

**Java.util.HashSet :** 
Impletements Set interface, underlying data structure for HashSet is hashtable, insertion ordered not maintain, object inserted based on their hash code. 
  Null entry allowed in HashSet
  HashSet also implements Searlizable and Cloneable interface

**Java.util.LinkedHashSet :** 
It is just ordered version of HashSet, It maintain insertion order of objects. When iteration order is needed this is useful class. LinkedHashSet lets us iterate through the elements in the order in which they were inserted.

LinkedHashMap does a mapping of keys to values whereas a LinkedHastSet simply stores a collection of things with no duplicates. LinkedHashMap extends HashMap and LinkedHashSet extends HashSet.

But maintain insertion order of objects have additional costs both interms of CPU cycles and need more memory.

**Initial Capcity and load factor :** Initial capcity means number of buckets when hashtable has been created, Number of buckets will automatically increase when hashtable is full.

Load factor is measure how full the HashSet is allowed to get before its capacity is automatically increased. When the number of entries in the hash table exceeds the products of the load factor and the current capacity, the hash table is rehased, so that the hash tables has approx twice the number of buckets. 

    load factor = Number of stored elements in table / Size of the hash table

If we increase load factor memory overhead decrease but it will affect add and search operation in hashtable. Because it will decrease internal rebuilding operation. If initial capcity is greater than the maximum number of entries divided by the load fator, no rehash operation will even occur. ideal value of load factor is 0.75 respect to time and space complexity. 

**Java.util.TreeSet :** 
TreeSet implements the SortedSet interface so duplicate values are not allowed. it does not preserve the insertion order of elements but elements are sorted by keys. TreeSet does not allow to insert Heterogeneous objects. It will throw classCastException at Runtime if trying to add hetrogeneous objects.

TreeSet is basically implementation of a self-balancing binary search tree like Red-Black Tree. Therefore operations like add, remove and search take O(Log n) time. And operations like printing n elements in sorted order takes O(n) time.

    TreeSet is not synchronized, it can be done externally using Collections.synchronized(<TreeSet);
    Null values not allowed in TreeSet, it will give NullPinterException
    TreeSet implements SortedSet so it has availability of all methods in Collection, Set and SortedSet interfaces.

**Java.util.EnumSet :**
EnumSet is one of the specialized implementation of Set interface for an enumeration type. It extends AbstractSet and implements Set Interface in Java.

    Generic class declared as public abstract class EnumSet<E extends Enum<E>>  

Here E specifies the elements. E must extend Enum, which enforces the requirement that the elements must be of specified enum type.

  EnumSet class is a member of the Java Collections Framework & is not synchronized.
  It’s a high performance set implementation, much faster than HashSet.
  All elements of each EnumSet instance must be elements of a single enum type.

**List :** 
Can contain duplicates and elements are ordered. List preserves the insertion order, so it allows positional access and insertion of elemets. List interface implemented by LinkedList (linked list based) and ArrayList (dynamic array based), Vector, Stack classes. 

It allows get,set, removal, add operation based on numerical position of elements in List. 

**Java.util.ArrayList Class:** 
ArrayList inherits AbstractList class and implements List interface, it initialize by size but its size can grows and shrink, due to these feature it is little bit slow as compare to standard arrays. It allows randomly access the list It cannot be used by primitive types, likt int, chat etc. It require wrapper class to for this case. 

**Java.util.Vector Class:** 
It extends AbstractList and implements List interfaces.The Vector class implements a growable array of objects. Vectors basically falls in legacy classes but now it is fully compatible with collections.

  - Vector implements a dynamic array that means it can grow or shrink as required. Like an array, it contains components that can be accessed using an integer index
  - They are very similar to ArrayList but Vector is synchronised and have some legacy method which collection framework does not contain.

If increment is specified, Vector will expand according to it in each allocation cycle but if increment is not specified then vector’s capacity get doubled in each allocation cycle. Vector defines three protected data member:

    int capacityIncreament: Contains the increment value.
    int elementCount: Number of elements currently in vector stored in it.
    Object elementData[]: Array that holds the vector is stored in it.

**Queue :** Typically order elements in FIFO order except exceptions like PriorityQueue.  

The **java.util.Queue** is a subtype of **java.util.Collection** interface. It is an ordered list of objects with its use limited to inserting elements at the end of list and deleting elements from the start of list i.e. it follows FIFO principle.
Since it is an interface, we need a concrete class during its declaration. There are many ways to initialize a Queue object, most common being -
  As a Priority Queue
  As a LinkedList
Please note that both the implementations are not thread safe. PriorityBlockingQueue is one alternative implementation if you need a thread safe implementation.

Operations on Queue :

  Add() - Adds an element at the tail of queue. More specifically, at the last of linkedlist if it is used, or according to the priority in case of priority queue implementation.
  peek() - To view the head of queue without removing it. Returns null if queue is empty.
  element() - Similar to peek(). Throws NoSuchElementException if queue is empty.
  remove() - Removes and returns the head of the queue. Throws NoSuchElementException when queue is impty.
  poll() - Removes and returns the head of the queue. Returns null if queue is empty.

Since it is a subtype of Collections class, it inherits all the methods of it namely size(), isEmpty(), contains() etc.

**PriorityQueue Class**
To process object in queue based on priority, called PriorityQueue. 

Important points of PriorityQueue:
  PriorityQueue doesn’t allow null
  We can’t create PriorityQueue of Objects that are non-comparable
  The elements of the priority queue are ordered according to their natural ordering, or by a Comparator provided at queue construction time, depending on which constructor is used.
  The head of this queue is the least element with respect to the specified ordering. If multiple elements are tied for least value, the head is one of those elements — ties are broken arbitrarily.
  The queue retrieval operations poll, remove, peek, and element access the element at the head of the queue.
  It inherits methods from AbstractQueue, AbstractCollection, Collection and Object class.

**Deque :** Elements can be inserted and removed at both ends. Allows both LIFO and FIFO. 

**Deque interface**
The **java.util.Deque** interface is a subtype of the **java.util.Queue** interface. The Deque is related to the double-ended queue that supports addition or removal of elements from either end of the data structure, it can be used as a queue (first-in-first-out/FIFO) or as a stack (last-in-first-out/LIFO).

Methods of deque:
    add(element): Adds an element to the tail.
    addFirst(element): Adds an element to the head.
    addLast(element): Adds an element to the tail.
    offer(element): Adds an element to the tail and returns a boolean to explain if the insertion was successful.
    offerFirst(element): Adds an element to the head and returns a boolean to explain if the insertion was successful.
    offerLast(element): Adds an element to the tail and returns a boolean to explain if the insertion was successful.
    iterator(): Returna an iterator for this deque.
    descendingIterator(): Returns an iterator that has the reverse order for this deque.
    push(element): Adds an element to the head.
    pop(element): Removes an element from the head and returns it.
    removeFirst(): Removes the element at the head.
    removeLast(): Removes the element at the tail.

**Map :**   
The **java.util.Map** interface represents a mapping between a key and a value. The Map interface is not a subtype of the Collection interface, therefor it behaves a bit different from rest of the collection types.

Contains Key value pairs. Doesn't allow duplicates. Some allow null key and null value (HashMap and LinkedHashMap) but some not (TreeMap). 

Maps are perfectly for key-value association mapping such as dictionaries. Use Maps when you want to retrieve and update elements by keys, or perform lookups by keys like A map of managers and employees. Each manager (Key) is associated with list of employees (Value) he manages.

The difference between Set and Map interface is, in Set we have only keys, but in Map, we have key value pairs.

**Java.util.HashMap :**

HashMap don’t allow duplicate keys, but allows duplicate values. That means A single key can’t contain more than 1 value but more than 1 key can contain a single value. HashMap allows null key also but only once and multiple null values. This class makes no guarantees as to the order of the map; in particular, it does not guarantee that the order will remain constant over time. It is roughly simillar to HashTable but is unsynchronized.

Internally HashMap contains an array of Node. and a node is represented as a class which contains 4 fields :

  int hash
  K key
  V value
  Node next

node is containing a reference of it own object, it is linked list. 

    Node<K,V>
    int hash
    K key
    V value
    Node<K,V> next

**Time complexity of HashMap**
HashMap provides constant time complexity for basic operations, get and put, if hash function is properly written and it disperses the elements properly among the buckets. Iteration over HashMap depends on the capacity of HashMap and number of key-value pairs. Basically it is directly proportional to the capacity + size. Capacity is the number of buckets in HashMap. So it is not a good idea to keep high number of buckets in HashMap initially.

**Performance of HashMap**
Performance of HashMap depends on 2 parameters:

  Initial Capacity
  Load Factor

Capacity is simply the number of buckets where and Initial Capacity is the capacity of HashMap instance when it is created. The Load Factor is a measure that when rehashing should be done. Rehashing is a process of increasing the capacity. In HashMap capacity is multiplied by 2. 

Load Factor is also a measure that what fraction of the HashMap is allowed to fill before rehashing. When the number of entries in HashMap increases the product of current capacity and load factor the capacity is increased that is rehashing is done. If we keep the initial capacity higher then rehashing will never be done. But by keeping it higher it increases the time complexity of iteration. So it should be choosed very cleverly to increase the performance. 

The expected number of values should be taken into account to set initial capacity. Most generally preffered load factor value is 0.75 which provides a good deal between time and space costs. Load factor’s value varies between 0 and 1.

**Synchronized HashMap**
HashMap is unsynchronized i.e. multiple threads can access it simultaneously. If multiple threads access this class simultaneously and at least one thread manipulates it structurally then it is necessary to make it synchronized externally. It is done by synchronizing some object which enzapsulates the map. If No such object exists then it can be wrapped around **Collections.synchronizedMap()** to make HashMap synchronized and avoid accidental unsynchronized access.

**HashMap and TreeMap**

    HashMap:  HashMap<K, V> hmap = new HashMap<K, V>();

HashMap does not maintain any order neither based on key nor on basis of value, If we want the keys to be maintained in a sorted order, we need to use TreeMap.

Complexity: get/put/containsKey() operations are O(1) in average case but we can’t guarantee that since it all depends on how much time does it take to compute the hash.

    TreeMap<K, V> hmap = new TreeMap<K, V>();

TreeMap can be a bit handy when we only need to store unique elements in a sorted order. Java.util.TreeMap uses a red-black tree in the background which makes sure that there are no duplicates; additionally it also maintains the elements in a sorted order.

For operations like add, remove, containsKey, time complexity is O(log n where n is number of elements present in TreeMap.

TreeMap always keeps the elements in a sorted(increasing) order, while the elements in a HashMap have no order. TreeMap also provides some cool methods for first, last, floor and ceiling of keys.

HashMap implements Map interface while TreeMap implements SortedMap interface. A Sorted Map interface is a child of Map.

HashMap implements Hashing, while TreeMap implements Red-Black Tree(a Self Balancing Binary Search Tree). Therefore all differences between Hashing and Balanced Binary Search Tree apply here.

Both HashMap and TreeMap have their counterparts HashSet and TreeSet. HashSet and TreeSet implement Set interface. In HashSet and TreeSet, we have only key, no value, these are mainly used to see presence/absence in a set.

**Hashmap vs Hashtable**
  1. HashMap is non synchronized. It is not-thread safe and can’t be shared between many threads without proper synchronization code whereas Hashtable is synchronized. It is thread-safe and can be shared with many threads.
  2. HashMap allows one null key and multiple null values whereas Hashtable doesn’t allow any null key or value.
  3. HashMap is generally preferred over HashTable if thread synchronization is not needed

Why HashTable doesn’t allow null and HashMap does?

To successfully store and retrieve objects from a HashTable, the objects used as keys must implement the hashCode method and the equals method. Since null is not an object, it can’t implement these methods. HashMap is an advanced version and improvement on the Hashtable. HashMap was created later.


    
    






                             
  
