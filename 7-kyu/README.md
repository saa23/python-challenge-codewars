### 1. Complementary DNA

Deoxyribonucleic acid (DNA) is a chemical found in the nucleus of cells and carries the "instructions" for the development and functioning of living organisms.

If you want to know more: http://en.wikipedia.org/wiki/DNA

In DNA strings, symbols "A" and "T" are complements of each other, as "C" and "G". Your function receives one side of the DNA (string, except for Haskell); you need to return the other complementary side. DNA strand is never empty or there is no DNA at all (again, except for Haskell).

More similar exercise are found here: http://rosalind.info/problems/list-view/ (source)

**Examples**
``` bash
input --> output

"ATTGC" --> "TAACG"

"GTAT" --> "CATA"
```

**Solution**
``` bash
def dna_strand(dna):
    complement = {"A":"T", "T":"A", "C":"G", "G":"C"}
    result = ''.join(complement[s] for s in dna)
    return result


## Test case 1
dna = "ATTGC"
print(dna_strand(dna))      # "TAACG"

## Test case 2
dna = "GTAT"
print(dna_strand(dna))      # "CATA"
```


### 2. Friend or Foe?

Make a program that filters a list of strings and returns a list with only your friends name in it.

If a name has exactly 4 letters in it, you can be sure that it has to be a friend of yours! Otherwise, you can be sure he's not...

**Examples**
``` bash
["Ryan", "Kieran", "Jason", "Yous"] --> ["Ryan", "Yous"]

["Ryan", "Kieran", "Mark"] --> ["Ryan", "Mark"]
```

**Solution**
``` bash
def friend(x):
    result = []
    for string in x:
        if len(string) == 4:
            result.append(string)
    return result


## Test case 1
arr = ["Ryan", "Kieran", "Jason", "Yous"]
print(friend(arr))      # ["Ryan", "Yous"]

## Test case 2
arr = ["Ryan", "Kieran", "Mark"]
print(friend(arr))      # ["Ryan", "Mark"]
```



### 3. Is this a triangle?
Implement a function that accepts 3 integer values a, b, c. The function should return true if a triangle can be built with the sides of given length and false in any other case.

(In this case, all triangles must have surface greater than 0 to be accepted).

**Examples**
``` bash
Input -> Output
1,2,2 -> true
4,2,3 -> true
2,2,2 -> true
1,2,3 -> false
-5,1,3 -> false
0,2,3 -> false
1,2,9 -> false
```

**Solution**
``` bash
def is_triangle(a, b, c):
    """
    Based on Triangle Inequality Theorem
    """
    if a+b > c and a+c > b and b+c > a:
        return True
    else: return False
```



### 4. Shortest Word
Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.


**Solution**
``` bash
def find_short(s):
    words = s.split()
    l = len(words[0])

    for word in words:
        len_str = len(word)
        if l > len_str:
            l = len_str
    return l


## Test case
s = "bitcoin take over the world maybe who knows perhaps"
print(find_short(s))  # answer: 3 (from word "who")
```


### 5. Sum of two lowest positive integers

Create a function that returns the sum of the two lowest positive numbers given an array of minimum 4 positive integers. No floats or non-positive integers will be passed.

**Examples**
``` bash
[19, 5, 42, 2, 77] --> 7

[10, 343445353, 3453445, 3453545353453] --> 3453455
```

**Solution**
``` bash
def sum_two_smallest_numbers(numbers):
    numbers.sort()
    return sum(numbers[:2])


# Test case 1
arr = [19, 5, 42, 2, 77]
print(sum_two_smallest_numbers(arr))        ## 7

# Test case 2
arr = [10, 343445353, 3453445, 3453545353453]
print(sum_two_smallest_numbers(arr))        ## 3453455
```


### 6. Exes and Ohs
Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contain any char.

**Examples**
```bash
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```

**Solution**
```bash
def xo(s:str):
    s_lower = s.lower()
    x_count = s_lower.count("x")
    o_count = s_lower.count("o")

    if x_count == o_count: return True
    else: return False


print(xo('ooxx'))       ## true
print(xo('xooxx'))      ## falsle
print(xo('ooxXm'))      ## true
print(xo('zpzpzpp'))    ## true
print(xo('zzoo'))       ## false
```