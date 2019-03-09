# 네임스페이스 (Namespace)

네임스페이스를 정리하기 전에 아래의 두 가지를 명심해야 한다.   


1. 모든 것은 객체이다.
2. 모든 변수는 포인터이다.    


위의 두 가지를 통해 ```Python```에서 데이터 타입은 ```class```뿐임을 알 수 있다.   
아래는 Python Global namespace, Local namespace의 예시이다.



Global space 예시   
```
a = 3
globals()
"""
실행 결과
{'__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__package__': None, '__doc__': None, '__name__': '__main__', 'a': 3, '__builtins__': <module 'builtins' (built-in)>}
"""

globals()['a']
# 실행결과 3
```


Local namespace 예시
```
def add_x_y(x,y):
    print(locals())
    return x+y

"""
# add_x_y(1,2) 실행 시 
{'y': 2, 'x': 1}
"""
```


Namespace와 Class는 함께 보면 좋다.
```
# 모든 Python의 class는 object를 상속 받아 객체
class Foo(object):
    A = 1
    B = 2
    def __init__(self):
            self.a=1
            self.b=2

dir(Foo)
"""
실행결과
['A', 'B', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']
"""

foo = Foo()
dir(foo)
['A', 'B', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'a', 'b']
```
