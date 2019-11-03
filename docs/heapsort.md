```python
def heapify(arr,n,i):
    largest=i
    l=2*i+1
    r=2*i+2
    if l < n and arr[largest] < arr[l]:
        largest=l
    if r < n and arr[largest] < arr[r]:
        largest=r
    if largest != i:
        arr[largest],arr[i]=arr[i],arr[largest]
        heapify(arr,n,largest)
```


```python
def heapsort(arr):
    n=len(arr)
    for i in range(n,-1,-1):
        heapify(arr,n,i)
    for i in range(n-1,0,-1):
        arr[i],arr[0]=arr[0],arr[i]
        heapify(arr,i,0)
```


```python
for i in range(4,0,-1):
    print(i)
```

    4
    3
    2
    1
    


```python
arr=[7,3,9,2]
heapsort(arr)
print(arr)
```

    [2, 3, 7, 9]
    


```python

```
