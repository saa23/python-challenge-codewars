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
print(dna_strand(dna))

## Test case 2
dna = "GTAT"
print(dna_strand(dna))
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
print(friend(arr))

## Test case 2
arr = ["Ryan", "Kieran", "Mark"]
print(friend(arr))
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
    return l # l: shortest word length


## Test case
s = "bitcoin take over the world maybe who knows perhaps"
print(find_short(s))

```