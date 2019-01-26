

## Dynamic Programming
### Concepts
* Definition: Simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner
* Key point is that it **REUSES** the results from othre sub-problems

### Fibonacci Sequence is one of best example of dynamic programming
* An example of recursive function is below
* Computational cost is very expensive : O(2^n)
```
def naive_fibo(n):
    if n==1 or n==2: return(n)
    return naive_fibo(n-1)+naive_fibo(n-2)
```
* The solution with DP is following
* Computational cost is much chipper: O(n)
```
def dynamic_fibo(n):
    fibo_seq = [1,1]
    for i in range(2, n):
        fibo_seq.append(sum(fibo_seq[i-2:i]))
    #print(fibo_seq)
    return fibo_seq[-1]
```
* While engineering features, dynamic programming may be useful. 

### Another example
**Q. Create a function which calculate the value of the nth elemetnt of the following series**

![equation](https://latex.codecogs.com/gif.latex?%5Csum_%7Bi%7D%5E%7Bn%7D%5Cfrac%7B1%7D%7B%5Csum_%7Bj%7D%5E%7Bi%7Dj%7D)  

* I solved it with three different ways

1. Naive sum; there's nothing special
```
def naive_sum(n):
    res_temp= []
    for i in range(1, n+1):
        temp = sum(range(1,i+1))
        res_temp.append(1/temp)
        #print(temp)
    return sum(res_temp)
```  
2. Series sum; it uses the property of arithmetic sequence
```
def series_sum(n):
    parts = [2/(i**2 + i) for i in range(1,n+1)]
    #print(parts)
    return sum(parts)
```  
3. Danymic sum; it uses the dynamic programming 
 ```
 def dynamic_sum(n):
    memory = 0
    parts = []
    for i in range(1,n+1):
        memory += i
        parts.append(1/memory)
    #print(parts)
    return sum(parts)
```  
* Intuitevely, the second one is simplest and seems fastest 
* However, the third one with dynamic programming is two times faster than the second one
