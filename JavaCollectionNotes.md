
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

**Deque :** Elements can be inserted and removed at both ends. Allows both LIFO and FIFO. 

**Map :** Contains Key value pairs. Doesn't allow duplicates.  HashMap and TreeMap. TreeMap implements SortedMap.        

The difference between Set and Map interface is, in Set we have only keys, but in Map, we have key value pairs.
                             
  
