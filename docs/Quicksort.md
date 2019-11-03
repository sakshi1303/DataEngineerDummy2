## Quicksort


```python
def partition(arr,low,high):
    i=low-1
    pivot=arr[high]
    for j in range(low,high):
        if arr[j]<pivot:
            i=i+1
            arr[i],arr[j]=arr[j],arr[i]
    arr[high],arr[i+1]=arr[i+1],arr[high]
    return i+1
```


```python
def quicksort(arr,low,high):
    if low<high:
        pi=partition(arr,low,high)
        quicksort(arr,low,pi-1)
        quicksort(arr,pi+1,high)
```


```python
arr=[2,9,4,10]
n=len(arr)
quicksort(arr,0,n-1)
```


```python
print(arr)
```

    [2, 4, 9, 10]
    
