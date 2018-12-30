# Garbage Collection

## refer
* https://blog.naver.com/hahava/221313725494
* https://winterj.me/python-gc/
* http://www.arctrix.com/nas/python/gc/
* https://en.wikipedia.org/wiki/Object_(computer_science)
* https://www.ibm.com/support/knowledgecenter/en/SSYKE2_7.0.0/com.ibm.java.win.70.doc/diag/understanding/mm_gc.html

### Key concepts
* Object: an object can be a variable, a data structure, a function, or a method, and as such, is a value in memory *referenced* by an identifier.
* Garbage collection: The garbage collector, or just collector, attempts to reclaim garbage, or memory occupied by objects that are no longer in use by the program
* Reference count: In computer science, reference counting is a technique of storing the number of references, pointers, or handles to a resource such as an object, block of memory, disk space or other resource.

### Kinds of garbage
* Objects whose reference count is zeros
* Objects with only cycled reference such as only refered by the object it self or two objects which only refered by each other
  * ex) l = []; l.append(l)
  * There is an algorithm which detects above objects

### Object generation
* Most objects are not used after some time
* JVM, on which spark is run, divide the memory area in to three generation: young, old, and permenant generation
* New objects are allocated in young generation
* When young generation is full, GC occurs and survived objects are moved to old generation

### Garbage collection in python
* Python’s memory allocation and deallocation method is automatic. The user does not have to preallocate or deallocate memory similar to using dynamic memory allocation in languages such as C or C++.
* Because reference cycles take computational work to discover, garbage collection must be a scheduled activity.
  * When the number of allocations minus the number of deallocations are greater than the threshold number, the garbage collector is run. 
