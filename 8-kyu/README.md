### Find the smallest integer in the array

Given an array of integers your solution should find the smallest integer.

**Examples**
Given `[34, 15, 88, 2]` your solution will return 2
Given `[34, -345, -1, 100]` your solution will return -345
You can assume, for the purpose of this kata, that the supplied array will not be empty.

**Solution**
``` bash
def find_smallest_int(arr):
    smallest = arr[0]
    for num in arr:
        if num < smallest:
            smallest = num
    return smallest


## Test case 1
arr = [34, 15, 88, 2]
print(find_smallest_int(arr))       # 2

## Test case 2
arr = [34, -345, -1, 100]
print(find_smallest_int(arr))       # -345
```

