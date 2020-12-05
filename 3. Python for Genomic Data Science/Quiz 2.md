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
You need what to use the public Galaxy site usegalaxy.org?
* Large hard drives (at least 20TB)
* Your own data in XML format
* Access to your own supercomputers and at least two IT professionals
* An email account and a web browser
```
Answer: An email account and a web browser
```

## Question 10
For analysis where usegalaxy.org does not provide appropriate computation power or tools, you can:
* All of these options
* Use any of the ~60 other public Galaxy servers
* Run your own, local Galaxy server
* Run Galaxy on the Amazon Cloud
```
Answer: All of these options
```

## Question 11
Galaxy...
* Cannot be used by anyone else to start a server
* Can run as a server on Windows
* Is highly configurable for many types of compute infrastructure
* Can only work on one cluster system
```
Answer: Is highly configurable for many types of compute infrastructure
```
