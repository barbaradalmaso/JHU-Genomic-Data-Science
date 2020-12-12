# Module 2

## Question 2
Boyer-Moore: How many alignments are skipped by the bad character rule for this alignment?

Note: the number of skips is one less than the number of positions P shifts by. That is, if the pattern shifts by 2 positions, that's 1 alignment skipped.

Also note: the question is asking only about the alignment shown. Do not consider any other alignments of P to T in your answer.

```python
T: GGCTATAATGCGTA
P:  TAATAAA
```

```
Answer: 0
```

## Question 2
Boyer-Moore: How many alignments are skipped by the good suffix rule in this scenario?

```python
T: GGCTATAATGCGTA
P:  TAATTAA
```
```
Answer: 3
```

## Question 3
Boyer-Moore, true or false: for given P and T, it's possible that some characters from T will never be examined, i.e., won't be involved in any character comparisons.
* False
* True
```
Answer: True


## Question 4
Consider a version of Boyer-Moore that uses only the bad character rule (no good suffix rule), and say our pattern P is a random string of 50% As and 50% Ts. In which scenario would you expect Boyer-Moore to skip the most alignments?
* The text T consists of 40% As, 40% Ts, 10% Cs and 10%Gs
* The text T consists of 10% As, 10% Ts, 40% Cs and 40%Gs
* The text T consists of 25% As, 25% Ts, 25% Cs and 25%Gs
```
Answer: The text T consists of 10% As, 10% Ts, 40% Cs and 40%Gs
```

## Question 5
The naive exact matching algorithm preprocesses:
* The text T
* Both
* The pattern P
* Neither
```
Answer: Neither
```

## Question 6
The Boyer-Moore algorithm preprocesses:
* The pattern P
* The text T
* Neither
* Both
```
Answer: The pattern P
```

## Question 7
In which of the these scenarios is an offline matching algorithm not appropriate?
* A tool that evaluates a password by comparing it against a large database of bad (easy-to-guess) passwords
* Your web browser's "find" function that allows you to find a particular word on the web page
you are currently viewing
A tool that searches for words in an archive of every speech made in the U.S. Congress
```
Answer: Your web browser's "find" function that allows you to find a particular word on the web page
you are currently viewing
```

8.
Question 8
Say we have a k-mer index containing all 5-mers from T. We query the index using the first 5-mer from P and the index returns a single index hit. What can we say about whether P occurs in T? Assume T is longer than P and that P is at least 6 bases long.
* It definitely does
* It definitely does not
* We don't know; not enough information
```
Answer: We don't know; not enough information
```

## Question 9
Say we have a k-mer index containing all k-mers from T and we query it with 3 different k-mers from the pattern P. The first query returns 0 hits, the second returns 1 hit, and the third returns 3 hits. What can we say about whether P occurs in T?
1 point
* It definitely does
* It definitely does not
* We don't know; not enough information
```
Answer: It definitely does not
```

## Question 10
Which of the following is not an "edit" allowed in edit distance:
* Transposition
* Substitution
* Insertion
* Deletion
```
Answer: Transposition
```
