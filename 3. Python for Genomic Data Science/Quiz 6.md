# Lecture 6 Quiz

## Question 1
Which of the following is a correct Python program to obtain the Python version you are using?

A.
```Python
print(__version__)
```
B.
```Python
import sys

print(sys.version)
```
C.
```Python
print(version)
```
D.
```Python
import sys
```
print(sys.__version__)
* B
* B, C, D
* A, B
* A, B, C

```
Answer: B
```

## Question 2
What does the following code do?
```Python
import random
def create_dna(n, alphabet=’acgt’):
    return ’’.join([random.choice(alphabet) for i in range(n)])
dna = create_dna(1000000)
```
* Creates a dna variable containing a string of length 1000000, and with the a,c,g,t characters.
* Creates a dna variable containing a string of length 1000000, containing the 'acgt' substring repeated.
* Creates a dna variable containing a string of length 999999, and with the a,c,g,t characters.
* Creates a dna variable containing a string of length less than 1000000, and with the a,c,g,t characters.
```
Answer: Creates a dna variable containing a string of length 1000000, and with the a,c,g,t characters.
```

## Question 3
The following functions are all supposed to count how many times a certain base (represented as a character variable in Python) 
appears in a dna sequence (represented as a string variable in Python):
```Python
def count1(dna, base):
    i = 0
    for c in dna:
        if c == base:
      i += 1 
    return i
def count2(dna, base):
    i = 0 
    for j in range(len(dna)):
        if dna[j] == base:
      i += 1 
    return i 
def count3(dna, base):
    match = [c == base for c in dna]
    return sum(match)
def count4(dna, base):
    return dna.count(base)
def count5(dna, base):
    return len([i for i in range(len(dna)) if dna[i] == base])
def count6(dna,base):
    return sum(c == base for c in dna)
```    
Which of them is correct?
* All of them are correct.
* count3, count4 only
* count2, count3 only
* count1, count2 only
```
Answer: All of them are correct.
```

## Question 4
Which of the correct functions defined in the previous exercise is the fastest?

Hint. You will need to generate a very large string to test them on, and the function clock() from the time module to time each function.
* count5  
* count3 
* count4
* count2
```
Answer: count4
```

## Question 5
If the PYTHONPATH environment variable is set, which of the following directories are searched for modules?
```Python
A) PYTHONPATH directory
```
```Python
B) current directory
```
```Python
C) home directory
```
```Python
D) installation dependent default path
```
* A, B, and D
* A only 
* A, B, and C
* A and D 
```
Answer: A, B, and D
```

## Question 6
A student imports a module called dnautil in Python using the following command:
```Python
import dnautil

What does the following call to the dir function do?

dir(dnautil)
```
* Lists the variables defined in the dnautil module
* Lists all the attributes of the dnautil module
* Lists the gc and has_stop_codon functions
* Lists all the functions in the dnautil module
```
Answer: Lists all the attributes of the dnautil module
```
