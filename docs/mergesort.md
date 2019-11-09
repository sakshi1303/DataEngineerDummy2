### Merge Sort

#### Pseudo Code

```python
merge(A,p,q,r)
    n1=q-p+1
    n2=r-q
    let L[1..n1+1] and R[1..n2+1] be new arrays
    for i=1 to n1
        L[i]=A[p+i-1]
    for j=1 to n2
        R[j]=A[q+j]
    L[n1+1]=infinity
    R[n2+1]=infinity
    i=1
    j=1
    for k=p to r
        if L[i] <= R[j]
            A[k]=L[i]
            i=i+1
        else
            A[k]=R[j]
            j=j+1
```

```python
merge-sort(A,p,r)
    if p<r
        q=[(p+r)/2]
        merge-sort(A,p,q)
        merge-sort(A,q+1,r)
        merge(A,p,q,r)
```


```python
import math
def merge(arr,p,q,r):
    n1=q-p+1
    n2=r-q
    L,R=[None]*(n1+1),[None]*(n2+1)
    for i in range(0,n1):
        L[i]=arr[p+i]
    for j in range(0,n2):
        R[j]=arr[q+j+1]
    L[n1],R[n2]=math.inf,math.inf
    i,j=0,0
    for k in range(p,r+1):
        if L[i] <= R[j]:
            arr[k]=L[i]
            i=i+1
        else:
            arr[k]=R[j]
            j=j+1
```


```python
def merge_sort(A,p,r):
    if p < r:
        q=(p+r)//2
        merge_sort(A,p,q)
        merge_sort(A,q+1,r)
        merge(A,p,q,r)
```


```python
arr=[2,9,6,0,3,1,5,7]
merge_sort(arr,0,len(arr)-1)
print(arr)
```

    [0, 1, 2, 3, 5, 6, 7, 9]
    
