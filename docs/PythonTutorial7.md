```python
import reprlib
```


```python
print(set('fdlfdhjgfnffgnlmgfnlfgmnl'))
```

    {'h', 'm', 'd', 'f', 'n', 'l', 'g', 'j'}
    


```python
print(reprlib.repr(set('fdlfdhjgfnffgnlmgfnlfgmnl')))
```

    {'d', 'f', 'g', 'h', 'j', 'l', ...}
    


```python
import pprint
```


```python
pprint.pprint(['a','b','u'],width=4)
```

    ['a',
     'b',
     'u']
    


```python
import textwrap
doc="jbbbjnknknk njnhnjnjjh nknjhnjnj njhjhbjhbjbjhb"
print(textwrap.fill(doc,width=5))
```

    jbbbj
    nknkn
    k njn
    hnjnj
    jh nk
    njhnj
    nj nj
    hjhbj
    hbjbj
    hb
    


```python
import locale
```
print(locale.localeconv)

```python
from string import Template
t=Template('$str1 every $str2')
print(t.substitute(str1='Hi',str2='one'))
```

    Hi every one
    


```python
print(t.safe_substitute(str1='Hi'))
```

    Hi every $str2
    


```python
import struct 
```


```python
var=struct.pack('hii',1,7,9)
print(var)
var=struct.pack('iii',1,7,9,10)
print(var)
```

    b'\x01\x00\x00\x00\x07\x00\x00\x00\t\x00\x00\x00'
    


    ---------------------------------------------------------------------------

    error                                     Traceback (most recent call last)

    <ipython-input-16-24b5667d4739> in <module>
          1 var=struct.pack('hii',1,7,9)
          2 print(var)
    ----> 3 var=struct.pack('iii',1,7,9,10)
          4 print(var)
    

    error: pack expected 3 items for packing (got 4)



```python
import threading,time
class Task(threading.Thread):
    def __init__(self,thread_number):
        threading.Thread.__init__(self)
        self.thread_number=thread_number
    def run(self):
        time.sleep(self.thread_number)
```


```python
t1=Task(5)
t2=Task(8)
t1.start()
t2.start()
t1.join()
t2.join()
```


```python
import logging
logging.debug('DEBUG')
```


```python
logging.warning('Warning')
```

    WARNING:root:Warning
    


```python
import weakref , gc
```


```python
class A:
    def __init__(self,value):
        self.value=value
    def __repr__(self):
        return str(self.value)
```


```python
a=A(10)
d=weakref.WeakValueDictionary()
d['b']=a
print(d['b'])
```

    10
    


```python
del a
```


```python
d['b']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-27-dee353b142fb> in <module>
    ----> 1 d['b']
    

    F:\Anaconda\lib\weakref.py in __getitem__(self, key)
        135         if self._pending_removals:
        136             self._commit_removals()
    --> 137         o = self.data[key]()
        138         if o is None:
        139             raise KeyError(key)
    

    KeyError: 'b'



```python
from array import array
```


```python
a=array('H',[10,30])
print(sum(a))
```

    40
    


```python
from collections import deque
d=deque()
d.append('1')
print(d)
d.popleft()
print(d)
```

    deque(['1'])
    deque([])
    


```python
li=[(1,'a'),(2,'c'),(4,'e')]
import bisect 
bisect.insort(li,(3,'b'))
```


```python
li
```




    [(1, 'a'), (2, 'c'), (3, 'b'), (4, 'e')]




```python
from heapq import heapify , heappop, heappush
data=[14,67,10]
```


```python
heapify(data)
```


```python
heappush(data,-1)
```


```python
heappop(data)
```




    -1




```python
from decimal import *
round(Decimal('0.78888080'),2)
```




    Decimal('0.79')




```python

```
