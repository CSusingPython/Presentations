<<<<<<< HEAD

=======
## Dynamic Programming
### Concepts
* Definition: Simplifying a complicated problem by breaking it down into simpler sub-problems in a recursive manner
* Key point is that it **reuses** the results from othre sub-problems

### Fibonacci Sequence is one of best example of dynamic programming
* The following is recursive
* It is very very slow: O(2^n)
```
def naive_fibo(n):
    if n==1 or n==2: return(n)
    return naive_fibo(n-1)+naive_fibo(n-2)
```
* Using dynamic programming
* Faster: O(n)
```
def dynamic_fibo(n):
    fibo_seq = [1,1]
    for i in range(2, n):
        fibo_seq.append(sum(fibo_seq[i-2:i]))
    #print(fibo_seq)
    return fibo_seq[-1]
```
* While engineering features, dynamic programming may be useful. 
* I have benefited from it when I was at work, in fact.
>>>>>>> 0195b326bcc0b294d4c7585a23fb771d2f484d4d
