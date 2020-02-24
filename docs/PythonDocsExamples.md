# Python Examples from Documentation

## Whetting your Appetite

```python
```

## Using the Python Interpreter

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

## An Informal Introduction to Python

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
0,1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,>>> 


```
