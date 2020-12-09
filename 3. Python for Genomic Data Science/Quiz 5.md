# Lecture 5 Quiz

## 1. Question 1
A student writes several functions to swap the values of the two variables x and y, i.e. if x=1 and y=2, after 
calling the swap function x=2 and y=1. The different functions that the student writes are given below:
```Python
def swap1(x,y) :
    x=y
    y=x
    return(x,y)
def swap2(x,y) :
    return(y,x)
def swap3(x,y) :
    z=x
    x=y
    y=z
    return(x,y)
def swap4(x,y) :
    x,y=y,x
    return(x,y)
```    
Which of the functions swap1, swap2, swap3, and swap4 is correct?
* Functions swap3, and swap4 only
* None
* Functions swap2, swap3, and swap4 only
* Function swap2 only

## Question 2
Consider the following two functions:
```Python
def f1(x):
    if (x > 0):
        x = 3*x 
        x = x / 2
    return x
def f2(x):
    if (x > 0):
        x = 3*x
    x = x / 2
    return x
```
For what values of x will f1 and f2 return the same value?
* When x is zero or positive
* Any value of x
* For negative values of x only
* For positive values of x only

## Question 3
A recursive function in programming is a function that calls itself during its execution. The following two functions are examples of recursive functions:
```Python
def function1(length):
    if length > 0:
        print(length)
        function1(length - 1)
def function2(length):
    while length > 0:
        print(length)
        function2(length - 1)
```
What can you say about the output of function1(3) and function2(3)?
* function1 produces the output: 

    3 2 1 and function2 runs infinitely.
* function1 produces the output: 3 2 1

    and function2 runs infinitely.
* The two functions produce the same output: 3 2 1
* The two functions produce the same output: 1 2 3.
 

## Question 4
The following recursive function takes three positive integer arguments:
```Python
def compute(n,x,y) :
    if n==0 : return x
    return compute(n-1,x+y,y)
```
What is the value returned by the compute function?
* n*(x+y)
* x
* x+y
* x+n*y

## Question 5
What will the returned value be for the compute function defined in Question 4 if the argument n is negative?
* The function will never return a value.
* x-n*y
* x
* x+n*y

## Question 6
The following functions are all intended to check whether a string representing a dna sequence contains any characters 
that are not 'a','c','g','t', 'A', 'C', 'G', or 'T'. At least some of these functions are wrong. Which ones are correct?
```Python
def valid_dna1(dna):
    for c in dna:
        if c in 'acgtACGT':
            return True
        else:
            return False
```
```Python 
def valid_dna2(dna):
    for c in dna:
       if 'c' in 'acgtACGT':
            return 'True'
        else:
            return 'False'
```
```Python
def valid_dna3(dna):
    for c in dna:
        flag = c in 'acgtACGT'
    return flag
```
```Python
def valid_dna4(dna):
    for c in dna:
        if not c in 'acgtACGT':
            return False
    return True
```
* valid_dna1, and valid_dna3 only
* valid_dna4 only
* valid_dna1, valid_dna2, and valid_dna4 only
* valid_dna2 only

## Question 7
What is the type of variable L3 and what is its value if L1 and L2 are lists?
```Python
L3 = [i for i in set(L1) if i in L2]
```
* L3 is a tuple with elements that are both in L1 and L2
* L3 is a set with all the elements in L1 and L2.
* L3 is a list that contains only the elements that are common between the lists (without duplicates).
* L3 is a set with elements common between the lists L2 and L3.

## Question 8
What will be printed after executing the following code?
```Python
>>>def f(mystring):
         print(message)
         print(mystring)
         message="Inside function now!"
         print(message)
>>>message="Outside function!"
>>>f("Test function:")
```
*   Outside function!
*   Outside function!
    Test function:
    Inside function now!
*   An error message.
*   Test function, then an error message

## Question 9
Which statement below is true about a function:
* must have at least one parameter
* must always have a return statement
* its arguments always appear within brackets
* may have no parameters

## Which of the following function headers is correct?
```
   A. def afunction(a1 = 1, a2):

   B. def afunction(a1 = 1, a2, a3 = 3):

   C. def afunction(a1 = 1, a2 = 2, a3 = 3):
```   
* C
* None is correct.
* A
* A, B
