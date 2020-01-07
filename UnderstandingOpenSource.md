# Understanding Open Source

Start simple
If I can check all high level function because those are mostly used
That is easiest thing check for four hardcoded space. 
Use grep -n '    def' *py to print exact number. 
How to add additional lines in a file at specfic positions. 
Or may be use simple python and use readline.
grep -n '    def' *py
>>> import re
>>> f=open('versioneer.py_no_comments.py','r')
>>> f1=open('abc.py','w')
>>> str1=f.readline()
>>> while str1:
...     f1.write(str1)
...     if re.match('^def',str1):
...             f1.write('print("' + str1 + '")')
...     str1=f.readline()
