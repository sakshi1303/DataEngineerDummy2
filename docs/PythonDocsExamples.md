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



```
</details>
