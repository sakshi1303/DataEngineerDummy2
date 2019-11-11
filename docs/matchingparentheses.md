## Matching parentheses

```python
open_list=["[","{","("]
closed_list=["]","}",")"]
def check(mystr):
    stack=[]
    for i in mystr:
        if i in open_list:
            stack.append(i)
        elif i in closed_list:
            pos=closed_list.index(i)
            if ((len(stack)>0) and (open_list[pos] == stack[len(stack)-1])):
                stack.pop()
            else:
                return "Unbalanced"
    if len(stack) == 0:
        return "Balanced"
str1="{[]{()}}"
print(check(str1))
str2="[[{]}]"
print(check(str2))
```
