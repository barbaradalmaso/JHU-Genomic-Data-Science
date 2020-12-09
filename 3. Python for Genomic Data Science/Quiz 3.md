# Lecture 3 Quiz
## Question 1
What data type is the object below?
```Python
[1e-10,(1,2),"BGP",[3]]
```
* Stack
* Array
* List
* Set
```
Answer:
```

## Question 2

What is the value returned when the code below is executed:
```Python
>>> grades = [70,80.0,90,100]

>>> (grades[1]+grades[3])/2
```
* 80
* 90
* 90.0
* 85
```
Answer:
```

## Question 3
Suppose splice_site_pairs = ['GT-AG','GC-AG','AT-AC']. What is splice_site_pairs[:-1] ?
* ['GT-AG','GC-AG','AT-AC']
* ['GT-AG']
* ['GT-AG', 'GC-AG']
* Error
```
Answer:
```

## Question 4
We want to add a new element to a list variable L. The new element is stored in a variable e. What command do we use?
* L.addEnd(e)
* L.add(e)
* L.addLast(e)
* L.append(e)
```
Answer:
```

## Question 5

Suppose t = ('a', 'c', 'g', 't'). What will be the output of the following code:
```Python
>>> t.append( ('A','C','G','T') )

>>> print len(t)
```
* 8
* 1
* Error
* 5
```
Answer:
```

## Question 6
What is the result of the print function in the following Python 3.xx code:
```Python
dna=input("Enter DNA sequence:")

dna_counts={'t':dna.count('t'),'c':dna.count('c'),'g':dna.count('g'),'a':dna.count('a')}

nt=sorted(dna_counts.keys())

print(nt[-1])
```
* 't'
* 'c'
* 'a'
* 'g'
```
Answer:
```

## Question 7
To delete an entry with the key 'a' from the dictionary dna_counts={'g': 13, 'c': 3,
```Python
't': 1, 'a': 16} what command do we use:
```
* dna_counts['a']=''
* dna_counts.delete('a':16)
* dna_counts[-1]=''
* del dna_counts['a']
```
Answer:
```

## Question 8
Suppose dna is a string variable that contains only 'a','c','g' or 't' characters. 
What Python code below can we use to find the frequency (max_freq) of the most frequent character in string dna?

* 
```Python
dna_counts=
{'t':dna.count('t'),'c':dna.count('c'),'g':dna.count('g'),'a':dna.count('a')}
max_freq=sorted(dna_counts.keys())[0]
```
*
```Python
dna_counts=
{'t':dna.count('t'),'c':dna.count('c'),'g':dna.count('g'),'a':dna.count('a')}
max_freq=sorted(dna_counts.values())[-1]
```
*
```Python
dna_counts=
{'t':dna.count('t'),'c':dna.count('c'),'g':dna.count('g'),'a':dna.count('a')}
max_freq=sorted(dna_counts.keys())[-1]
```

```
Answer:
```

## Question 9
Suppose L1 and L2 are two list variables. What does the list variable L3 = list(set(L1)&set(L2)) contain?
* A list of two sets: one set with the elements of list L1, and another set with the elements of L2
* A list of sets formed with the elements of lists L1 and L2
* All elements in lists L1 and L2
* All elements common between lists L1 and L2 without duplicates
```
Answer:
```

## Question 10
How many elements are in the dictionary someData after the following code has been executed?
```Python
someData = { }
someData['cheese'] = 'dairy'
someData['Cheese'] = 'dairy'
someData['Cheese'] = 'Dairy'
someData['cheese'] = 'Dairy'
```
* Can't say - an error message was issued.
* 3
* 2
* 0
```
Answer:
```
