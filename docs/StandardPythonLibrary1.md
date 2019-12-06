Absolute value of integers


```python
abs(-3.02)
```




    3.02



If all elements are not nulls. 


```python
print(all([1,'',56,78]))
print(all([1,'3',56,78]))
```

    False
    True


if any of the elements are non nuls. 


```python
print(any([1,'',56,78]))
print(any(['','']))
```

    True
    False



```python
ascii('a\\u')
ascii("µ")
```




    "'\\xb5'"




```python
print(bin(3),bin(4))
```

    0b11 0b100



```python
print(bool(''),bool(1))
```

    False True


Breakpoint needs analysis


```python
breakpoint('x'='a')
```


      File "<ipython-input-25-bb0acfb6139f>", line 1
        breakpoint('x'='a')
                  ^
    SyntaxError: keyword can't be an expression




```python
bytearray(list(range(10)))
```




    bytearray(b'\x00\x01\x02\x03\x04\x05\x06\x07\x08\t')




```python
bytes(list(range(4)))
```




    b'\x00\x01\x02\x03'




```python
print(callable(str),callable('x'))
```

    True False



```python
print(chr(122))
```

    z


@classmethod requires more attention


```python
compile('print (\'Hello World\')','<string>',mode='exec')
```




    <code object <module> at 0x7f70e817b390, file "<string>", line 1>




```python
complex(1,6)
```




    (1+6j)




```python
class A:
    def met(self):
        pass
del A.met
```


```python
dict({'A':'a'})
```




    {'A': 'a'}




```python
dir(dict)
```




    ['__class__',
     '__contains__',
     '__delattr__',
     '__delitem__',
     '__dir__',
     '__doc__',
     '__eq__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getitem__',
     '__gt__',
     '__hash__',
     '__init__',
     '__init_subclass__',
     '__iter__',
     '__le__',
     '__len__',
     '__lt__',
     '__ne__',
     '__new__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__setattr__',
     '__setitem__',
     '__sizeof__',
     '__str__',
     '__subclasshook__',
     'clear',
     'copy',
     'fromkeys',
     'get',
     'items',
     'keys',
     'pop',
     'popitem',
     'setdefault',
     'update',
     'values']




```python
divmod(45,7)
```




    (6, 3)




```python
list(enumerate(['a','b','c','d']))
```




    [(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd')]




```python
eval("print ('Hello World')")
```

    Hello World



```python
exec("print ('Hello World');print ('Hello World')")
```

    Hello World
    Hello World



```python
def func(var):
    if var==1:
        return True
    else:
        return False
print(list(filter(None,[1,2,3])))
print(list(filter(func,[1,2,3])))
```

    [1, 2, 3]
    [1]



```python
float(1e06)
```




    1000000.0




```python
str1='{subject} runs.'
print(str1.format(subject='Ram'))
```

    Ram runs.



```python
a=frozenset([1,1,6,8])
print(a)
```

    frozenset({8, 1, 6})



```python
a[0]=9
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-64-cba6ae86e37f> in <module>
    ----> 1 a[0]=9
    

    TypeError: 'frozenset' object does not support item assignment



```python
class A:
    def __init__(self,value):
        self.value=value
a=A('a')
```


```python
print(a.value)
print(getattr(a,'value'))
print(hasattr(a,'value'))
print(hasattr(a,'values'))
```

    a
    a
    True
    False



```python
globals()['__name__']
```




    '__main__'



globals returns a dictionary of all values in symbol table. 


```python
hash(a)
```




    8757681661313




```python
help(int)
```

    Help on class int in module builtins:
    
    class int(object)
     |  int([x]) -> integer
     |  int(x, base=10) -> integer
     |  
     |  Convert a number or string to an integer, or return 0 if no arguments
     |  are given.  If x is a number, return x.__int__().  For floating point
     |  numbers, this truncates towards zero.
     |  
     |  If x is not a number or if base is given, then x must be a string,
     |  bytes, or bytearray instance representing an integer literal in the
     |  given base.  The literal can be preceded by '+' or '-' and be surrounded
     |  by whitespace.  The base defaults to 10.  Valid bases are 0 and 2-36.
     |  Base 0 means to interpret the base from the string as an integer literal.
     |  >>> int('0b100', base=0)
     |  4
     |  
     |  Methods defined here:
     |  
     |  __abs__(self, /)
     |      abs(self)
     |  
     |  __add__(self, value, /)
     |      Return self+value.
     |  
     |  __and__(self, value, /)
     |      Return self&value.
     |  
     |  __bool__(self, /)
     |      self != 0
     |  
     |  __ceil__(...)
     |      Ceiling of an Integral returns itself.
     |  
     |  __divmod__(self, value, /)
     |      Return divmod(self, value).
     |  
     |  __eq__(self, value, /)
     |      Return self==value.
     |  
     |  __float__(self, /)
     |      float(self)
     |  
     |  __floor__(...)
     |      Flooring an Integral returns itself.
     |  
     |  __floordiv__(self, value, /)
     |      Return self//value.
     |  
     |  __format__(self, format_spec, /)
     |      Default object formatter.
     |  
     |  __ge__(self, value, /)
     |      Return self>=value.
     |  
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |  
     |  __getnewargs__(self, /)
     |  
     |  __gt__(self, value, /)
     |      Return self>value.
     |  
     |  __hash__(self, /)
     |      Return hash(self).
     |  
     |  __index__(self, /)
     |      Return self converted to an integer, if self is suitable for use as an index into a list.
     |  
     |  __int__(self, /)
     |      int(self)
     |  
     |  __invert__(self, /)
     |      ~self
     |  
     |  __le__(self, value, /)
     |      Return self<=value.
     |  
     |  __lshift__(self, value, /)
     |      Return self<<value.
     |  
     |  __lt__(self, value, /)
     |      Return self<value.
     |  
     |  __mod__(self, value, /)
     |      Return self%value.
     |  
     |  __mul__(self, value, /)
     |      Return self*value.
     |  
     |  __ne__(self, value, /)
     |      Return self!=value.
     |  
     |  __neg__(self, /)
     |      -self
     |  
     |  __or__(self, value, /)
     |      Return self|value.
     |  
     |  __pos__(self, /)
     |      +self
     |  
     |  __pow__(self, value, mod=None, /)
     |      Return pow(self, value, mod).
     |  
     |  __radd__(self, value, /)
     |      Return value+self.
     |  
     |  __rand__(self, value, /)
     |      Return value&self.
     |  
     |  __rdivmod__(self, value, /)
     |      Return divmod(value, self).
     |  
     |  __repr__(self, /)
     |      Return repr(self).
     |  
     |  __rfloordiv__(self, value, /)
     |      Return value//self.
     |  
     |  __rlshift__(self, value, /)
     |      Return value<<self.
     |  
     |  __rmod__(self, value, /)
     |      Return value%self.
     |  
     |  __rmul__(self, value, /)
     |      Return value*self.
     |  
     |  __ror__(self, value, /)
     |      Return value|self.
     |  
     |  __round__(...)
     |      Rounding an Integral returns itself.
     |      Rounding with an ndigits argument also returns an integer.
     |  
     |  __rpow__(self, value, mod=None, /)
     |      Return pow(value, self, mod).
     |  
     |  __rrshift__(self, value, /)
     |      Return value>>self.
     |  
     |  __rshift__(self, value, /)
     |      Return self>>value.
     |  
     |  __rsub__(self, value, /)
     |      Return value-self.
     |  
     |  __rtruediv__(self, value, /)
     |      Return value/self.
     |  
     |  __rxor__(self, value, /)
     |      Return value^self.
     |  
     |  __sizeof__(self, /)
     |      Returns size in memory, in bytes.
     |  
     |  __str__(self, /)
     |      Return str(self).
     |  
     |  __sub__(self, value, /)
     |      Return self-value.
     |  
     |  __truediv__(self, value, /)
     |      Return self/value.
     |  
     |  __trunc__(...)
     |      Truncating an Integral returns itself.
     |  
     |  __xor__(self, value, /)
     |      Return self^value.
     |  
     |  bit_length(self, /)
     |      Number of bits necessary to represent self in binary.
     |      
     |      >>> bin(37)
     |      '0b100101'
     |      >>> (37).bit_length()
     |      6
     |  
     |  conjugate(...)
     |      Returns self, the complex conjugate of any int.
     |  
     |  to_bytes(self, /, length, byteorder, *, signed=False)
     |      Return an array of bytes representing an integer.
     |      
     |      length
     |        Length of bytes object to use.  An OverflowError is raised if the
     |        integer is not representable with the given number of bytes.
     |      byteorder
     |        The byte order used to represent the integer.  If byteorder is 'big',
     |        the most significant byte is at the beginning of the byte array.  If
     |        byteorder is 'little', the most significant byte is at the end of the
     |        byte array.  To request the native byte order of the host system, use
     |        `sys.byteorder' as the byte order value.
     |      signed
     |        Determines whether two's complement is used to represent the integer.
     |        If signed is False and a negative integer is given, an OverflowError
     |        is raised.
     |  
     |  ----------------------------------------------------------------------
     |  Class methods defined here:
     |  
     |  from_bytes(bytes, byteorder, *, signed=False) from builtins.type
     |      Return the integer represented by the given array of bytes.
     |      
     |      bytes
     |        Holds the array of bytes to convert.  The argument must either
     |        support the buffer protocol or be an iterable object producing bytes.
     |        Bytes and bytearray are examples of built-in objects that support the
     |        buffer protocol.
     |      byteorder
     |        The byte order used to represent the integer.  If byteorder is 'big',
     |        the most significant byte is at the beginning of the byte array.  If
     |        byteorder is 'little', the most significant byte is at the end of the
     |        byte array.  To request the native byte order of the host system, use
     |        `sys.byteorder' as the byte order value.
     |      signed
     |        Indicates whether two's complement is used to represent the integer.
     |  
     |  ----------------------------------------------------------------------
     |  Static methods defined here:
     |  
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |  
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |  
     |  denominator
     |      the denominator of a rational number in lowest terms
     |  
     |  imag
     |      the imaginary part of a complex number
     |  
     |  numerator
     |      the numerator of a rational number in lowest terms
     |  
     |  real
     |      the real part of a complex number
    



```python
hex(23)
```




    '0x17'




```python
x='A'
id(x)
```




    140123012335344




```python
s=input('Hi')
```

    Hi Wow



```python
s
```




    'Wow'




```python
int(9.2)
```




    9




```python
x=str('A')
```


```python
print(isinstance(x,str))
```

    True



```python
import threading
class SubClass(threading.Thread):
    pass
subclass=SubClass()
issubclass(SubClass,threading.Thread)
```




    True




```python
s=iter((1,2,3))
print(s.__next__())
```

    1



```python
print(len((1,2,3)))
```

    3



```python
list([1,2,3])
```




    [1, 2, 3]




```python
locals()
```




    {'__name__': '__main__',
     '__doc__': 'Automatically created module for IPython interactive environment',
     '__package__': None,
     '__loader__': None,
     '__spec__': None,
     '__builtin__': <module 'builtins' (built-in)>,
     '__builtins__': <module 'builtins' (built-in)>,
     '_ih': ['', 'locals()'],
     '_oh': {},
     '_dh': ['/home/aditya/Documents/pythonscripts/PythonTutorial'],
     'In': ['', 'locals()'],
     'Out': {},
     'get_ipython': <bound method InteractiveShell.get_ipython of <ipykernel.zmqshell.ZMQInteractiveShell object at 0x7f340c17e250>>,
     'exit': <IPython.core.autocall.ZMQExitAutocall at 0x7f340c19a890>,
     'quit': <IPython.core.autocall.ZMQExitAutocall at 0x7f340c19a890>,
     '_': '',
     '__': '',
     '___': '',
     '_i': '',
     '_ii': '',
     '_iii': '',
     '_i1': 'locals()'}




```python
def func(x):
    return x+1
x=map(func,iter([1,2,3]))
```


```python
x.__next__()
```




    3




```python
x,y,z=8,9,40
max(x,y,z)
```




    40




```python
A=str()
memoryview(A)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-12-e19e8ae8b10f> in <module>
          1 A=str()
    ----> 2 memoryview(A)
    

    TypeError: memoryview: a bytes-like object is required, not 'str'



```python
min(x,y,z)
```




    8




```python
next(iter([7,6,8]))
```




    7




```python
A=object()
print(A.__repr__)
```

    <method-wrapper '__repr__' of object object at 0x7f340c180260>



```python
print(oct(9),oct(8),oct(10))
```

    0o11 0o10 0o12



```python
f=open('sample.txt','w')
f.write('Hello')
f.close()
```


```python
print(ord('A'),ord('B'),ord(' '))
```

    65 66 32



```python
print(pow(8,2))
print(pow(5,2,3))
```

    64
    1



```python
class A:
    def __init__(self):
        self._value=100
    def x(self):
        return self._value
a=A()
print(a.x)
class A:
    def __init__(self):
        self._value=100
    @property
    def x(self):
        return self._value
a=A()
print(a.x)
```

    <bound method A.x of <__main__.A object at 0x7f33f3f46410>>
    100



```python
print(list(range(6)))
print(list(range(6,10)))
print(list(range(6,10,-2)))
print(list(range(16,10,-2)))
```

    [0, 1, 2, 3, 4, 5]
    [6, 7, 8, 9]
    []
    [16, 14, 12]



```python
class A:
    def __init__(self):
        self.value=10
    def __repr__(self):
        return 'Value is ' + str(self.value)
print(str(A))
a=A()
print(str(a))
```

    <class '__main__.A'>
    Value is 10



```python
list(reversed([7,8,9]))
```




    [9, 8, 7]




```python
round(7.066,1)
```




    7.1




```python
set([1,5,9,9,10])
```




    {1, 5, 9, 10}




```python
class A:
    def __init__(self):
        self.value=0
a=A()
setattr(a,'value',10)
print(a.value)
```

    10



```python
slice(67,98,8)
```




    slice(67, 98, 8)




```python
sorted([98,56,100])
```




    [56, 98, 100]




```python
class A:
    @staticmethod
    def f(self,value):
        return value
```


```python
sum((1,8,6))
```




    15




```python
super(str)
```




    <super: str, None>




```python
x=tuple((1,2,7))
print(x[0])
x[0]=6
```

    1



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-68-4af10af5b143> in <module>
          1 x=tuple((1,2,7))
          2 print(x[0])
    ----> 3 x[0]=6
    

    TypeError: 'tuple' object does not support item assignment



```python
type(x)
```




    tuple




```python
vars(A)
```




    mappingproxy({'__module__': '__main__',
                  'f': <staticmethod at 0x7f33f3fcb450>,
                  '__dict__': <attribute '__dict__' of 'A' objects>,
                  '__weakref__': <attribute '__weakref__' of 'A' objects>,
                  '__doc__': None})




```python
x=[1,8,0]
y=[8,65,90,87]
list(zip(x,y))
```




    [(1, 8), (8, 65), (0, 90)]




```python
oses=__import__('os')
```


```python

```
