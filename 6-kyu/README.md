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
print(array_diff([1,2],[1]))        # [2]

## Test case 2
print(array_diff([1,2,2]],[1]))     # [2, 2]

## Test case 3
print(array_diff([1,2,2]],[2]))     # [1]
```


### 3. Roman Numerals Decoder
Create a function that takes a Roman numeral as its argument and returns its value as a numeric decimal integer. You don't need to validate the form of the Roman numeral.

Modern Roman numerals are written by expressing each decimal digit of the number to be encoded separately, starting with the leftmost digit and skipping any 0s. So 1990 is rendered "MCMXC" (1000 = M, 900 = CM, 90 = XC) and 2008 is rendered "MMVIII" (2000 = MM, 8 = VIII). The Roman numeral for 1666, "MDCLXVI", uses each letter in descending order.

**Examples**
``` bash
"MM"      -> 2000
"MDCLXVI" -> 1666
"M"       -> 1000
"CD"      ->  400
"XC"      ->   90
"XL"      ->   40
"I"       ->    1
```

**Solution**
``` bash
def solution(roman : str) -> int:
    rules = {
        'I': 1, 
        'V': 5, 
        'X': 10, 
        'L': 50, 
        'C': 100, 
        'D': 500, 
        'M': 1000,
        }

    result = 0
    i = 0

    while i < len(roman):
        current_value = rules[roman[i]]
        if i + 1 < len(roman) and rules[roman[i + 1]] > current_value:
            result -= current_value
        else:
            result += current_value
        i += 1

    return result


## Test case 1
print(solution('MDCLXVI'))      # 1666

## Test case 2
print(solution('CD'))           # 400

## Test case 3
print(solution('XC'))           # 90
```

### 4. Count characters in your string
The main idea is to count all the occurring characters in a string. If you have a string like aba, then the result should be {'a': 2, 'b': 1}.

What if the string is empty? Then the result should be empty object literal, {}.

**Solution**
Alternative 1
```bash
from collections import Counter

def count(s: str):
    res = Counter(s)
    return dict(res)
```


Alternative 2
```bash
def count(s: str):
    dict_res = {}

    for char in s:
        if char in dict_res:    ## if the char has been mapped
            dict_res[char] += 1
        else:                   ## if the char is mapped for the first time
            dict_res[char] = 1
    return dict_res
```


### 5. Are they the "same"?
Given two arrays `a` and `b` write a function comp(a, b) (orcompSame(a, b)) that checks whether the two arrays have the "same" elements, with the same multiplicities (the multiplicity of a member is the number of times it appears). "Same" means, here, that the elements in b are the elements in a squared, regardless of the order.

**Examples**
```bash
a = [121, 144, 19, 161, 19, 144, 19, 11]  
b = [121, 14641, 20736, 361, 25921, 361, 20736, 361]
The result of comp(a,b) is `True`


a = [121, 144, 19, 161, 19, 144, 19, 11] 
b = [11*11, 121*121, 144*144, 19*19, 161*161, 19*19, 144*144, 19*19]
The result of comp(a,b) is `False`

```

**Solution**
```bash
def comp(array1, array2):
    try:
        return sorted([v**2 for v in array1]) == sorted(array2)
    except:
        return False
```

### 6. Split Strings
Complete the solution so that it splits the string into pairs of two characters. If the string contains an odd number of characters then it should replace the missing second character of the final pair with an underscore ('_').

**Examples**
```bash
'abc' =>  ['ab', 'c_']
'abcdef' => ['ab', 'cd', 'ef']
```

**Solution**
```bash
def solution(s):
    pairs = [s[i:i+2] for i in range(0, len(s), 2)]
    if len(pairs) == 0:
        return []
    if len(pairs[-1]) < 2:
        pairs[-1] += '_'
    return pairs
```