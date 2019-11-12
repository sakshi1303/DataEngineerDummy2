## Maximum Sub array

```python
def findmaxcrosssubarray(arr,low,mid,high):
    leftsum=-math.inf
    sum=0
    for i in range(mid,low-1,-1):
        sum=sum+arr[i]
        if sum > leftsum:
            leftsum=sum
            maxleft=i
    rightsum=-math.inf
    sum=0
    for j in range(mid+1,high+1):
        sum=sum+arr[j]
        if sum>rightsum:
            rightsum=sum
            maxright=j
    return (maxleft,maxright,leftsum+rightsum)    
def findmaxsubarray(arr,low,high):
    if high==low:
        return (low,high,arr[low])
    else:
        mid=(low+high)//2
        leftlow,lefthigh,leftsum=findmaxsubarray(arr,low,mid)
        rightlow,righthigh,rightsum=findmaxsubarray(arr,mid+1,high)
        crosslow,crosshigh,crosssum=findmaxcrosssubarray(arr,low,mid,high)
        if leftsum >= rightsum and leftsum >= crosssum:
            return (leftlow,lefthigh,leftsum)
        elif rightsum >= leftsum and rightsum >= crosssum:
            return (rightlow,righthigh,rightsum)
        else:
            return (crosslow,crosshigh,crosssum)
import math
arr=[5,-6,-1,8,6,-9,10,4]
x1,x2,x3=findmaxcrosssubarray(arr,0,2,4)
print(str(x1) + str(x2) + str(x3))
x1,x2,x3=findmaxsubarray(arr,0,len(arr)-1)
print(str(x1) + str(x2) + str(x3))
print(arr)

```
