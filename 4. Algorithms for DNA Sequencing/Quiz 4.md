# Module 4
 
## Question 1
The slow (sometimes called “brute force”) algorithm for finding the shortest common superstring of the strings in set S involves:
* Iteratively removing strings from S that don’t belong in the superstring XXX
* Concatenating the strings in of S xx
* Finding the longest common substring of the strings in S XXX
* Trying all orderings of the strings in S
```
Answer:  Trying all orderings of the strings in S
```

## Question 2
Which of the following is not a true statement about the slow (brute force) shortest common superstring algorithm.
* The amount of time it takes grows with the factorial of the number of input strings
* The superstring returned might be longer than the shortest possible one
* It might collapse repetitive portions of the genome
```
Answer: The superstring returned might be longer than the shortest possible one
```

## Question 3
Which of the following is not a true statement about the greedy shortest common superstring formulation of the assembly problem?
* The superstring returned might be longer than the shortest possible one 
* The amount of time it takes grows with the factorial of the number of input strings
* It might collapse repetitive portions of the genome
```
Answer: The amount of time it takes grows with the factorial of the number of input string
```

## Question 4
True or false: an Eulerian walk is a way of moving through a graph such that each node is visited exactly once
* True 
* False
```
Answer: False
```

## Question 5
If the genome is repetitive and we try to use the De Bruijn Graph/Eulerian Path method for assembling it, we might find that:
* The genome “spelled out” along the Eulerian path is not a superstring of the reads
* There is more than one Eulerian path
* The De Bruijn graph breaks into pieces
```
Answer: There is more than one Eulerian path
```

## Question 6
In a De Bruijn assembly graph for given k, there is one edge per
* k-mer
* k-1-mer
* genome
* read
```
Answer: k-mer
```

## Question 7
Which of the following does not help with the problem of assembling repetitive genomes:
* Longer reads
* Increasing minimum required overlap length for the overlap graph
* Paired-end reads
```
Answer: Increasing minimum required overlap length for the overlap graph
```
