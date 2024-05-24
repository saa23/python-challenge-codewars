### 1. Find The Parity Outlier

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer $N$. Write a method that takes the array as an argument and returns this "outlier" $N$.

**Examples**
``` bash
[2, 4, 0, 100, 4, 11, 2602, 36] -->  11 (the only odd number)

[160, 3, 1719, 19, 11, 13, -21] --> 160 (the only even number)
```

**Solution**
``` bash
def find_outlier(arr):
    parity_count = [x % 2 for x in arr[:3]]
    if sum(parity_count) >= 2:
        # if >= 2 means majority are odds
        # find the even integer
        for num in arr:
            if num % 2 == 0:
                return num
    else:
        # if >= 2 means majority are even
        # find the odds integer
        for num in arr:
            if num % 2 != 0:
                return num


## Test case 1
arr = [2, 4, 0, 100, 4, 11, 2602, 36]
print(find_outlier(arr))        # 11 (odd number)

## Test case 2
arr = [160, 3, 1719, 19, 11, 13, -21]
print(find_outlier(arr))        # 160 (even number)
```

### 2. Array.diff
Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.

It should remove all values from list a, which are present in list b keeping their order.
``` bash
array_diff([1,2],[1]) == [2]
```

If a value is present in b, all of its occurrences must be removed from the other:
``` bash
array_diff([1,2,2,2,3],[2]) == [1,3]
```

**Solution**
``` bash
def array_diff(a, b):
    results = []
    for val in a:
        if val not in b:
            results.append(val)
    return results


## Test case 1
print(array_diff([1,2],[1]))        # [2]]

## Test case 2
print(array_diff([1,2,2]],[1]))     # [2, 2]]

## Test case 3
print(array_diff([1,2,2]],[2]))     # [1]]
```
