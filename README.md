Check whether array is subset of another array or not
In this program we will  Check whether array is subset of another array or not in Python. A subset is defined as a set whose elements are all members of another set. We will input two arrays and check whether the second array is subset of first array and display accordingly

Check whether array is subset of another array or not
Method Discussed :
Method 1 : Using nested loops
Method 2 : Using sorting and binary search.
Method 3 : Using sorting and merging.
Method 4 : Using Hashing
Method 5 : Using Union concept
Method 1 :
Run a loop for loo from index 0 to length of arr2
Run a inner loop from index 0 to length of arr2
If(arr2[i]==arr1[j]), then break the inner loop
Check if(j==m) then return 0.
Otherwise, return 1.
Method 1 : Code in Python
#Write a Program to Check whether array is subset of another array or not
def isSubset(arr1, arr2, m, n):
    i = 0
    j = 0
    for i in range(n):
        for j in range(m):
            if(arr2[i] == arr1[j]):
                break
         
        if (j == m):
            return 0
    return 1
 
# Driver code
arr1 = [11, 12, 13, 21, 30, 70]
arr2 = [11, 30, 70, 12]
 
m = len(arr1)
n = len(arr2)
 
if(isSubset(arr1, arr2, m, n)):
    print("arr2[] is subset of arr1[] ")
else:
    print("arr2[] is not a subset of arr1[]")
Output :
arr2[] is subset of arr1[]
Related Pages
Find maximum product sub-array in a given array

Finding Arrays are disjoint or not

Determine can all numbers of an array be made equal

Finding Minimum sum of absolute difference of given array

Sort an array according to the order defined by another array 

Method 2 :
First sort the array using quick sort algorithm.
Then start iterating over the second array, and using binary search search the elements of arr2 in arr1.
Method 2 : Code in Python
#Write a Program to Check whether array is subset of another array or not
def isSubset(arr1, arr2, m, n):
    i = 0
 
    quickSort(arr1, 0, m-1)
    for i in range(n):
        if (binarySearch(arr1, 0, m - 1, arr2[i]) == -1):
            return 0
 
    return 1
 

def binarySearch(arr, low, high, x):
    if(high >= low):
        mid = (low + high)//2
 
        if((mid == 0 or x > arr[mid-1]) and (arr[mid] == x)):
            return mid
        elif(x > arr[mid]):
            return binarySearch(arr, (mid + 1), high, x)
        else:
            return binarySearch(arr, low, (mid - 1), x)
 
    return -1
 
 
def partition(A, si, ei):
    x = A[ei]
    i = (si - 1)
 
    for j in range(si, ei):
        if(A[j] <= x):
            i += 1
            A[i], A[j] = A[j], A[i]
    A[i + 1], A[ei] = A[ei], A[i + 1]
    return (i + 1)
 
def quickSort(A, si, ei):
    if(si < ei):
        pi = partition(A, si, ei)
        quickSort(A, si, pi - 1)
        quickSort(A, pi + 1, ei)
 
 
# Driver code
arr1 = [11, 1, 13, 21, 3, 7]
arr2 = [11, 3, 7, 1]
 
m = len(arr1)
n = len(arr2)
 
if(isSubset(arr1, arr2, m, n)):
    print("arr2[] is subset of arr1[] ")
else:
    print("arr2[] is not a subset of arr1[] ")
Output :
arr2[] is subset of arr1[]
Method 3 :
Sort the arr1.
Using concept of merging check the elements of arr2 in arr1.
Method 3 : Code in Python
#Write a Program to Check whether array is subset of another array or not
def isSubset(arr1, arr2, m, n):
    i = 0
    j = 0
    if m < n:
        return 0
 
    arr1.sort()
    arr2.sort()
 
    while i < n and j < m:
        if arr1[j] < arr2[i]: 
            j += 1 
        elif arr1[j] == arr2[i]: 
            j += 1 
            i += 1 
        elif arr1[j] > arr2[i]:
            return 0
    return False if i < n else True
 
 
# Driver code
arr1 = [11, 1, 13, 21, 3, 7]
arr2 = [11, 3, 7, 1]
 
m = len(arr1)
n = len(arr2)
if isSubset(arr1, arr2, m, n) == True:
    print("arr2 is subset of arr1 ")
else:
    printf("arr2 is not a subset of arr1 ")
Output :
arr2[] is subset of arr1[]
Method 4 :
In this method we will use hashing concept.

Method 4 : Code in Python
#Write a Program to Check whether array is subset of another array or not
def isSubset(arr1, m, arr2, n):
     
    # Using STL set for hashing
    st = set()
 
    # hset stores all the values of arr1
    for i in range(0, m):
        st.add(arr1[i])
 
    for i in range(0, n):
        if arr2[i] in st:
            continue
        else:
            return False
 
    return True
    
# Driver Code
arr1 = [ 11, 12, 13, 21, 30, 70 ]
arr2 = [ 11, 30, 70, 12 ]
     
m = len(arr1)
n = len(arr2)
     
if (isSubset(arr1, m, arr2, n)):
    print("arr2[] is subset of arr1[] ")
else:
    print("arr2[] is not a subset of arr1[] ")
Output :
arr2[] is subset of arr1[]
Union function:
Let's see how to check whether array is subset of another array or not using union function in Python. In general Mathematics we know that a set is said to subset of another set if A U B = A In set theory, the union of two sets is the set of all elements in the two sets.
A={11 13 5 1 7}
B={7 5 1}
A U B ={11 13 5 1 7}
Here A U B equals to set A hence B is subset of A
Method 5 :
Check if arr1.union(arr2)==arr1
Then print arr2 is subset of arr1.
Otherwise Print arr2 is not subset of arr1
Method 5 : Code in Python
#Write a Program to Check whether array is subset of another array or not
arr1 = {11, 12, 13, 21, 30, 70}
arr2 = {11, 30, 70, 12}
 
m = len(arr1)
n = len(arr2)
 
if(arr1.union(arr2)==arr1):
    print("arr2[] is subset of arr1[] ")
else:
    print("arr2[] is not a subset of arr1[]")
Output
arr2[] is subset of arr1[] 
