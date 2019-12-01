## Classes

Classes provides a means of bundling data and functionality together. 

A namespace is a mapping from names to objects. Examples are set of built-in names , global names in a module etc. 


```python
def do_local():
    spam='local spam'
def do_nonlocal():
    nonlocal spam
    spam='nonlocal spam'
def do_global():
    global spam
    spam='global spam'
spam ='test spam'
print(spam)

```


      File "<ipython-input-1-ad141565a2b8>", line 4
        nonlocal spam
        ^
    SyntaxError: no binding for nonlocal 'spam' found




```python
class Complex:
    def __init__(self,realpart,imagpart):
        self.realpart=realpart
        self.imagpart=imagpart
    def __repr__(self):
        print(f'{str(self.realpart)} + i{str(self.imagpart)}')
x=Complex(5,2)
print(x)
```

    5 + i2



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-6-3314a9044e50> in <module>
          6         print(f'{str(self.realpart)} + i{str(self.imagpart)}')
          7 x=Complex(5,2)
    ----> 8 print(x)
    

    TypeError: __str__ returned non-string (type NoneType)



```python
class Dog:
    kind='canine'
    def __init__(self,name):
        self.name=name
```


```python
a,b=Dog('A'),Dog('B')
print(a.kind , a.name , b.kind , b.name)
```

    canine A canine B



```python
class Warehouse:
    purpose='storage'
    region='west'
    li=[]
w1,w2=Warehouse(),Warehouse()
w1.purpose='store'
w1.li.append('Hi')
print(w2.purpose)
print(w2.li)
```

    storage
    ['Hi']


In case of mutable objects like list, dictionary changing one instance will have effect on another instance as well. Same is not true for string objects.


```python
class PetDog(Dog):
    pass
print(isinstance(PetDog,Dog))
print(issubclass(PetDog,Dog))
```

    False
    True



```python
class GoodDog(PetDog):
    pass
print(issubclass(GoodDog,Dog))
print(GoodDog.kind)
# print(GoodDog.name)
GoodDog.kind='canines'
print(Dog.kind)
print(GoodDog.kind)
```

    True
    canine
    canine
    canines



```python
s='abc'
it=iter(s)
print(next(it))
print(next(it))
print(next(it))
print(next(it))
```

    a
    b
    c



    ---------------------------------------------------------------------------

    StopIteration                             Traceback (most recent call last)

    <ipython-input-28-a4e2d379e6d4> in <module>
          4 print(next(it))
          5 print(next(it))
    ----> 6 print(next(it))
    

    StopIteration: 



```python
class Reverse:
    def __init__(self,data):
        self.data=data
        self.index=len(data)
    def __next__(self):
        if self.index==0:
            raise StopIteration
        self.index = self.index - 1
        return self.data[self.index]
```


```python
x=Reverse('abcd')
print(next(x))
print(next(x))
print(next(x))
```

    d
    c
    b



```python
x=Reverse('abcd')
for i in x:
    print(i)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-32-1d0b2591c750> in <module>
          1 x=Reverse('abcd')
    ----> 2 for i in x:
          3     print(i)


    TypeError: 'Reverse' object is not iterable



```python
def reverse(data):
    for index in range(len(data)):
        yield data[index]
for i in reverse('golf'):
    print(i)
```

    g
    o
    l
    f



```python

```
