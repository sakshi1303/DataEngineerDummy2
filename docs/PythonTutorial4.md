```python
1/0
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    <ipython-input-2-06f355f99298> in <module>
    ----> 1 1/0
          2 '2' + 2


    ZeroDivisionError: division by zero



```python
'2' + 2
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-3-d2b23a1db757> in <module>
    ----> 1 '2' + 2
    

    TypeError: can only concatenate str (not "int") to str



```python
try:
    x=int(input("Please enter a number"))
except ValueError:
    print('Error')
```

    Please enter a number y


    Error



```python
class B(Exception):
    pass
class C(B):
    pass
class D(C):
    pass
```


```python
for cls in [B,C,D]:
    try:
        raise cls()
    except B:
        print('B')
```

    B
    B
    B



```python
for cls in [B,C,D]:
    try:
        raise cls()
    except C:
        print('B')
```


    ---------------------------------------------------------------------------

    B                                         Traceback (most recent call last)

    <ipython-input-11-013ac1f8f7d7> in <module>
          1 for cls in [B,C,D]:
          2     try:
    ----> 3         raise cls()
          4     except C:
          5         print('B')


    B: 



```python
import sys
try:
    aaaaaaaaaaaaaaooooooo
except:
    print('What?')
```

    What?



```python
import sys
try:
    aaaaaaaaaaaaaaooooooo
except ValueError:
    print('What?')
else:
    print('Done')
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-14-73a2ca7a74a5> in <module>
          1 import sys
          2 try:
    ----> 3     aaaaaaaaaaaaaaooooooo
          4 except ValueError:
          5     print('What?')


    NameError: name 'aaaaaaaaaaaaaaooooooo' is not defined



```python
try :
    raise NameError('Hi')
except NameError:
    print('Good')
```

    Good



```python
class Error(Exception):
    pass
class InputError(Error):
    def __init__(self,expression,message):
        self.expression=expression
        self.message=message
```


```python
try:
    raise InputError('a','b')
except InputError:
    print('Hi')
```

    Hi



```python
try:
    raise KeyboardInterrupt
finally:
    print('Hi')
```

    Hi



    ---------------------------------------------------------------------------

    KeyboardInterrupt                         Traceback (most recent call last)

    <ipython-input-18-bd34e13b7d2b> in <module>
          1 try:
    ----> 2     raise KeyboardInterrupt
          3 finally:
          4     print('Hi')


    KeyboardInterrupt: 



```python
try:
    raise KeyboardInterrupt
except :
    print('Hi1')
finally:
    print('Hi 2')
```

    Hi1
    Hi 2


Use with clause for clean up actions. 


```python

```
