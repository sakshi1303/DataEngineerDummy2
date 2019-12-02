```python
import os 
print(os.getcwd())
print(os.chdir('/home/aditya/Documents/pythonscripts/PythonTutorial'))
os.system('ls')
print(dir(os))
```

    /home/aditya/Documents/pythonscripts/PythonTutorial
    None
    ['CLD_CONTINUED', 'CLD_DUMPED', 'CLD_EXITED', 'CLD_TRAPPED', 'DirEntry', 'EX_CANTCREAT', 'EX_CONFIG', 'EX_DATAERR', 'EX_IOERR', 'EX_NOHOST', 'EX_NOINPUT', 'EX_NOPERM', 'EX_NOUSER', 'EX_OK', 'EX_OSERR', 'EX_OSFILE', 'EX_PROTOCOL', 'EX_SOFTWARE', 'EX_TEMPFAIL', 'EX_UNAVAILABLE', 'EX_USAGE', 'F_LOCK', 'F_OK', 'F_TEST', 'F_TLOCK', 'F_ULOCK', 'GRND_NONBLOCK', 'GRND_RANDOM', 'MutableMapping', 'NGROUPS_MAX', 'O_ACCMODE', 'O_APPEND', 'O_ASYNC', 'O_CLOEXEC', 'O_CREAT', 'O_DIRECT', 'O_DIRECTORY', 'O_DSYNC', 'O_EXCL', 'O_LARGEFILE', 'O_NDELAY', 'O_NOATIME', 'O_NOCTTY', 'O_NOFOLLOW', 'O_NONBLOCK', 'O_PATH', 'O_RDONLY', 'O_RDWR', 'O_RSYNC', 'O_SYNC', 'O_TMPFILE', 'O_TRUNC', 'O_WRONLY', 'POSIX_FADV_DONTNEED', 'POSIX_FADV_NOREUSE', 'POSIX_FADV_NORMAL', 'POSIX_FADV_RANDOM', 'POSIX_FADV_SEQUENTIAL', 'POSIX_FADV_WILLNEED', 'PRIO_PGRP', 'PRIO_PROCESS', 'PRIO_USER', 'P_ALL', 'P_NOWAIT', 'P_NOWAITO', 'P_PGID', 'P_PID', 'P_WAIT', 'PathLike', 'RTLD_DEEPBIND', 'RTLD_GLOBAL', 'RTLD_LAZY', 'RTLD_LOCAL', 'RTLD_NODELETE', 'RTLD_NOLOAD', 'RTLD_NOW', 'RWF_DSYNC', 'RWF_HIPRI', 'RWF_NOWAIT', 'RWF_SYNC', 'R_OK', 'SCHED_BATCH', 'SCHED_FIFO', 'SCHED_IDLE', 'SCHED_OTHER', 'SCHED_RESET_ON_FORK', 'SCHED_RR', 'SEEK_CUR', 'SEEK_DATA', 'SEEK_END', 'SEEK_HOLE', 'SEEK_SET', 'ST_APPEND', 'ST_MANDLOCK', 'ST_NOATIME', 'ST_NODEV', 'ST_NODIRATIME', 'ST_NOEXEC', 'ST_NOSUID', 'ST_RDONLY', 'ST_RELATIME', 'ST_SYNCHRONOUS', 'ST_WRITE', 'TMP_MAX', 'WCONTINUED', 'WCOREDUMP', 'WEXITED', 'WEXITSTATUS', 'WIFCONTINUED', 'WIFEXITED', 'WIFSIGNALED', 'WIFSTOPPED', 'WNOHANG', 'WNOWAIT', 'WSTOPPED', 'WSTOPSIG', 'WTERMSIG', 'WUNTRACED', 'W_OK', 'XATTR_CREATE', 'XATTR_REPLACE', 'XATTR_SIZE_MAX', 'X_OK', '_Environ', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', '_execvpe', '_exists', '_exit', '_fspath', '_fwalk', '_get_exports_list', '_putenv', '_spawnvef', '_unsetenv', '_wrap_close', 'abc', 'abort', 'access', 'altsep', 'chdir', 'chmod', 'chown', 'chroot', 'close', 'closerange', 'confstr', 'confstr_names', 'cpu_count', 'ctermid', 'curdir', 'defpath', 'device_encoding', 'devnull', 'dup', 'dup2', 'environ', 'environb', 'error', 'execl', 'execle', 'execlp', 'execlpe', 'execv', 'execve', 'execvp', 'execvpe', 'extsep', 'fchdir', 'fchmod', 'fchown', 'fdatasync', 'fdopen', 'fork', 'forkpty', 'fpathconf', 'fsdecode', 'fsencode', 'fspath', 'fstat', 'fstatvfs', 'fsync', 'ftruncate', 'fwalk', 'get_blocking', 'get_exec_path', 'get_inheritable', 'get_terminal_size', 'getcwd', 'getcwdb', 'getegid', 'getenv', 'getenvb', 'geteuid', 'getgid', 'getgrouplist', 'getgroups', 'getloadavg', 'getlogin', 'getpgid', 'getpgrp', 'getpid', 'getppid', 'getpriority', 'getrandom', 'getresgid', 'getresuid', 'getsid', 'getuid', 'getxattr', 'initgroups', 'isatty', 'kill', 'killpg', 'lchown', 'linesep', 'link', 'listdir', 'listxattr', 'lockf', 'lseek', 'lstat', 'major', 'makedev', 'makedirs', 'minor', 'mkdir', 'mkfifo', 'mknod', 'name', 'nice', 'open', 'openpty', 'pardir', 'path', 'pathconf', 'pathconf_names', 'pathsep', 'pipe', 'pipe2', 'popen', 'posix_fadvise', 'posix_fallocate', 'pread', 'preadv', 'putenv', 'pwrite', 'pwritev', 'read', 'readlink', 'readv', 'register_at_fork', 'remove', 'removedirs', 'removexattr', 'rename', 'renames', 'replace', 'rmdir', 'scandir', 'sched_get_priority_max', 'sched_get_priority_min', 'sched_getaffinity', 'sched_getparam', 'sched_getscheduler', 'sched_param', 'sched_rr_get_interval', 'sched_setaffinity', 'sched_setparam', 'sched_setscheduler', 'sched_yield', 'sendfile', 'sep', 'set_blocking', 'set_inheritable', 'setegid', 'seteuid', 'setgid', 'setgroups', 'setpgid', 'setpgrp', 'setpriority', 'setregid', 'setresgid', 'setresuid', 'setreuid', 'setsid', 'setuid', 'setxattr', 'spawnl', 'spawnle', 'spawnlp', 'spawnlpe', 'spawnv', 'spawnve', 'spawnvp', 'spawnvpe', 'st', 'stat', 'stat_result', 'statvfs', 'statvfs_result', 'strerror', 'supports_bytes_environ', 'supports_dir_fd', 'supports_effective_ids', 'supports_fd', 'supports_follow_symlinks', 'symlink', 'sync', 'sys', 'sysconf', 'sysconf_names', 'system', 'tcgetpgrp', 'tcsetpgrp', 'terminal_size', 'times', 'times_result', 'truncate', 'ttyname', 'umask', 'uname', 'uname_result', 'unlink', 'unsetenv', 'urandom', 'utime', 'wait', 'wait3', 'wait4', 'waitid', 'waitid_result', 'waitpid', 'walk', 'write', 'writev']



```python
import shutil
shutil.copyfile('fibo.py','fibo1.py')
```




    'fibo1.py'




```python
import glob
print(glob.glob('*.ipynb'))
```

    ['PythonTutorial5.ipynb', 'PythonTutorial3.ipynb', 'PythonTutorial6.ipynb', 'PythonTutorial4.ipynb', 'PythonTutorial1.ipynb', 'PythonTutorial2.ipynb']



```python
import sys
print(sys.argv)
```

    ['/home/aditya/.local/lib/python3.7/site-packages/ipykernel_launcher.py', '-f', '/home/aditya/.local/share/jupyter/runtime/kernel-9f55e36c-15e6-4856-9a61-7c082791311e.json']



```python
import argparse
parser=argparse.ArgumentParser()
```


```python
sys.stderr.write('Warning')
```

    Warning


```python
import re
print(re.findall(r'\bf[a-z]*','Foo bar fest far' ))
print(re.sub(r'(\b[a-z]+) \1',r'\1',))
```

    ['fest', 'far']



```python
'two toos'.replace('two','too')
```




    'too toos'




```python
import math
print(math.cos(math.pi/4))
print(math.log(1024,2))
```

    0.7071067811865476
    10.0



```python
import random
print(random.choice(['A','B','C']))
print(random.sample(range(100),3))
print(random.random())
print(random.randrange(99))
```

    B
    [67, 60, 36]
    0.9828944902534488
    47



```python
import statistics
print(statistics.mean([1,4,0]))
print(statistics.median([1,4,0]))
print(statistics.variance([1,4,0]))
```

    1.6666666666666667
    1
    4.333333333333333



```python
from urllib.request import urlopen
with urlopen('https://yogiadi.github.io/DataEngineerDummy2/') as response:
    for line in response:
        print(line)
```

    b'<!DOCTYPE html>\n'
    b'<html lang="en-US">\n'
    b'  <head>\n'
    b'    <meta charset="UTF-8">\n'
    b'    <meta http-equiv="X-UA-Compatible" content="IE=edge">\n'
    b'    <meta name="viewport" content="width=device-width, initial-scale=1">\n'
    b'\n'
    b'<!-- Begin Jekyll SEO tag v2.5.0 -->\n'
    b'<title>List of algorithms | DataEngineerDummy2</title>\n'
    b'<meta name="generator" content="Jekyll v3.8.5" />\n'
    b'<meta property="og:title" content="List of algorithms" />\n'
    b'<meta property="og:locale" content="en_US" />\n'
    b'<meta name="description" content="Repository for Data Engineer for tech giants" />\n'
    b'<meta property="og:description" content="Repository for Data Engineer for tech giants" />\n'
    b'<link rel="canonical" href="https://yogiadi.github.io/DataEngineerDummy2/" />\n'
    b'<meta property="og:url" content="https://yogiadi.github.io/DataEngineerDummy2/" />\n'
    b'<meta property="og:site_name" content="DataEngineerDummy2" />\n'
    b'<script type="application/ld+json">\n'
    b'{"@type":"WebSite","headline":"List of algorithms","url":"https://yogiadi.github.io/DataEngineerDummy2/","name":"DataEngineerDummy2","description":"Repository for Data Engineer for tech giants","@context":"http://schema.org"}</script>\n'
    b'<!-- End Jekyll SEO tag -->\n'
    b'\n'
    b'    <link rel="stylesheet" href="/DataEngineerDummy2/assets/css/style.css?v=b6a9771044b5518dc59046239e5d1b1673807089">\n'
    b'  </head>\n'
    b'  <body>\n'
    b'    <div class="container-lg px-3 my-5 markdown-body">\n'
    b'      \n'
    b'      <h1><a href="https://yogiadi.github.io/DataEngineerDummy2/">DataEngineerDummy2</a></h1>\n'
    b'      \n'
    b'\n'
    b'      <h2 id="list-of-algorithms">List of algorithms</h2>\n'
    b'<ol>\n'
    b'<li>\n'
    b'<p>DFS</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>BFS</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>Matching Parenthesis problem</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>Using Hash Tables</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>Variables/Pointers manipulation</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>reverse linked list (duplicates , removing duplicates)</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>sorting fundamentals (quicksort, mergesort,bubblesort techniques ,</p>\n'
    b'<p>runtime of a sort,time space complexity)</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>Recursion</p>\n'
    b'</li>\n'
    b'<li>\n'
    b'<p>custom data structures (object oriented programming)</p>\n'
    b'</li>\n'
    b'</ol>\n'
    b'<p>10.Binary search</p>\n'
    b'<h2 id="index">Index</h2>\n'
    b'<ol>\n'
    b'<li><a href="/DataEngineerDummy2/heapsort.html">HeapSort</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/sql.html">SQL</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/Quicksort.html">Quicksort</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/breadthfirstsearch.html">BFS</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/depthfirstsearch.html">DFS</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/mergesort.html">Merge Sort</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/matchingparentheses.html">Matching parentheses</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/maxsubarray.html">Maximum Subarray</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/PythonTutorial1.html">Python Tutorial1</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/PythonTutorial2.html">Python Tutorial2</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/PythonTutorial3.html">Python Tutorial3</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/PythonTutorial4.html">Python Tutorial4</a></li>\n'
    b'<li><a href="/DataEngineerDummy2/PythonTutorial5.html">Python Tutorial5</a></li>\n'
    b'</ol>\n'
    b'\n'
    b'\n'
    b'      \n'
    b'    </div>\n'
    b'    <script src="https://cdnjs.cloudflare.com/ajax/libs/anchor-js/4.1.0/anchor.min.js" integrity="sha256-lZaRhKri35AyJSypXXs4o6OPFTbTmUoltBbDCbdzegg=" crossorigin="anonymous"></script>\n'
    b'    <script>anchors.add();</script>\n'
    b'    \n'
    b'  </body>\n'
    b'</html>\n'



```python
import smtplib
server=smtplib.SMTP('localhost')
```


```python
from datetime import date
print(date.today())
print(date.today().strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B."))
print(date.today() - date(2019,11,2))
```

    2019-12-02
    12-02-19. 02 Dec 2019 is a Monday on the 02 day of December.
    30 days, 0:00:00



```python
import zlib
print(zlib.compress(b'wwwwwwwwwwwwwwwwwwwwwwwwwwww'))
print(len(zlib.compress(b'wwwwwwwwwwwwwwwwwwwwwwwwwwww')))
print(len(b'wwwwwwwwwwwwwwwwwwwwwwwwwwww'))
print(zlib.decompress(b'x\x9c+/\xc7\r\x00\xbc\xd6\r\x05'))
```

    b'x\x9c+/\xc7\r\x00\xbc\xd6\r\x05'
    11
    28
    b'wwwwwwwwwwwwwwwwwwwwwwwwwwww'



```python
from timeit import Timer
print(Timer('t=b;a=b;a=t','a=100;b=2000').timeit())
```

    0.0346057669999027



```python
def summation(values):
    """
    >>> print(sum([10,20]))
    30
    """
    return sum(values)
import doctest
doctest.testmod()
```




    TestResults(failed=0, attempted=1)




```python
import unittest
class TestSum(unittest.TestCase):
    def test_summation(self):
        self.assertEqual(summation([10,30]), 40)
```


```python
unittest.main()
```

    E
    ======================================================================
    ERROR: /home/aditya/ (unittest.loader._FailedTest)
    ----------------------------------------------------------------------
    AttributeError: module '__main__' has no attribute '/home/aditya/'
    
    ----------------------------------------------------------------------
    Ran 1 test in 0.002s
    
    FAILED (errors=1)



    An exception has occurred, use %tb to see the full traceback.


    SystemExit: True



    /home/aditya/.local/lib/python3.7/site-packages/IPython/core/interactiveshell.py:3334: UserWarning: To exit: use 'exit', 'quit', or Ctrl-D.
      warn("To exit: use 'exit', 'quit', or Ctrl-D.", stacklevel=1)



```python

```
