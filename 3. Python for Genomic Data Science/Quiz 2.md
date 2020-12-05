## Question 1
What is the result of the following operation in Python: 17/2 ?
* 8 or 8.5, depending on the Python version
* 8
* 8.0
* 8.5
```
Answer: 8.5
```

## Question 2
Given the following code in Python:
```python
>>> mydna = 'acgt'
>>> mydna = mydna + mydna
```
What will be the result of typing the following at the Python interpreter prompt:
```python
>>> myDna
```
* an error message
* no output
* ' '
* 'ACGT'
```
Answer: an error message
```

## Question 3
The following commands are entered at the prompt of Python interpreter.
```python
>>> dna="atgctggggact"
>>> dna[:3]
>>> dna
```
What will be the output of the last command?
* 'ctggggact'
* 'atg'
* 'atgctggggact'
* 'atgc'
```
Answer: 'atgctggggact'
```

## Question 4
What is the output of
```python
'dna'+1+2+3
```
* Error
* dna
* dna123
* dna6
```
Answer: Error
```

## Question 5
Given a string variable called dna, for instance:
```python
>>> dna='agcagttagcta'
```
What is a correct way to count the number of occurrences of 'ag' in dna:
* dna.count('ag')
* count(dna,'a')+count(dna,'g')
* count(dna,'ag')+count(dna,'AG')
* count(dna,'ag')
```
Answer: dna.count('ag')
```

## Question 6
What is the value of the variable seqlen, after the following code is entered in Python:
```python
>>> seqlen = '10bp'
>>> seqlen='2'+seqlen
>>> seqlen=seqlen*2
```
* '1010bp'
* '12bp12bp'
* '10bp'
* '210bp210bp'
```
Answer: '210bp210bp'
```

## Question 7
You wish to display the following text using the print function in Python:
```python
>HSBGPG Human bone gla gene\transcript "BGP"
GGCAGATTCCCCCTAGACODE
```
Select the correct way to display this output in Python 3.xx:
* print("""\ >HSBGPG Human bone gla gene\transcript "BGP" GGCAGATTCCCCCTAGA""")
* print('>HSBGPG Human bone gla gene\\transcript "BGP"\nGGCAGATTCCCCCTAGA')
* print('>HSBGPG Human bone gla gene\transcript "BGP"
  GGCAGATTCCCCCTAGA')
* print(">HSBGPG Human bone gla gene\transcript "BGP"\nGGCAGATTCCCCCTAGA")
```
Answer: print('>HSBGPG Human bone gla gene\\transcript "BGP"\nGGCAGATTCCCCCTAGA')
```

## Question 8
A student is writing Python 3.xx code to read in a dna sequence using the following command:
```python
>>> dna=input("Enter a DNA sequence, please:")
```
The student tries three different ways to compute the index of the second occurrence of the string 'atg' in the dna sequence:
```python
A.
>>> o1 = dna.find('atg')
>>> dna.find('atg',o1+1)

B.
>>> dna.rfind('atg')

C. 
>>> dna.find('atg',dna.find('atg')+1) 
```
Which of these ways is correct:
* A or C
* B
* A
* None of these
```
Answer: B
```

## Question 9
What are the types of the following literals, in order?
```python
1, 1., 1.0, 1e10, 0x12, "1", "1.0", 100000000000000000, 100000000000000000.0
```
int, no type (error), float, float, hex, string, string, int, float
int, float, float, float, int, str, str, int, float
int, float, float, float, hex, int, float, int, float
int, no type (error), float, double, int, string, string, long, double
```
Answer: int, no type (error), float, float, hex, string, string, int, float
```

## Question 10
What is the result of 
```python
int(4+6/2+2*2)?
```
* 11.0
* 9
* 9.0
* 11
```
Answer: 11
```

## Question 11
What is the difference between the expressions
```python
val = 1234567 

val = 1.234567 * 10 ** 6
```
* In the first expression val is of type int, in the second val is of type float. Numerical values are different.
* In the first expression val is of type int, in the second val is of type float. Numerical value is the same.
* The two values are not equal.
* No difference.
* The value of the variable val in the first expression is different from the value of the variable val in the second expression.
```
Answer: In the first expression val is of type int, in the second val is of type float. Numerical values are different.
```

# Question 12
What are the values of the variables a, b, c and d after the following statements have been executed?
```python
a=1

b=2

c=a+b

a = b

a = c

d=a+c
```
* a will be 2, b will be 2, c 3 and d 4.
* a will be 3, b will be 2, c 3 and d 6.
* a will be 1, b will be 2, c 3 and d 6.
* a will be 1, b will be 2, c 3 and d 4.
```
Answer: a will be 3, b will be 2, c 3 and d 6.
```
