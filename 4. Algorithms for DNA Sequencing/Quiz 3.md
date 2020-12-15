# Module 3

## Question 1
The value in each edit-distance matrix element depends on its neighbors:
* Above, to the left, and to the upper-left
* To the upper-left, to the left and to the lower-left
* To the left and to the lower-left
* Above, to the left, and to the right
```
Answer: Above, to the left, and to the upper-left
```

## Question 2
Say we have filled in the approximate matching matrix and identified the minimum value (say, 2) in the bottom row. Now we would like to know the shape of the corresponding 2-edit alignment, i.e. we would like to know where the insertions, deletions and substitutions are. We use a procedure called:
* Filling 
* Pathing 
* Binary search
* Traceback
```
Answer: Traceback
```

## Question 3
Say the edit distance between DNA strings α and β is 407. What is the edit distance 
between α and βG (β concatenated with the base G)?
* could be any of the other choices
* 406
* 407
* 408
```
Answer: could be any of the other choices
```

## Question 4
Say we are using dynamic programming to find approximate occurrences of P in T. About how many dynamic programming matrix elements do we have to fill in?
* |T|^2 (squared)
* |P| |T|
* |P|^2 (squared)
* |P| + |T|
```
Answer: |P| |T|
```

## Question 5
Local alignment is different from global alignment because:
* Insertions and deletions incur no penalty
* It finds similarities between substrings rather than between entire strings
* It compares three strings instead of two
* There is no dynamic programming algorithm for solving it
```
Answer: It finds similarities between substrings rather than between entire strings
```

## Question 6
The first law of assembly says that if a prefix of read A is similar to a suffix of read B, then...
* A and B should not be joined in the final assembly
* Read B might have a sequencing error at the end
* A and B must be from different genomes
* A and B might overlap in the genome
```
Answer: A and B might overlap in the genome
```

## Question 7
The second law of assembly says that more coverage leads to...
* more sequencing errors
* less accurate results
* more and longer overlaps between reads
```
Answer: more and longer overlaps between reads
```

## Question 8
In an overlap graph, the nodes of the graph correspond to
* Genomes
* Reads
* Bases
* Overlaps
```
Answer: Reads
```

## Question 9
The overlap graph is a useful structure because:
* It makes it faster to compare reads
* A reconstruction of the genome corresponds to a path through the graph
* It helps to ignore long overlaps
```
Answer: A reconstruction of the genome corresponds to a path through the graph
```

## Question 10
Which of the following is not a reason why an overlap might contain sequence differences (i.e. might not be an exact match):
* Polyploidy
* Insufficient coverage
* Sequencing error
```
Answer: Insufficient coverage
```
