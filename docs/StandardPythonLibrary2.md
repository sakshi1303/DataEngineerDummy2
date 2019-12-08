```python
import math
x,y=20,8
print(x+y)
print(x-y)
print(x//y)
print(x%y)
print(abs(x))
print(float(x))
print(complex(x,y))
```

    28
    12
    2
    4
    20
    20.0
    (20+8j)



```python
print(math.ceil(6.3))
print(math.floor(6.8))
print(round(8.912345,2))
```

    7
    6
    8.91



```python
print(x)
print(x|y)
print(x^y)
print(x&y)
print(x<<2)
print(x>>2)
print(~x)
```

    20
    28
    28
    0
    80
    5
    -21



```python
print(bin(x))
print(x.bit_length())
```

    0b10100
    5



```python
(1024).to_bytes(2,byteorder='big')
```




    b'\x04\x00'




```python
int.from_bytes(b'\x00\x10',byteorder='big')
```




    16




```python
print((0.55).as_integer_ratio())
```

    (2476979795053773, 4503599627370496)



```python
(-2.0).is_integer()
```




    True




```python
print(float.hex(32.0))
print(float.fromhex('0x1.0000000000000p+5'))
```

    0x1.0000000000000p+5
    32.0



```python
import sys
print(sys.hash_info)
```

    sys.hash_info(width=64, modulus=2305843009213693951, inf=314159, nan=0, imag=1000003, algorithm='siphash24', hash_bits=64, seed_bits=128, cutoff=0)



```python
x=iter([1,8,9])
print(x)
print(next(x))
```

    <list_iterator object at 0x7f60bb614ed0>
    1



```python
print(1 in [1,7])
print(str(1)*4)
```

    True
    1111



```python
l=[8,0]
l.sort()
```


```python
l
```




    [0, 8]




```python
tuple('123')
```




    ('1', '2', '3')




```python
list(range(7,10))
```




    [7, 8, 9]




```python
list(range(0,20,2))
```




    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]




```python
str(b'78')
```




    "b'78'"




```python
print('knknkn'.capitalize())
print('kkkk'.casefold())
print('kkkk'.center(10,'0'))
print('ababdab'.count('ab',4,10))
print('$'.encode('UTF-8'))
print('wow'.endswith('ows'))
print('wow'.endswith('ow'))
```

    Knknkn
    kkkk
    000kkkk000
    1
    b'$'
    False
    True



```python
print(('12\t123').expandtabs())
print(('12\t123').expandtabs(1))
```

    12      123
    12 123



```python
print(('xxababbbbab').find('ab'))
```

    2



```python
print('Sum of {0}'.format(2))
```

    Sum of 2



```python
class Default(dict):
    def __missing__(self,key):
        return key
print('{name} is in {country}'.format_map(Default(name='Guido')))
print('{name} is in {country}'.format_map(Default(names='Guido')))
```

    Guido is in country
    name is in country



```python
'xxababbbbbaa'.index('ab')
```




    2




```python
print('---'.isalnum())
print('--a'.isalnum())
print('sa'.isalnum())
print('sa'.isalpha())
print('````'.isascii())
print('````'.isdecimal())
print('456'.isdecimal())
print('456'.isdigit())
print('456a'.isdigit())
```

    False
    False
    True
    True
    True
    False
    True
    True
    False



```python
print('456a'.isidentifier())
print('True'.isidentifier())
print('str'.isidentifier())
```

    False
    True
    True



```python
from keyword import iskeyword
'hello'.isidentifier()
```




    True




```python
print('lmvfmvf'.islower())
print('lmvfmvf'.isupper())
print('1234r'.isnumeric())
print('1234'.isnumeric())
print('1234'.isprintable())
```

    True
    False
    False
    True
    True



```python
print('   ---'.isspace())
print('   '.isspace())
print('This is Great   '.istitle())
print('This Is Great   '.istitle())
```

    False
    True
    False



```python
print('-'.join(['This' , 'is']))
```

    This-is



```python
print('kkk'.ljust(9,'0'))
```

    kkk000000



```python
print('kkk000'.strip('0'))
```

    kkk



```python
'dfdf'.maketrans('fdf','ert')
```




    {102: 116, 100: 114}




```python
print('this.is.awesome'.partition('.'))
print('this is'.replace('this','it'))
print('this is'.rfind('is'))
print('this is'.rindex('is'))
print('this is'.rjust(10,'0'))
```

    ('this', '.', 'is.awesome')
    it is
    5
    5
    000this is



```python
print('this.is.awesome'.rpartition('.'))
print('this.is.awesome'.rsplit('.'))
print('this is wow '.rstrip('w'))
```

    ('this.is', '.', 'awesome')
    ['this', 'is', 'awesome']
    this is wow 



```python
print('this is split'.split())
print('this\nis\nsplit'.splitlines())
print('this is'.startswith('th'))
```

    ['this', 'is', 'split']
    ['this', 'is', 'split']
    True



```python
print('abcdefghijklemno'.strip('abcdfghijklmno'))
```

    efghijkle



```python
print('Abcde'.swapcase())
print('Hello world'.title())
print('Hello world'.translate({'Hello':'Hi'}))
print('Hello world'.upper())
print('Hello world'.zfill(100))
```

    aBCDE
    Hello World
    Hello world
    HELLO WORLD
    00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000Hello world



```python
print(bytes.fromhex('1223'))
print(bytes.hex(b'\x12#'))
```

    b'\x12#'
    1223



```python
v=memoryview(b'abcdefg')
print(v[1])
```

    98



```python
hash(4)
```




    4




```python
m = memoryview(b"abc")
m.tobytes()
```




    b'abc'




```python
memoryview(b'abc').tolist()
```




    [97, 98, 99]




```python
m=memoryview(bytearray(b'abc'))
m.release()
m[0]
m.toreadonly()
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-162-00af6c9d0b65> in <module>
          1 m=memoryview(bytearray(b'abc'))
          2 m.release()
    ----> 3 m[0]
          4 m.toreadonly()


    ValueError: operation forbidden on released memoryview object



```python
m=memoryview(bytearray(b'abc'))
y=m.cast('b')
print(y)
```

    <memory at 0x7f60bbf1e7a0>



```python
b=bytearray(b'xyz')
```


```python
print(set([1,5,5]))
print(frozenset([1,5,5]))
print(len(frozenset([1,5,5])))
print(5 in set([1,5,5]))
print(5 not in set([1,5,5]))
print(set([1,26]).isdisjoint(set([1,5,5])))
print(set([1,26]).isdisjoint(set([5,5])))
```

    {1, 5}
    frozenset({1, 5})
    2
    True
    False
    False
    True



```python
print(set([1,26]).issubset(set([5,5])))
print(set([5]).issubset(set([5,51])))
print(set([5]).union(set([5,51])))
print(set([5]) | set([5,51]))
print(set([5]) & set([5,51]))
print(set([5]) |= set([5,51]))
```


      File "<ipython-input-183-0ebcdf942223>", line 6
        print(set([5]) |= set([5,51]))
                        ^
    SyntaxError: invalid syntax




```python
x=set([1,89,90])
x.add(9)
print(x)
x.remove(9)
print(x)
x.pop()
print(x)
x.clear()
print(x)
```

    {89, 1, 90, 9}
    {89, 1, 90}
    {1, 90}
    set()



```python
a=dict(one=1,two=2)
print(a)
b=a.copy()
a={'one':1,'two':2}
print(a)
a=dict({'one':1,'two':2})
print(a)
a=dict(zip([1,2,3],['one','two','three']))
print(a,list(a),len(a) , a[1])
del a[2]
print(a , 2 in a , 3 in a , 2 not in a)
print(next(iter(a)),next(iter(a)))
a.clear()
print(a)
print(b)
```

    {'one': 1, 'two': 2}
    {'one': 1, 'two': 2}
    {'one': 1, 'two': 2}
    {1: 'one', 2: 'two', 3: 'three'} [1, 2, 3] 3 one
    {1: 'one', 3: 'three'} False True True
    1 1
    {}
    {'one': 1, 'two': 2}



```python
a=dict(zip([1,2,3],['one','two','three']))
dict.fromkeys((1,2),('one','two'))
print(a.get(1))
print(a.get(4,'default'))
print(a.items(),a.keys())
a.pop(1)
# print(reversed(a.keys()))
print(a)
a.popitem()
a.setdefault(6,'six')
print(a)
a.update({1:'ones'})
print(a , a.values())
```

    one
    default
    dict_items([(1, 'one'), (2, 'two'), (3, 'three')]) dict_keys([1, 2, 3])
    {2: 'two', 3: 'three'}
    {2: 'two', 6: 'six'}
    {2: 'two', 6: 'six', 1: 'ones'} dict_values(['two', 'six', 'ones'])



```python
len(a.keys())
s=iter(a.keys())
print(next(s),next(s) , 2 in a.keys() , reversed(a.keys()))
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-246-8fc1e0eb7daf> in <module>
          1 len(a.keys())
          2 s=iter(a.keys())
    ----> 3 print(next(s),next(s) , 2 in a.keys() , reversed(a.keys()))
    

    TypeError: 'dict_keys' object is not reversible



```python
with open('sample.txt') as f:
    print(f.read())
```

    Hello



```python
import sys
print(sys.__dict__['__name__'])
```

    sys



```python
class C:
    def method(self):
        pass
c=C()
c.method.whoami='Hello'
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-257-d5ca869d1c84> in <module>
          3         pass
          4 c=C()
    ----> 5 c.method.whoami='Hello'
    

    AttributeError: 'method' object has no attribute 'whoami'



```python
c.method.__func__.whoami='Hello'
```


```python
type(None)
type(Ellipsis)
```




    ellipsis




```python
print(C.__dict__)
print(c.__dict__)
print(c.__class__)
print(C.__bases__)
print(C.__mro__)
print(C.mro())
```

    {'__module__': '__main__', 'method': <function C.method at 0x7f60bb5ed320>, '__dict__': <attribute '__dict__' of 'C' objects>, '__weakref__': <attribute '__weakref__' of 'C' objects>, '__doc__': None}
    {}
    <class '__main__.C'>
    (<class 'object'>,)
    (<class '__main__.C'>, <class 'object'>)
    [<class '__main__.C'>, <class 'object'>]



```python

```
