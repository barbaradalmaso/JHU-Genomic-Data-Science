## Module 1 Quiz

## Question 1
Which of the following Unix commands can be used to view the content of a file?
* more
* gzip
* ls
* cp
```
Answer: more
```

## Question 2
Which of the following commands can be using to compress the content of a file?
* bzip2
* mkdir
* tail
* cat
```
Answer:bzip2
```

## Question 3
The file “months” lists each of the 12 months on a separate line, and no further lines. What would be the result if the following command was run: ```cat months | head -1000 | wc –l```
* July
* 12
* April
* September
```
Answer: 12
```
## Question 4
What is the effect of using the pipe operator ‘|’ in a sequence of commands:
* Re-direct standard output only
* Divide the command into smaller sections for easy reading only, with no other effect on the results
* Re-direct standard input only
* Re-direct the standard input or standard output of a command
```
Answer: Re-direct the standard input or standard output of a command
```

## Question 5
If typing ```‘pwd’``` produces ```“/home/userA/Coursera/L1/”```, which of the following commands will list the file content of the current directory?
* listdir .
* ls /home/userA/Coursera/L1
* mkdir L1
* more * .txt
```
Answer: ls /home/userA/Coursera/L1
```

## Question 6
Suppose your current working directory is ```“/home/Coursera/L1/”```, and “peach”, “apple” and “pear” are subdirectories, each containing a single file named “genome”. What would be the current directory, as reported by running the ‘pwd’ command, after each of the four commands in the sequence below:
```
      cd apple
      rm *
      cd ../..
      mv apple plum
```
* 
```Python
/home/Coursera/L1/apple
/home/Coursera/L1/apple
/home/Coursera/L1/apple
/home/Coursera/L1/plum
```
* 
```Python
/home/Coursera/L1/apple/genome
/home/Coursera/L1
/home/Coursera/apple
/home/Coursera/plum
```
* 
```Python
/home/Coursera/
L1/appleL1/apple
L1
/home/Coursera/L1
```
*
```Python
/home/Coursera/L1/apple
/home/Coursera/L1/apple
/home/Coursera
/home/Coursera
```
```
Answer: 
/home/Coursera/L1/apple
/home/Coursera/L1/apple
/home/Coursera
/home/Coursera
``` 

## Question 7
Consider the file “seasons” with the following columns separated by spaces ‘ ‘:
```
January 1 winter
…
December 12 winter
```
What would be the sequence of outputs for the following commands: 
```
cut -d ' ' -f1,3 seasons | sort -u | wc -l" and "cut -f1 
    seasons | sort | uniq -c | wc -l
```
* 5, 10
* 4, 3
* 3, 12
* 4, 4
* 12, 12
* 4, 6
* 12, 3
* 4, 12
* 12, 20
* 3, 4
* 12, 4
```
Answer: 12, 12
``` 
## Question 8
Your current working directory is named “Plants”. Its subdirectory “apple” contains the files “apple.genome”, “apple.samples” and “apple.genes”. What would be the result of the command ```rmdir apple```?
* None of these choices
* The directory apple will be removed and all of its files will be redirected elsewhere
* The command will have no effect, since the directory is not empty
* Only the content of the “apple” directory will be removed
```
Answer: The command will have no effect, since the directory is not empty
``` 

## Question 9
Suppose that you have two files, A and B, containing experiment data:
```Python
File A:                 File B:
geneA  +            geneB   +
geneB  +            geneC   +
geneC  -
```
What would be the sequence of outputs for the commands: 
```
(1) comm -3 A B | wc –l  
(2) comm -1 -3 A B | wc –l   
(3) comm -2 A B | wc –l
```
* 1,2,4
* 3, 1, 3
* 1,1,4
* 1,1,3
```
Answer: 3, 1, 3
``` 
## Question 10
The current working directory contains four subdirectories named “apple”, “pear”, “peach” and “strawberry”, each with the following files: “genome”, “genes” and “samples”. Which of the following commands would extract the top line from all of the “genes” files?
* more {apple,pear,peach,strawberry}/genes | head -1
* more /g*s | head -1
* head -1 {apple,pear,peach,strawberry}/genes
* cat *p*/genes strawberry/genes | head -1
```
Answer: head -1 {apple,pear,peach,strawberry}/genes
``` 
