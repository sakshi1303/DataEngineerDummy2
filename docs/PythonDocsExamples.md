# Python Examples from Documentation

## Whetting your Appetite

<details>
<summary>Code samples</summary>

```python
```
</details>

## Using the Python Interpreter

<details>
<summary>Code samples</summary>

```python
>>> flat=True
>>> if flat:
...     print('Hi')
... 
Hi

>>> # this is comment
... spam=1
>>> 
```
</details>

## An Informal Introduction to Python

<details>
<summary>Code samples</summary>

```python

>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6)/4
5.0
>>> 8/5
1.6
>>> 17/3
5.666666666666667
>>> 17//3
5
>>> 17%3
2
>>> 5*3+2
17
>>> 5**2
25
>>> 2**7
128
>>> width=20
>>> height=5*9
>>> width*height
900
>>> n
3
>>> x
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'x' is not defined
>>> 4*3.75-1
14.0
>>> tax=12.5/100
>>> price=100.50
>>> price*tax
12.5625
>>> price+_
113.0625
>>> round(_,2)
113.06
>>> 'spam eggs'
'spam eggs'
>>> 'doesn\'t'
"doesn't"
>>> "doesn't"
"doesn't"
>>> '"Yes," they said.'
'"Yes," they said.'
>>> "\"Yes,\" they said."
'"Yes," they said.'
>>> '"Isn\'t, " they said.'
'"Isn\'t, " they said.'
>>> '"Isn\'t," they said.'
'"Isn\'t," they said.'
>>> print('"Isn\'t," they said.')
"Isn't," they said.
>>> s='First line. \nSecond line.'
>>> s
'First line. \nSecond line.'
>>> print(s)
First line. 
Second line.
>>> print('C:\some\name')
C:\some
ame
>>> print(r'C:\some\name')
C:\some\name
>>> print("""\
... Usage: thingy [OPTIONS]
... -h
... -H hostname
... """)
Usage: thingy [OPTIONS]
-h
-H hostname

>>> # 3 times
... 3 * 'un' + 'ium'
'unununium'
>>> 'Py' 'thon'
'Python'
>>> text = ('Put severa' 'l stri' 'ngs')
>>> text
'Put several strings'
>>> prefix='Py'
>>> prefix 'thon'
  File "<stdin>", line 1
    prefix 'thon'
                ^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  File "<stdin>", line 1
    ('un' * 3) 'ium'
                   ^
SyntaxError: invalid syntax
>>> prefix + 'thon'
'Python'
>>> word='Python'
>>> word[0]
'P'
>>> word[5]
'n'
>>> word[-1]
'n'
>>> word[-2]
'o'
>>> word[-6]
'P'
>>> word[0:2]
'Py'
>>> word[2:5]
'tho'
>>> word[:2] + word[2:]
'Python'
>>> word[:2]
'Py'
>>> word[4:]
'on'
>>> word[42]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
>>> word[4:42]
'on'
>>> word[0]
'P'
>>> word[0]='J'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
>>> s='super'
>>> len(s)
5
>>> squares=[1,4,9,16,25]
>>> squares
[1, 4, 9, 16, 25]
>>> squares[0]
1
>>> squares[-1]
25
>>> squares[:]
[1, 4, 9, 16, 25]
>>> squares[:2] + squares[2:]
[1, 4, 9, 16, 25]
>>> cubes=[1,8,27,65,125]
>>> 4**3
64
>>> cubes[3]=64
>>> cubes
[1, 8, 27, 64, 125]
>>> cubes.append(216)
>>> cubes.append(7**3)
>>> cubes
[1, 8, 27, 64, 125, 216, 343]
>>> letters=['a','b','c','d','e','f','g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters[2:5]=['C','D','E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> letters[2:5]
['C', 'D', 'E']
>>> letters[2:5]=[]
>>> letters
['a', 'b', 'f', 'g']
>>> letters[:]=[]
>>> letters
[]

>>> letters=['a','b','c','d']
>>> len(letters)
4
>>> a=['a','b','c']
>>> n=[1,2,3]
>>> x=[a,n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
>>> # Fibonacci series
... a,b = 0,1
>>> while a<10:
...     print(a)
...     a,b = b,a+b
... 
0
1
1
2
3
5
8
>>> i=256*256
>>> print('The value of i is',i)
The value of i is 65536
>>> a,b = 0,1
>>> while a < 1000:
...     print(a,end=',')
...     a,b = b,a+b
... 
0,1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
>>> 

```
</details>

## More Control Flow Tools

<details>
<summary>Code samples</summary>

```python

In [1]: x=int(input("Please enter an integer: "))                               
Please enter an integer: 56

In [2]: if x < 0: 
   ...:     x = 0 
   ...:     print('Negative changed to zero') 
   ...: elif x == 0: 
   ...:     print('Zero') 
   ...: elif x == 1: 
   ...:     print('Single') 
   ...: else: 
   ...:     print('More') 
   ...:                                                                         
More

In [3]: words = ['cat','window','defenestrate']                                 

In [4]: for w in words: 
   ...:     print(w,len(w)) 
   ...:                                                                         
cat 3
window 6
defenestrate 12

In [6]: users = {'a':'active','b':'inactive'}                                   

In [7]: for user, status in users.copy().items(): 
   ...:     if status == 'inactive': 
   ...:         del users[user] 
   ...:                                                                         

In [8]: users                                                                   
Out[8]: {'a': 'active'}

In [8]: users                                                                   
Out[8]: {'a': 'active'}

In [9]: users = {'a':'active','b':'inactive'}                                   

In [10]: active_users={}                                                        

In [11]: for user, status in users.items(): 
    ...:     if status == 'active': 
    ...:         active_users[user] = status 
    ...:                                                                        

In [12]: users                                                                  
Out[12]: {'a': 'active', 'b': 'inactive'}

In [13]: active_users                                                           
Out[13]: {'a': 'active'}

In [14]: for i in range(5): 
    ...:     print(i) 
    ...:                                                                        
0
1
2
3
4

In [15]: range(5,10)                                                            
Out[15]: range(5, 10)

In [17]: a = ['Mary','had','a','little','lamb']                                 

In [18]: for i in range(len(a)): 
    ...:     print(i,a[i]) 
    ...:                                                                        
0 Mary
1 had
2 a
3 little
4 lamb

In [16]: print(range(5,10))                                                     
range(5, 10)

In [19]: sum(range(5,10))                                                       
Out[19]: 35

In [20]: list(range(5,10))                                                      
Out[20]: [5, 6, 7, 8, 9]

In [24]: for n in range(2, 10): 
    ...:     for x in range(2, n): 
    ...:         if n % x == 0: 
    ...:             print(n, 'equals', x, '*', n//x) 
    ...:             break 
    ...:     else: 
    ...:         print(n, 'is a prime number') 
    ...:                                                                        
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3

In [25]: for num in range(2, 10): 
    ...:     if num % 2 == 0: 
    ...:         print("Found an even number", num) 
    ...:         continue 
    ...:     print("Found a number", num) 
    ...:                                                                        
Found an even number 2
Found a number 3
Found an even number 4
Found a number 5
Found an even number 6
Found a number 7
Found an even number 8
Found a number 9

In [1]: while True: 
   ...:     pass 
   ...:                                                                         
^C---------------------------------------------------------------------------
KeyboardInterrupt                         Traceback (most recent call last)
<ipython-input-1-414c137564b4> in <module>
      1 while True:
----> 2     pass
      3 

KeyboardInterrupt: 

In [2]: class MyEmptyClass: 
   ...:     pass 
   ...:                                                                         

In [3]: def initlog(*args): 
   ...:     pass 
   ...:                                                                         

In [4]: def fib(n): 
   ...:     a, b=0,1 
   ...:     while a < n: 
   ...:         print(a, end=' ') 
   ...:         a, b = b, a+b 
   ...:         print() 
   ...:                                                                         

In [5]: fib(2000)                                                               
0 
1 
1 
2 
3 
5 
8 
13 
21 
34 
55 
89 
144 
233 
377 
610 
987 
1597 

In [6]: fib                                                                     
Out[6]: <function __main__.fib(n)>

In [7]: f = fib                                                                 

In [8]: f(100)                                                                  
0 
1 
1 
2 
3 
5 
8 
13 
21 
34 
55 
89 

In [11]: fib(0) ## None is suppressed                                           

In [12]: print(fib(0))                                                          
None

In [13]: def fib2(n): 
    ...:     result = [] 
    ...:     a, b = 0,1 
    ...:     while a < n: 
    ...:         result.append(a) 
    ...:         a, b = b, a+b 
    ...:     return result 
    ...:                                                                        

In [14]: f100=fib2(100)                                                         

In [15]: f100                                                                   
Out[15]: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]

In [16]: def ask_ok(prompt, retries=4, reminder='Please try again'): 
    ...:     while True: 
    ...:         ok=input(prompt) 
    ...:         if ok in ('y','ye', 'yes'): 
    ...:             return True 
    ...:         if ok in ('n', 'no', 'nop', 'nope'): 
    ...:             return False 
    ...:         retries = retries - 1 
    ...:         if retries < 0: 
    ...:             raise ValueError('invalid user response') 
    ...:         print(reminder) 
    ...:                                                                        

In [17]: ask_ok('Do you want to quit')                                          
Do you want to quity
Out[17]: True

In [18]: i = 5                                                                  

In [19]: def f(arg=i): 
    ...:     print(arg) 
    ...:                                                                        

In [20]: i=6                                                                    

In [21]: f()                                                                    
5

In [22]: def f(a, L=[]): 
    ...:     L.append(a) 
    ...:     return L 
    ...:                                                                        

In [23]: print(f(1))                                                            
[1]

In [24]: print(f(2))                                                            
[1, 2]

In [25]: print(f(3))                                                            
[1, 2, 3]

In [26]: def f(a, L=None): 
    ...:     if L is None: 
    ...:         L= [] 
    ...:     L.append(a) 
    ...:     return L 
    ...:                                                                        

In [27]: print(f(1))                                                            
[1]

In [28]: print(f(2))                                                            
[2]

In [29]: print(f(3))                                                            
[3]

In [30]: def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blu
    ...: e'): 
    ...:     print("--This parrot wouldn't", action, end=' ') 
    ...:     print("If you put", voltage, "volts through it.") 
    ...:     print("--Lovely plumage, the",type) 
    ...:     print("--It's",state, "!") 
    ...:    
    
In [31]: parrot(1000)                                                          
--This parrot wouldn't voom If you put 1000 volts through it.
--Lovely plumage, the Norwegian Blue
--It's a stiff !

In [31]: parrot(1000)                                                          
--This parrot wouldn't voom If you put 1000 volts through it.
--Lovely plumage, the Norwegian Blue
--It's a stiff !

In [32]: parrot(voltage=1000)                                                                                          
--This parrot wouldn't voom If you put 1000 volts through it.
--Lovely plumage, the Norwegian Blue
--It's a stiff !

In [33]: parrot(voltage=100000,action='VOOOOOM')                                                                       
--This parrot wouldn't VOOOOOM If you put 100000 volts through it.
--Lovely plumage, the Norwegian Blue
--It's a stiff !

In [34]: parrot('a million','bereft of life', 'jump')                                                                  
--This parrot wouldn't jump If you put a million volts through it.
--Lovely plumage, the Norwegian Blue
--It's bereft of life !

In [35]: parrot('a thousand',state='pushing up the daisies')                                                           
--This parrot wouldn't voom If you put a thousand volts through it.
--Lovely plumage, the Norwegian Blue
--It's pushing up the daisies !

In [2]: parrot()                                                                
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-1fa32faf15ff> in <module>
----> 1 parrot()

TypeError: parrot() missing 1 required positional argument: 'voltage'

In [3]: parrot(voltage=5.0,'dead')                                              
  File "<ipython-input-3-0e2a2e945ec5>", line 1
    parrot(voltage=5.0,'dead')
                      ^
SyntaxError: positional argument follows keyword argument


In [4]: parrot(110, voltage=220)                                                       
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-c1313626062d> in <module>
----> 1 parrot(110, voltage=220)

TypeError: parrot() got multiple values for argument 'voltage'

In [5]: parrot(actor='John Cleese')                                                    
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-5-65e0c6ab2f7f> in <module>
----> 1 parrot(actor='John Cleese')

TypeError: parrot() got an unexpected keyword argument 'actor'


In [6]: def function(a): 
   ...:     pass 
   ...:                                                                                

In [7]: function(0,a=0 
   ...: )                                                                              
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-7-ace1a42cd44e> in <module>
----> 1 function(0,a=0
      2 )

TypeError: function() got multiple values for argument 'a'

In [8]: def cheeseshop(kind, *arguments, **keywords): 
   ...:     print("--Do you have any", kind, "?") 
   ...:     print("-- I'm sorry, we're all out of ", kind) 
   ...:     for arg in arguments: 
   ...:         print(arg) 
   ...:     print("-" * 40) 
   ...:     for kw in keywords: 
   ...:         print(kw, ":", keywords[kw]) 
   ...:                                                                                

In [9]: cheeseshop("Limburger", "It's very runny sir.",shopkeeper="Michael Palin")     
--Do you have any Limburger ?
-- I'm sorry, we're all out of  Limburger
It's very runny sir.
----------------------------------------
shopkeeper : Michael Palin


In [11]: def standard_arg(arg): 
    ...:     print(arg) 
    ...:                                                                               

In [12]: def pos_only_arg(arg, /): 
    ...:     print(arg)                                                                
  File "<ipython-input-12-dac7287a6fee>", line 1
    def pos_only_arg(arg, /):
                          ^
SyntaxError: invalid syntax


In [13]:                                                                               

In [13]: def pos_only_arg(arg, //): 
    ...:     print(arg)                                                                
  File "<ipython-input-13-11cfb5bd9ea4>", line 1
    def pos_only_arg(arg, //):
                           ^
SyntaxError: invalid syntax


In [14]: def kwd_only_arg(*, arg): 
    ...:     print(arg) 
    ...:                                                                               

In [15]: def combined_example(pos_only, /, standard, *, kwd_only): 
    ...:     print(pos_only, standard, kwd_only)                                       
  File "<ipython-input-15-e71a7fd473ab>", line 1
    def combined_example(pos_only, /, standard, *, kwd_only):
                                   ^
SyntaxError: invalid syntax

In [17]: standard_arg(2)                                                               
2

In [18]: standard_arg(arg=2)                                                           
2

In [19]: pos_only_arg(1)                                                               
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-19-bbb555849e09> in <module>
----> 1 pos_only_arg(1)

NameError: name 'pos_only_arg' is not defined

In [20]: kwd_only_arg(1)                                                               
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-20-e6e9a1a2a268> in <module>
----> 1 kwd_only_arg(1)

TypeError: kwd_only_arg() takes 0 positional arguments but 1 was given

In [21]: def foo(name, **kwds): 
    ...:     return 'name' in kwds 
    ...:                                                                               

In [22]: foo(1, **{'name':2})                                                          
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-22-4973700be595> in <module>
----> 1 foo(1, **{'name':2})

TypeError: foo() got multiple values for argument 'name'

In [23]: def foo(name, / , **kwds): 
    ...:     return 'name' in kwds                                                     
  File "<ipython-input-23-c68083edc5e1>", line 1
    def foo(name, / , **kwds):
                  ^
SyntaxError: invalid syntax

In [24]: def write_multiple_items(file, separator, *args): 
    ...:     file.write(separator.join(args)) 
    ...:                                                                               

In [25]: def concat(*args, sep="/"): 
    ...:     return sep.join(args) 
    ...:      
    ...:                                                                               

In [26]: concat("earth","mars", "venus")                                               
Out[26]: 'earth/mars/venus'

In [28]: concat("earth","mars", "venus",sep=",")                                       
Out[28]: 'earth,mars,venus'

In [30]: list(range(7,10))                                                             
Out[30]: [7, 8, 9]

In [31]: args=[3,6]                                                                    

In [32]: list(range(*args))                                                            
Out[32]: [3, 4, 5]

In [33]: def parrot(voltage, state='a stiff', action='voom'): 
    ...:     print(voltage,state,action) 

In [36]: d={"voltage":"1","state":"2","action":"3"}                                    

In [37]: parrot(**d)                                                                   
1 2 3

In [39]: def make_incrementor(n): 
    ...:     return lambda x:x + n  
    ...:                                                                               

In [40]: f = make_incrementor(42)                                                      

In [41]: f(0)                                                                          
Out[41]: 42

In [42]: f(1)                                                                          
Out[42]: 43

In [43]: f(2)                                                                          
Out[43]: 44

In [44]: pairs = [(1,'one'),(2,'two'),(3, 'three')]                                    

In [45]: pairs.sort(key=lambda pair: pair[1])                                          

In [46]: pairs                                                                         
Out[46]: [(1, 'one'), (3, 'three'), (2, 'two')]

In [47]: pairs.sort(key=lambda pair: pair[0])                                          

In [48]: pairs                                                                         
Out[48]: [(1, 'one'), (2, 'two'), (3, 'three')]

In [49]: def my_function(): 
    ...:     """Do nothing, but document it.  
    ...:     No really""" 
    ...:     pass 
    ...:                                                                               

In [50]: print(my_function.__doc__)                                                    
Do nothing, but document it. 
    No really

In [53]: def f (val : str)-> str: 
    ...:     print(f.__annotations__) 
    ...:     return val 
    ...:      
    ...:                                                                               

In [54]: f('spam')                                                                     
{'val': <class 'str'>, 'return': <class 'str'>}
Out[54]: 'spam'


```
</details>

## Data Structures

<details>
<summary>Code Sample</summary>
  
```python
In [1]: fruits=['orange','apple','pear','banana','kiwi','apple','banana']       

In [2]: fruits.count('apple')                                                   
Out[2]: 2

In [3]: fruits.index('banana')                                                  
Out[3]: 3

In [4]: fruits.index('banana',4)                                                
Out[4]: 6

In [5]: fruits.reverse()                                                        

In [6]: fruits                                                                  
Out[6]: ['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']

In [7]: fruits.append('grape')                                                  

In [8]: fruits                                                                  
Out[8]: ['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']

In [9]: fruits.sort()                                                                        

In [10]: fruits                                                                              
Out[10]: ['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']

In [11]: fruits.pop()                                                                        
Out[11]: 'pear'

```

### Using Lists as Stacks

```python
In [13]: stack=[3,4,5]                                                                       

In [14]: stack.append(6)                                                                     

In [15]: stack.append(7)                                                                     

In [16]: stack                                                                               
Out[16]: [3, 4, 5, 6, 7]

In [17]: stack.pop()                                                                         
Out[17]: 7

In [18]: stack.pop()                                                                         
Out[18]: 6

In [19]: stack                                                                               
Out[19]: [3, 4, 5]

```

### Using Lists as Queues

```python
In [21]: from collections import deque                                                       

In [22]: queue = deque(["Eric", "John", "Michael"])                                          

In [23]: queue.append("Terry")                                                               

In [24]: queue.append("Graham")                                                              

In [25]: queue.popleft()                                                                     
Out[25]: 'Eric'

In [26]: queue.popleft()                                                                     
Out[26]: 'John'

In [27]: queue                                                                               
Out[27]: deque(['Michael', 'Terry', 'Graham'])

```

### List Comprehensions

```python
In [29]: squares=[]                                                                          

In [30]: for x in range(10): 
    ...:     squares.append(x**2) 
    ...:                                                                                     

In [31]: squares                                                                             
Out[31]: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

In [32]: squares=[]                                                                          

In [33]: squares=list(map(lambda x:x**2, range(10)))                                         

In [34]: squares = [ x ** 2 for x in range(10)]                                              

In [35]: squares                                                                             
Out[35]: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

In [1]: [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]                                                  
Out[1]: [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]

In [2]: vec = [ -4, -2, 0 , 2 , 4]                                                                            

In [3]: [x*2 for x in vec ]                                                                                   
Out[3]: [-8, -4, 0, 4, 8]

In [4]: [x for x in vec if x >= 0 ]                                                                           
Out[4]: [0, 2, 4]

In [5]: [abs(x) for x in vec]                                                                                 
Out[5]: [4, 2, 0, 2, 4]

In [6]: freshfruit = [ ' banana ', ' loganberry ', ' passion fruit ' ]                                                   

In [7]: [weapon.strip() for weapon in freshfruit ]                                                                       
Out[7]: ['banana', 'loganberry', 'passion fruit']

In [8]: [(x,x**2) for x in range(6)]                                                                                     
Out[8]: [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]

In [9]: vec = [[1,2,3],[4,5,6],[7,8,9]]                                                                                  

In [10]: [num for elem in vec for num in elem]                                                                           
Out[10]: [1, 2, 3, 4, 5, 6, 7, 8, 9]

In [11]: from math import pi                                                                                             

In [12]: [str(round(pi, i)) for i in range(1,6)]                                                                         
Out[12]: ['3.1', '3.14', '3.142', '3.1416', '3.14159']

```
### Nested List Comprehensions

```python

In [14]: matrix = [ 
    ...:     [1,2,3,4], 
    ...:     [5,6,7,8], 
    ...:     [9,10,11,12], 
    ...: ]                                                                                                               

In [15]: matrix                                                                                                          
Out[15]: [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]

In [16]: [[row[i] for row in matrix] for i in range(4)]                                                                  
Out[16]: [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]

In [17]: list(zip(*matrix))                                                                                              
Out[17]: [(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]


```

### The del statement

```python

In [1]: a = [ -1, 1, 66.25, 333, 333 , 1234.5 ]                                                       

In [2]: del a[0]                                                                                      

In [3]: a                                                                                             
Out[3]: [1, 66.25, 333, 333, 1234.5]

In [4]: del a[2:4]                                                                                    

In [5]: a                                                                                             
Out[5]: [1, 66.25, 1234.5]

In [6]: del a[:]                                                                                      

In [7]: a                                                                                             
Out[7]: []

```

</details>

### Tuples and Sequences

<details>
<summary>Answer</summary>

```python

In [9]: t = 12345, 54321, 'hello!'                                                                    

In [10]: t[0]                                                                                         
Out[10]: 12345

In [11]: t                                                                                            
Out[11]: (12345, 54321, 'hello!')

In [12]: # Tuples may be nested                                                                       

In [13]: # Tuples may be nested                                                                       

In [14]: u = t, (1, 2, 3, 4, 5)                                                                       

In [15]: u                                                                                            
Out[15]: ((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))

In [16]: t[0] = 88888                                                                                 
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-16-d739abe3b757> in <module>
----> 1 t[0] = 88888

TypeError: 'tuple' object does not support item assignment

In [17]: v = ([1,2,3], [3,2,1])                                                                       

In [18]: v                                                                                            
Out[18]: ([1, 2, 3], [3, 2, 1])

In [24]: empty=()                                                                                     

In [25]: singleton = 'hello',                                                                         

In [26]: len(empty)                                                                                   
Out[26]: 0

In [27]: len(singleton)                                                                               
Out[27]: 1

In [28]: singleton                                                                                    
Out[28]: ('hello',)

In [29]: x, y, z = t   

```

</details>

### Sets

<details>
<summary>Answer</summary>

```python

In [31]: basket = {'apple','orange','apple','pear','orange','banana'}                                 

In [32]: print(basket)                                                                                
{'apple', 'orange', 'pear', 'banana'}

In [33]: 'orange' in basket                                                                           
Out[33]: True

In [34]: 'crabgrass' in basket                                                                        
Out[34]: False

In [35]: a = set('abracadabra')                                                                       

In [36]: b = set('alacazam')                                                                          

In [37]: a                                                                                            
Out[37]: {'a', 'b', 'c', 'd', 'r'}

In [38]: a - b                                                                                        
Out[38]: {'b', 'd', 'r'}

In [39]: a | b                                                                                        
Out[39]: {'a', 'b', 'c', 'd', 'l', 'm', 'r', 'z'}

In [40]: a & b                                                                                        
Out[40]: {'a', 'c'}

In [41]: a ^ b                                                                                        
Out[41]: {'b', 'd', 'l', 'm', 'r', 'z'}

In [42]: a = {x for x in 'abracadabra' if x not in 'abc'}                                             

In [43]: a                                                                                            
Out[43]: {'d', 'r'}

```

</details>

### Dictionaries

<details>
<summary>Answer</summary>

```python

In [45]: tel = {'jack' : 4098, 'sape':4139}                                                           

In [46]: tel['guido']=4127                                                                            

In [47]: tel                                                                                          
Out[47]: {'jack': 4098, 'sape': 4139, 'guido': 4127}

In [48]: tel['jack']                                                                                  
Out[48]: 4098

In [49]: del tel['sape']                                                                              

In [50]: tel['irv']=4127                                                                              

In [51]: tel                                                                                          
Out[51]: {'jack': 4098, 'guido': 4127, 'irv': 4127}

In [52]: list(tel)                                                                                    
Out[52]: ['jack', 'guido', 'irv']

In [53]: sorted(tel)                                                                                  
Out[53]: ['guido', 'irv', 'jack']

In [54]: 'guido' in tel                                                                               
Out[54]: True

In [55]: 'jack' not in tel                                                                            
Out[55]: False

In [56]: dict([('sape', 4139), ('guido',4127),('jack',4908)])                                         
Out[56]: {'sape': 4139, 'guido': 4127, 'jack': 4908}

In [57]: {x:x**2 for x in (2,4,6)}                                                                    
Out[57]: {2: 4, 4: 16, 6: 36}

In [58]: dict(sape=4139, guido=4127, jack=4098)                                                       
Out[58]: {'sape': 4139, 'guido': 4127, 'jack': 4098}

```
</details>

### Looping Techniques

<details>
<summary>Answer</summary>

```python

In [60]: knights= {'gallahad': 'the pure', 'robin': ' the brave'}                                     

In [61]: for k, v in knights.items(): 
    ...:     print(k, v) 
    ...:                                                                                              
gallahad the pure
robin  the brave

In [62]: for i , v in enumerate(['tic, 'tac', 'toe' ])                                                
  File "<ipython-input-62-67503f558f5e>", line 1
    for i , v in enumerate(['tic, 'tac', 'toe' ])
                                     ^
SyntaxError: invalid syntax


In [63]: for i , v in enumerate(['tic', 'tac', 'toe' ]): 
    ...:     print(i, v) 
    ...:                                                                                              
0 tic
1 tac
2 toe

In [64]: questions = ['name' , 'quest' , 'favorite color']                                            

In [65]: answers = ['lancelot', 'the holy grail' , 'blue']                                            

In [66]: for q, a in zip(questions, answers): 
    ...:     print(q, a) 
    ...:                                                                                              
name lancelot
quest the holy grail
favorite color blue

In [67]: for i in reversed(range(1,10,2)): 
    ...:     print(i) 
    ...:                                                                                              
9
7
5
3
1

In [69]: basket = ['apple' , 'orange', 'apple', 'pear', 'orange' , 'banana']                          

In [70]: for f in sorted(set(basket)): 
    ...:     print(f) 
    ...:                                                                                              
apple
banana
orange
pear

In [71]: import math                                                                                  

In [72]: raw_data = [ 56.2, float('NaN'), 51.7, 55.3, 52.5, float('NaN'), 47.8]                       

In [73]: filtered_data=[]                                                                             

In [74]: for value in raw_data: 
    ...:     if not math.isnan(value): 
    ...:         filtered_data.append(value) 
    ...:                                                                                              

In [75]: filtered_data                                                                                
Out[75]: [56.2, 51.7, 55.3, 52.5, 47.8]


```
  
</details>  

### More on Conditions

<details>
<summary>Answer</summary>

```python

In [76]: string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'                                  

In [77]: non_null = string1 or string2 or string3                                                     

In [78]: non_null                                                                                     
Out[78]: 'Trondheim'

```
</details>

### Comparing Sequences and Other Types

<details>
<summary>Answer</summary>

```python

In [80]: (1,2,3) < (1,2,4)                                                                            
Out[80]: True

In [81]: [1,2,3] < [1,2,4]                                                                            
Out[81]: True

In [82]: 'ABC' < 'C', 'Pascal' < 'Python'                                                             
Out[82]: (True, True)

In [83]: (1, 2, 3, 4) < (1, 2, 4)                                                                     
Out[83]: True

In [84]: (1,2) < (1,1,-1)                                                                             
Out[84]: False

In [85]: (1,2,3) == (1.0,2.0,3.0)                                                                     
Out[85]: True

In [86]: (1,2,('aa','ab')) < (1,2,('abc','a'), 4)                                                     
Out[86]: True


``` 
</details>
 
## Modules

<details>
  <summary>Answer</summary>
  
```python

aditya@aditya-Inspiron-5559:~$ cat fibo.py
def fib(n):
    a, b = 0,1
    while a < n:
        print(a, end=' ')
        a, b = b , a + b
    print()

def fib2(n):
    result = []
    a, b = 0,1
    while a < n:
        result.append(a)
        a, b = b, a+ b
    return result
    
In [1]: import fibo                                                                                  

In [2]: fibo.fib(1000)                                                                               
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 

In [3]: fibo.fib2(100)                                                                               
Out[3]: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]

In [4]: fibo.__name__                                                                                
Out[4]: 'fibo'

In [5]: fib=fibo.fib                                                                                 

In [6]: fib(500)                                                                                     
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 

   
```   
</details>  

### More on Modules

<details>
<summary>Answer</summary>
  
```python

In [7]: from fibo import fib, fib2                                                                   

In [8]: fib(500)                                                                                     
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 

In [9]: from fibo import *                                                                           

In [10]: fib(500)                                                                                    
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 

In [11]: import fibo as fib                                                                          

In [12]: fib.fib(500)                                                                                
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 

In [13]: from fibo import fib as fibonacci                                                           

In [14]: fibonacci(500)                                                                              
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 


```
  
</details>

## Classes 

### Scopes and Namespaces Example

<details>
  <summary>Answer</summary>
  
  ```python
  In [7]: def scope_test():
   ...:     def do_local():
   ...:         spam="local spam"
   ...:     def do_nonlocal():
   ...:         nonlocal spam
   ...:         spam="nonlocal spam"
   ...:     def do_global():
   ...:         global spam
   ...:         spam="global spam"
  File "<ipython-input-7-e091150e6d1b>", line 5
    nonlocal spam
    ^
SyntaxError: no binding for nonlocal 'spam' found
```

</details>
