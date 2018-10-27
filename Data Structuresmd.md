# Built-in sequences
## 1. Container sequences vs Flat sequences
* To highlight the different memory models of the sequence types I used the terms container sequence and flat sequence. 
  The “container” word is from the Data Model documentation: Some objects contain references to other objects; these are called containers.
* Container sequences: list, tuple and collections.deque can hold items of different types
* Flat sequences: str, bytes, bytearray, memoryview and array.array hold items of one type.
* example
```
board = [['_'] * 3 for i in range(3)]
board[1][2] = 'X'
board

#The outer list is made of three references to the same inner list. While it is unchanged, all seems right
weird_board = [['_'] * 3] * 3
weird_board[1][2] = 'O'
weird_board
```

## 2. Named tuples
* Instances of a class that you build with namedtuple take exactly the same amount of memory as tuples because the field names are stored in the class. 
  They use less memory than a regular object because they do store attributes in a per-instance __dict__.
```
from collections import namedtuple
City = namedtuple('City', 'name country population coordinates')
tokyo = City('Tokyo', 'JP', 36.933, (35.689722, 139.691667))
tokyo
```

## 3. Dictionary
### 1.  Ordered dictionary
  * collections.OrderedDict: maintains keys in insertion order, allowing iteration over items in a predictable order. 
  The popitem method of an OrderedDict pops the first item by default, 
  but if called as my_odict.popitem(last=True), it pops the last item added
  * Example
```
import collections
d = collections.OrderedDict() 
# d= {}
d['a'] = 'A'
d['b'] = 'B'
d['c'] = 'C'
d['d'] = 'D'
d['e'] = 'E'

for k, v in d.items():
    print k, v
```
### 2. Properties
* 1. Keys must be hashable objects
* 2. dicts have significant memory overhead
  Because a dict uses a hash table internally, and hash tables must be sparse to work, they are not space efficient. 
  For example, if you are handling a large quantity of records it makes sense to store them in a list of tuples or named tuples instead of using a list of dictionaries in JSON style, with one dict per record. 
  Replacing dicts with tuples reduces the memory usage in two ways: by removing the overhead of one hash table per record and by not storing the field names again with each record.
* 3. Key search is very fast
* 4. Key ordering depends on insertion order
* 5. Adding items to a dict may change the order of existing keys
  Whenever you add a new item to a dict, the Python interpreter may decide that the hash table of that dictionary needs to grow. This entails building a new, bigger hash table, and adding all current items to the new table. During this process, new (but different) hash collisions may happen, with the result that the keys are likely to be ordered differently in the new hash table. All of this is implementation-dependent, so you cannot reliably predict when it will happen. **If you are iterating over the dictionay keys and changing them at the same time, your loop may not scan all the items as expected — not even the items that were already in the dictionary before you added to it.**

### 3. Comparision of sizes
```
from collections import namedtuple
import sys

City = namedtuple('City', 'name country population coordinates')
tokyo_list = ['Tokyo', 'JP', 36.933, (35.689722, 139.691667)]
tokyo = tuple(tokyo_list)
tokyo_nt = City(*tokyo_list)
tokyo_ordered_dict = tokyo_nt._asdict()
tokyo_dict = dict(tokyo_dict)

print("""
size of list: %s
size of tuple: %s
size of named tuple: %s
size of dictionary: %s
size of ordered dictionary: %s
"""%(sys.getsizeof(tokyo_list), sys.getsizeof(tokyo), sys.getsizeof(tokyo_nt), sys.getsizeof(tokyo_dict), sys.getsizeof(tokyo_ordered_dict)))

```
