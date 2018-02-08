
**Java Collection Framework**

A Java Collection is group of individual objects represented as a Single Unit. The Collection interface (java.util.Collection) and Map interface (java.util.Map) are two main root interfacess of Java Collection classess. 

                                   **Hierarchy of Collection Framework**

![alt text](https://github.com/imhimanshu/booknotes/blob/master/01-Collection-framework-hierarchy-in-java.png)

Collection : Root interface with basic methods like add(), remove(), 
             contains(), isEmpty(), addAll(), ... etc.
 
**Set :** Doesn't allow duplicates. Example implementations of Set interface are HashSet (Hashing based) and TreeSet (balanced
      BST based). Note that TreeSet implements SortedSet.

**List :** Can contain duplicates and elements are ordered. List preserves the insertion order, so it allows positional access and insertion of elemets. List interface implemented by LinkedList (linked list based) and ArrayList (dynamic array based), Vector, Stack classes. 

It allows get,set, removal, add operation based on numerical position of elements in List. 

**Java.util.ArrayList Class:** ArrayList inherits AbstractList class and implements List interface, it initialize by size but its size can grows and shrink, due to these feature it is little bit slow as compare to standard arrays. It allows randomly access the list It cannot be used by primitive types, likt int, chat etc. It require wrapper class to for this case. 

**Java.util.Vector Class:** It extends AbstractList and implements List interfaces.The Vector class implements a growable array of objects. Vectors basically falls in legacy classes but now it is fully compatible with collections.

  - Vector implements a dynamic array that means it can grow or shrink as required. Like an array, it contains components that can be accessed using an integer index
  - They are very similar to ArrayList but Vector is synchronised and have some legacy method which collection framework does not contain.

If increment is specified, Vector will expand according to it in each allocation cycle but if increment is not specified then vector’s capacity get doubled in each allocation cycle. Vector defines three protected data member:

    int capacityIncreament: Contains the increment value.
    int elementCount: Number of elements currently in vector stored in it.
    Object elementData[]: Array that holds the vector is stored in it.

**Queue :** Typically order elements in FIFO order except exceptions like PriorityQueue.  

**Deque :** Elements can be inserted and removed at both ends. Allows both LIFO and FIFO. 

**Map :** Contains Key value pairs. Doesn't allow duplicates.  HashMap and TreeMap. TreeMap implements SortedMap.        

The difference between Set and Map interface is, in Set we have only keys, but in Map, we have key value pairs.
                             
  
