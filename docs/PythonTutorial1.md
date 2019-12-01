## Whetting Your Appetite

## collapsible markdown?

<details><summary>CLICK ME</summary>
<p>

#### yes, even hidden code blocks!

```python
print("hello world!")
```

</p>
</details>

## Using the Python Interpreter

* Usually installed in /usr/local/bin/python3.8
* Using Control-D on Unix, Control-Z on Windows exits python interpreter
* Use python -c for command line arguments
* Use python -m for loading module
* Use -i to use interactive mode for scripts
* Script name and additional arguements are passed as list to argv in sys module
* Length of list is atleast one , if no script name is given then it is an empty script
* When - is used as script name then sys.argv[0] has -. Similarly when -c is used then script name in sys.argv[0] is -c. 
* For -m sys.argv[0] contains module name.
* Python source files are treated as encoded in UTF-8.
* To declare any other encoding
```
# -*- coding: encoding -*-
# -*- coding: cp1252 -*-

```


## An informal introduction to Python


```python
print(type(2+2))
print(type(3.0/2))
print(type(3.0//2))
print(type(17%3))
print(type(5 * 3 + 2))
print(2+2)
print(3.0/2)
print(3.0//2)
print(17%3)
print(5 * 3 + 2)
print(3 ** 2)
```

    <class 'int'>
    <class 'float'>
    <class 'float'>
    <class 'int'>
    <class 'int'>
    4
    1.5
    1.0
    2
    17
    9


* // for floor division
* .0 returns float , otherwise int



```python
width=20
```

* = for assigning variable
* In interactive mode, the last printed expression is assigned to the variable _.Only in interactive mode
* String can enclosed in '..' or "..." and \ can be used to escape quotes


```python
print('spam eggs')
print('doesn\'t')
print("doesn't")
s='First Line \n second line'
print(s)
# In interactive mode use print to show characters like \n to show their true value
```

    spam eggs
    doesn't
    doesn't
    First Line 
     second line



```python
s
```




    'First Line \n second line'



* If you dont want characeters prefaces by \ as special charaters use 'r' for raw string
* Use triple quotes for multiline values""" """. 
* End of lines are automatically included in string but its possible to prevent this by adding '\' at end of line. 


```python
print("""\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
```

    Usage: thingy [OPTIONS]
         -h                        Display this usage message
         -H hostname               Hostname to connect to
    



```python
print("""
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
""")
```

    
    Usage: thingy [OPTIONS]
         -h                        Display this usage message
         -H hostname               Hostname to connect to
    


* Strings are concatenated with + and repeated with *


```python
3 * 'un' + 'ium'
```




    'unununium'




```python
text=('Good'
     'Bye')
print(text)
# Strings next to each other are automatically concatenated but works only with literals not variables or expessions
```

    GoodBye



```python
word='Python'
print(word[0]+word[-1])
# Above is called indexing when only one value is returned and slicing means more than one value.
print(word[0:2])
# characters from 0 (included) to 2(excluded)
print(word[0:9])
print(word[:2]+word[2:])
```

    Pn
    Py
    Python
    Python

 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
   0   1   2   3   4   5   6
  -6  -5  -4  -3  -2  -1
* out of range doesnot work in indexing but in slicing it works
* Strings are immutable hence their value cannot be changed.
* len() returns length of a string
* List can contain elements of different types


```python
squares=[1,4,9,16,25]
print(squares[-1])
print(squares[-3:])
```

    25
    [9, 16, 25]


* Lists support concatenation and are immutable.
* Use append to add to the list


```python
squares.append(6*6)
print(squares)
```

    [1, 4, 9, 16, 25, 36, 36]



```python
squares=[1,4,9,16,25]
# Assignmennt to slices is also possible
squares[1:3]=[0,0]
print(squares)
# Assignment can be used for remmoval as well
squares[1:3]=[]
print(squares)
print(len(squares))
```

    [1, 0, 0, 16, 25]
    [1, 16, 25]
    3


* It is possible to nest lists


```python
x=[['a','b'],'1','2']
print(x)
print(x[0][1])
```

    [['a', 'b'], '1', '2']
    b



```python
a,b=0,1
while a < 10:
    print(a)
    a,b=b,a+b
```

    0
    1
    1
    2
    3
    5
    8


## More Control Flow Tools


```python
x=int(input("Please enter an integer"))
if x <0:
    print('Negative')
elif x ==0:
    print('Zero')
else:
    print('More')
```

    Please enter an integer 42


    More


* Python's for statement iterates over items of sequence in which they are stored
* range gives a sequence of numbers
* Object returned by range is not a list but an iterator


```python
words=['Cat','Bat','Rat']
for i in words:
    print(i)
```

    Cat
    Bat
    Rat



```python
print(type(range(5,10)))
print('range1')
for i in range(5,10):
    print(i)
print('range2')
for i in range(5,10,2):
    print(i)
print('range3')
for i in range(1000,100,-100):
    print(i)
```

    <class 'range'>
    range1
    5
    6
    7
    8
    9
    range2
    5
    7
    9
    range3
    1000
    900
    800
    700
    600
    500
    400
    300
    200



```python
a=['Mary','had','little']
for i in range(len(a)):
    print(i,a[i])
print(sum(range(0,6)))
```

    0 Mary
    1 had
    2 little
    15


* Loop statements have an else clause which is executed when loop terminates except when terminated by break statement. 
* When using + int and str are not concatenated so use comma.
* pass does nothing and is used when no action is required


```python
for n in range(2,10):
    for x in range(2,n):# 2 will be excluded
        if n % x ==0 :
            print(n, 'equals',x,'*',n//x)
            break
    else:
        print(n,'is a prime number')
```

    2 is a prime number
    3 is a prime number
    4 equals 2 * 2
    5 is a prime number
    6 equals 2 * 3
    7 is a prime number
    8 equals 2 * 4
    9 equals 3 * 3



```python
class MyEmptyClass:
    pass
```


```python
def fib(n):
    """ Print fibonacci numbers"""
    a,b=0,1
    while a < n:
#         print(a,'-')
        print(a,end=' ')
        a,b=b,a+b
    print()
fib(100)
```

    0 -
    0 1 -
    1 1 -
    1 2 -
    2 3 -
    3 5 -
    5 8 -
    8 13 -
    13 21 -
    21 34 -
    34 55 -
    55 89 -
    89 



```python
def fib(n):
    """ Print fibonacci numbers"""
    a,b=0,1
    while a < n:
        print(a,end=' ')
        a,b=b,a+b
    print()
fib(100)
print(fib.__doc__)
```

    0 1 1 2 3 5 8 13 21 34 55 89 
     Print fibonacci numbers


* First statement string literal can be used for docstring
* All variable assignment in function store value in symbol table . 
* So look up is first in local symbol table then in global symbol table then in built-in names. 
* Functions without a return statement returns None value.


```python
def ask_ok(prompt,retries=6):
    for i in range(retries):
        print(1)
        x=input(prompt)
```


```python
ask_ok('Go')
```

    1


    Go i


    1


    Go i


    1


    Go i


    1


    Go i


    1


    Go i


    1


    Go i


* Function can be called by using kwarg where we specify keyword as aruement and its value. 
* Use * and ** for any number of keywords and arguements.


```python
def parrot(x='X',y='Y'):
    print(x,y)
```


```python
parrot()
parrot(x='A')
parrot(y='A')
```

    X Y
    A Y
    X A



```python
def parrot(*ar,**kw):
    for i in ar:
        print('Args is ' , i)
    for i in kw:
        print('Keyword is ', i , kw[i],kw )
```


```python
parrot('X','Y',x='A',y='B')
parrot(y='A')
```

    Args is  X
    Args is  Y
    Keyword is  x A {'x': 'A', 'y': 'B'}
    Keyword is  y B {'x': 'A', 'y': 'B'}
    Keyword is  y A {'y': 'A'}



```python
def parrot(z,**kw):
#     for i in ar:
#         print('Args is ' , i)
    for i in kw:
        print('Keyword is ', i , kw[i],kw )
    print(z)
parrot(z='Z',x='A',y='B')
parrot(z='Z',y='A')
```

    Keyword is  x A {'x': 'A', 'y': 'B'}
    Keyword is  y B {'x': 'A', 'y': 'B'}
    Z
    Keyword is  y A {'y': 'A'}
    Z


* Positional only arguements are placed before a '/'
* "*" is used for keyword only arguments


```python
def combined_example(pos_only,/,standard, *, kwd_only):
    print(pos_only, standard, kwd_only)
combined_example(1,2,x=8)
```


      File "<ipython-input-9-173ebcb103a6>", line 1
        def combined_example(pos_only,/,standard, *, kwd_only):
                                      ^
    SyntaxError: invalid syntax




```python
def concat(*args,sep='/'):
    print(sep.join(args))
concat('etc','pwd','file')
concat('etc','pwd','file',sep='.')
```

    etc/pwd/file
    etc.pwd.file



```python
print(list(range(3,6)))
args=[3,6]
print(list(range(*args)))
```

    [3, 4, 5]
    [3, 4, 5]


Lambda functions can be used whenever function objects are used


```python
def make_incrementor(n):
    return lambda x:x+n
f=make_incrementor(42)
print(f(0))
print(f(1))
print(f(0))
```

    42
    43
    42



```python
pairs=[(1,'one'),(2,'two'),(3,'three')]
pairs.sort(key=lambda pair:pair[0])
print(pairs)
pairs.sort(key=lambda pair:pair[1])
print(pairs)
```

    [(1, 'one'), (2, 'two'), (3, 'three')]
    [(1, 'one'), (3, 'three'), (2, 'two')]


Docstring can be included by using """ test""" in the function


```python
def sample_func():
    """Doc1
Doc2"""
    pass
    """ Test1"""
print(sample_func.__doc__)
```

    Doc1
    Doc2


Function annotations are completely optional metadata information about the types used by user-defined functions 


```python
def sample_func(ham:str,egg:str='eggs') -> str:
    return ham + egg
print(sample_func.__annotations__)
print(sample_func('ham'))
```

    {'ham': <class 'str'>, 'egg': <class 'str'>, 'return': <class 'str'>}
    hameggs


## PEP 8 coding style

* 4 space indentation
* no line more than 79 characters
* Use blank lines to separate functions and classes
* Use docstrings
* Use spaces around brackets and commas
* UpperCamelCase for classes and lowercase_with_underscores for functions

## Data Structures

* list.append(x) For appending an item to the list
* list.extend(iterable) Appending all the items from iterable
* list.index(i,x) Insert x at ith position
* list.remove(x) Remove first occurrence of x .
* list.pop(i) Remove element from ith position . If no argument is given then return last item
* list.clear() Remove all items from the list. Equivalent to del l[:]
* list.index(x,[start,end]) return position of an item. Start and end for limiting the search
* list.count(x) Number of times x has appeared
* list.sort(key=None,reverse=False)
* list.reverse() Reverse elements of the list
* list.copy() Return shallow copy of the list. Equivalent to a[:]


```python
fruits=['apple','orange','banana','kiwi','pear','apple','banana','apple']
fruits.append('grapes')
print(fruits.count('apple'))
print(fruits.index('banana'))
print(fruits.index('banana',4))
print(fruits.reverse())
print(fruits)
print(fruits.sort(reverse=False))
print(fruits)
print(fruits.pop())
print(fruits)
```

    3
    2
    6
    None
    ['grapes', 'apple', 'banana', 'apple', 'pear', 'kiwi', 'banana', 'orange', 'apple']
    None
    ['apple', 'apple', 'apple', 'banana', 'banana', 'grapes', 'kiwi', 'orange', 'pear']
    pear
    ['apple', 'apple', 'apple', 'banana', 'banana', 'grapes', 'kiwi', 'orange']


### Using Lists as stacks


```python
stack=[3,4,5]
stack.append(6)
print(stack)
stack.pop()
print(stack)
```

    [3, 4, 5, 6]
    [3, 4, 5]


### Using Lists as queues

It is possible to use List as queues but it is very efficient


```python
from collections import deque
queue=deque([1,2,3])
print(queue)
queue.append(4)
print(queue)
queue.popleft()
print(queue)
```

    deque([1, 2, 3])
    deque([1, 2, 3, 4])
    deque([2, 3, 4])



```python
squares=[]
for x in range(10):
    squares.append(x**2)
print(squares)
squares=list(map(lambda x:x**2,range(10)))
print(squares)
squares=[x**2 for x in range(10)]
print(squares)
```

    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]



```python
[(x,y) for x in [1,2,3] for y in [3,4,5]]
```




    [(1, 3), (1, 4), (1, 5), (2, 3), (2, 4), (2, 5), (3, 3), (3, 4), (3, 5)]




```python
vec=[[1,2,3],[4,5,6]]
li=[j for i in vec for j in i]
print(li)
li=[[ row[i] for row in vec] for i in range(3)]
print(li)
print(list(zip(*vec)))
```

    [1, 2, 3, 4, 5, 6]
    [[1, 4], [2, 5], [3, 6]]
    [(1, 4), (2, 5), (3, 6)]



```python
a=[0,1,2,3,4]
del a[0:2]
print(a)
```

    [2, 3, 4]


#### Tuples are immutable


```python
t=1,2,3
print(t[0])
t[0]=-1
```

    1



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-66-b39759913992> in <module>
          1 t=1,2,3
          2 print(t[0])
    ----> 3 t[0]=-1
    

    TypeError: 'tuple' object does not support item assignment


#### Trailing commas convert them into tuple. 


```python
x,y,z=(1,2,3)
print(y)
```

    2


##### A set is an unordered collection with no duplicate elements. 


```python
basket={'apple','orange','banana','apple'}
print(basket)
print('apple' in basket)
print('apples' in basket)
a=set('abcdeabcde')
b=set('cdefgcdefg')
print(a)
print(b)
print(a-b)
print(a&b)
print(a|b)
print(a^b)
```

    {'banana', 'apple', 'orange'}
    True
    False
    {'c', 'a', 'e', 'b', 'd'}
    {'c', 'g', 'e', 'f', 'd'}
    {'b', 'a'}
    {'e', 'c', 'd'}
    {'c', 'g', 'a', 'e', 'f', 'b', 'd'}
    {'f', 'b', 'g', 'a'}



```python
tel={'b':'B','c':'C'}
tel['a']='A'
print(tel)
print(sorted(tel))
print(list(tel))
print('a' in tel)
print('A' in tel)
for i,j in tel.items():
    print(i,j)
```

    {'b': 'B', 'c': 'C', 'a': 'A'}
    ['a', 'b', 'c']
    ['b', 'c', 'a']
    True
    False
    b B
    c C
    a A



```python
for i,v in enumerate(['a','b','c']):
    print(i,v)
```

    0 a
    1 b
    2 c



```python
li1=[1,2,3]
li2=[4,5,6]
for i,j in zip(li1,li2):
    print(i,j)
```

    1 4
    2 5
    3 6



```python
for i in reversed(range(1,10,2)):
    print(i)
```

    9
    7
    5
    3
    1



```python
str1,str2,str3='','a','b'
non_null=str1 or str2 or str3
print(non_null)
str1,str2,str3='a','b','c'
non_null=str1 or str2 or str3
print(non_null)
```

    a
    a



```python
print((1,2,3) < (1,2,4))
print([1,2,3] > [1,2,4])
print((1, 2)  < (1, 2, -1))
print((1, 2, 3) == (1.0, 2.0, 3.0))
print((1, 2, ('aa', 'ab')) < (1, 2, ('abc', 'a'), 4))
```

    True
    False
    True
    True
    True



```python

```
