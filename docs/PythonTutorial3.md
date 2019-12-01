## Input and Output Formatting

Use f'' to print values with variables enclosed in {}. 


```python
year=2016
print (f'This is year {year}')
```

    This is year 2016


.format to print string with variables. 


```python
votes=10
print('vote {:2.2%}'.format(votes))
print('vote {:2%}'.format(votes))
print('vote {:1}'.format(votes))
```

    vote 1000.00%
    vote 1000.000000%
    vote 10


Difference between str() and repr attribute.


```python
s='Hello \n World'
print(str(s))
print(repr(s))
di={'Foo':1,'Bar':2}
print(str(di))
print(repr(di))
```

    Hello 
     World
    'Hello \n World'
    {'Foo': 1, 'Bar': 2}
    {'Foo': 1, 'Bar': 2}


Formatted string liberals also is used to evalute expressions such as 


```python
import math
print(f'Value of pi is {math.pi:.4}')
print(f'Add 2 + 3 = {2 +3}')
string='Hello \n World'
print(f'{string}')
print(f'{string!r}')
```

    Value of pi is 3.142
    Add 2 + 3 = 5
    Hello 
     World
    'Hello \n World'


* Passing an integer after colon ':' decides the width of the character. 


```python
print('{} {}'.format('Hello','World'))
print('{0} {1}'.format('Hello','World'))
print('{1} {0}'.format('Hello','World'))
print('{hello} {world}'.format(hello='Hello',world='World'))
```

    Hello World
    Hello World
    World Hello
    Hello World


zfill works as padding for numbers


```python
'12'.zfill(5)
```




    '00012'




```python
f=open('pkgs/samples.py')
val=f.read()
print(val)
f=open('pkgs/samples.py')
val=f.readline()
print(val)
f=open('pkgs/samples.py')
for line in f:
    print(line)
```

    def sample_func():
        pass
    def sample_func():
    
    def sample_func():
    
        pass


Use f.write to write on string.


```python
f=open('pkgs/samples.py','a')
f.write('# This is life.')
f=open('pkgs/samples.py')
print(f.read())
```

    def sample_func():
        pass# This is life.# This is life.


f.seek() is used to move the cursor.


```python
f=open('pkgs/samples.py')
print(f.read())
f=open('pkgs/samples.py')
f.seek(3)
print(f.read())
f=open('pkgs/samples.py')
f.seek(3,2)
print(f.read())
```

    def sample_func():
        pass# This is life.# This is life.
     sample_func():
        pass# This is life.# This is life.



    ---------------------------------------------------------------------------

    UnsupportedOperation                      Traceback (most recent call last)

    <ipython-input-43-3b7b515f3bb2> in <module>
          5 print(f.read())
          6 f=open('pkgs/samples.py')
    ----> 7 f.seek(3,2)
          8 print(f.read())


    UnsupportedOperation: can't do nonzero end-relative seeks


* json module can convert complex Python data hierarchies into string representation which is called serialization. 
* Reconstructing the data from string representation is called deserializing. 


```python
class SampleClass:
    def __init__(self,a,b):
        self.a=a
        self.b=b
    def __repr__():
        print(a,b)
sampleClass=SampleClass(a='A',b='B')
```


```python
import json
json.dumps(sampleClass)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-52-b5956cb61f51> in <module>
          1 import json
    ----> 2 json.dumps(sampleClass)
    

    /usr/lib/python3.7/json/__init__.py in dumps(obj, skipkeys, ensure_ascii, check_circular, allow_nan, cls, indent, separators, default, sort_keys, **kw)
        229         cls is None and indent is None and separators is None and
        230         default is None and not sort_keys and not kw):
    --> 231         return _default_encoder.encode(obj)
        232     if cls is None:
        233         cls = JSONEncoder


    /usr/lib/python3.7/json/encoder.py in encode(self, o)
        197         # exceptions aren't as detailed.  The list call should be roughly
        198         # equivalent to the PySequence_Fast that ''.join() would do.
    --> 199         chunks = self.iterencode(o, _one_shot=True)
        200         if not isinstance(chunks, (list, tuple)):
        201             chunks = list(chunks)


    /usr/lib/python3.7/json/encoder.py in iterencode(self, o, _one_shot)
        255                 self.key_separator, self.item_separator, self.sort_keys,
        256                 self.skipkeys, _one_shot)
    --> 257         return _iterencode(o, 0)
        258 
        259 def _make_iterencode(markers, _default, _encoder, _indent, _floatstr,


    /usr/lib/python3.7/json/encoder.py in default(self, o)
        177 
        178         """
    --> 179         raise TypeError(f'Object of type {o.__class__.__name__} '
        180                         f'is not JSON serializable')
        181 


    TypeError: Object of type SampleClass is not JSON serializable


Difference between dump and dumps is that dump requires a file name. 


```python
json.load(open('pkgs/samples.py'))
```


    ---------------------------------------------------------------------------

    JSONDecodeError                           Traceback (most recent call last)

    <ipython-input-54-82bcf1ddc987> in <module>
    ----> 1 json.load(open('pkgs/samples.py'))
    

    /usr/lib/python3.7/json/__init__.py in load(fp, cls, object_hook, parse_float, parse_int, parse_constant, object_pairs_hook, **kw)
        294         cls=cls, object_hook=object_hook,
        295         parse_float=parse_float, parse_int=parse_int,
    --> 296         parse_constant=parse_constant, object_pairs_hook=object_pairs_hook, **kw)
        297 
        298 


    /usr/lib/python3.7/json/__init__.py in loads(s, encoding, cls, object_hook, parse_float, parse_int, parse_constant, object_pairs_hook, **kw)
        346             parse_int is None and parse_float is None and
        347             parse_constant is None and object_pairs_hook is None and not kw):
    --> 348         return _default_decoder.decode(s)
        349     if cls is None:
        350         cls = JSONDecoder


    /usr/lib/python3.7/json/decoder.py in decode(self, s, _w)
        335 
        336         """
    --> 337         obj, end = self.raw_decode(s, idx=_w(s, 0).end())
        338         end = _w(s, end).end()
        339         if end != len(s):


    /usr/lib/python3.7/json/decoder.py in raw_decode(self, s, idx)
        353             obj, end = self.scan_once(s, idx)
        354         except StopIteration as err:
    --> 355             raise JSONDecodeError("Expecting value", s, err.value) from None
        356         return obj, end


    JSONDecodeError: Expecting value: line 1 column 1 (char 0)



```python

```
