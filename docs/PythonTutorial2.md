# Modules

A module is a file containing Python definitions and statements.


```python
from fibo import fib
```

File name fibo.py and function defined is fib 


```python
import fibo
```


```python
fibo.fib()
```


```python
import fibo as fb
```


```python
fb.fib()
```

Introducing \_\_name\_\_ == \_\_main\_\_ makes sure that you are able to run the script as it is. 


```python
!python fibo.py 50
```

    50


Module search path 

* Current directory 
* PYTHONPATH - a list of directory names

* To speed up loading modules , Python caches compiled version of each module in \_\_pycache\_\_ directory under name module.version.pyc . 
* -0 removes assert statements , -00 removes assert and  \_\_doc\_\_ strings. 
* compileall module can create .pyc files for all modules in the directory. 

sys.ps1 and sys.ps2 are primary and secondary prompts. 


```python
import sys
print(sys.ps1)
print(sys.ps2)
```

    In : 
    ...: 



```python
sys.path
```




    ['/home/aditya/Documents/pythonscripts/PythonTutorial',
     '/usr/lib/python37.zip',
     '/usr/lib/python3.7',
     '/usr/lib/python3.7/lib-dynload',
     '',
     '/home/aditya/.local/lib/python3.7/site-packages',
     '/usr/local/lib/python3.7/dist-packages',
     '/usr/lib/python3/dist-packages',
     '/home/aditya/.local/lib/python3.7/site-packages/IPython/extensions',
     '/home/aditya/.ipython']



sys.path has PYTHONPATH. 

dir() returns all names in modules.


```python
dir(fibo)
```




    ['__builtins__',
     '__cached__',
     '__doc__',
     '__file__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     'fib']




```python
import builtins
dir(builtins)
```




    ['ArithmeticError',
     'AssertionError',
     'AttributeError',
     'BaseException',
     'BlockingIOError',
     'BrokenPipeError',
     'BufferError',
     'BytesWarning',
     'ChildProcessError',
     'ConnectionAbortedError',
     'ConnectionError',
     'ConnectionRefusedError',
     'ConnectionResetError',
     'DeprecationWarning',
     'EOFError',
     'Ellipsis',
     'EnvironmentError',
     'Exception',
     'False',
     'FileExistsError',
     'FileNotFoundError',
     'FloatingPointError',
     'FutureWarning',
     'GeneratorExit',
     'IOError',
     'ImportError',
     'ImportWarning',
     'IndentationError',
     'IndexError',
     'InterruptedError',
     'IsADirectoryError',
     'KeyError',
     'KeyboardInterrupt',
     'LookupError',
     'MemoryError',
     'ModuleNotFoundError',
     'NameError',
     'None',
     'NotADirectoryError',
     'NotImplemented',
     'NotImplementedError',
     'OSError',
     'OverflowError',
     'PendingDeprecationWarning',
     'PermissionError',
     'ProcessLookupError',
     'RecursionError',
     'ReferenceError',
     'ResourceWarning',
     'RuntimeError',
     'RuntimeWarning',
     'StopAsyncIteration',
     'StopIteration',
     'SyntaxError',
     'SyntaxWarning',
     'SystemError',
     'SystemExit',
     'TabError',
     'TimeoutError',
     'True',
     'TypeError',
     'UnboundLocalError',
     'UnicodeDecodeError',
     'UnicodeEncodeError',
     'UnicodeError',
     'UnicodeTranslateError',
     'UnicodeWarning',
     'UserWarning',
     'ValueError',
     'Warning',
     'ZeroDivisionError',
     '__IPYTHON__',
     '__build_class__',
     '__debug__',
     '__doc__',
     '__import__',
     '__loader__',
     '__name__',
     '__package__',
     '__spec__',
     'abs',
     'all',
     'any',
     'ascii',
     'bin',
     'bool',
     'breakpoint',
     'bytearray',
     'bytes',
     'callable',
     'chr',
     'classmethod',
     'compile',
     'complex',
     'copyright',
     'credits',
     'delattr',
     'dict',
     'dir',
     'display',
     'divmod',
     'enumerate',
     'eval',
     'exec',
     'filter',
     'float',
     'format',
     'frozenset',
     'get_ipython',
     'getattr',
     'globals',
     'hasattr',
     'hash',
     'help',
     'hex',
     'id',
     'input',
     'int',
     'isinstance',
     'issubclass',
     'iter',
     'len',
     'license',
     'list',
     'locals',
     'map',
     'max',
     'memoryview',
     'min',
     'next',
     'object',
     'oct',
     'open',
     'ord',
     'pow',
     'print',
     'property',
     'range',
     'repr',
     'reversed',
     'round',
     'set',
     'setattr',
     'slice',
     'sorted',
     'staticmethod',
     'str',
     'sum',
     'super',
     'tuple',
     'type',
     'vars',
     'zip']



* Packages are a way of structuring Python's module namespace by using dotted module names. 
* \_\_init\_\_.py converts the directory in which it resides into a package. 


```python
import pkgs
```

when \_\_all\_\_ is defined then import * only those modules which are defined in \_\_all\_\_  in \_\_init\_\_.py 

Use relative imports such as '.' to import specific libraries. 

\_\_path\_\_ contains the number of directory holding the packages \_\_init\_\_.py 


```python

```
