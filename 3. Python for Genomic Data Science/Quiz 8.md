# Lecture 8 Quiz

## Question 1
What module can we use to run BLAST over the internet in Biopython:
* NCBIXML
* NCBIWWW.qblast()
* Bio.Blast.NCBIWWW
* Bio.Blast.NCBIXML
```
Answer: NCBIWWW.qblast()
```

## Question 2
Which one of the following modules is not part of the Bio.Blast package in Biopython:
* Applications
* NCBIWWW
* FastaIO
* NCBIXML
```
Answer: Applications
```

## Question 3
Using Biopython find out what species the following unknown DNA sequence comes from:
```Python
TGGGCCTCATATTTATCCTATATACCATGTTCGTATGGTGGCGCGATGTTCTACGTGAATCCACGTTCGAAGGACATCAT
  ACCAAAGTCGTAC
AATTAGGACCTCGATATGGTTTTATTCTGTTTATCGTATCGGAGGTTATGTTCTTTTTTGCTCTTTTTCGGGCTTCTTCT
  CATTCTTCTTTGGCAC
CTACGGTAGAG
```
Hint. Identify the alignment with the lowest E value.
* Rhazya stricta
* Sambucus canadensis
* Viburnum dentatum
* Nicotiana tabacum
```
Answer: Rhazya stricta
```

## Question 4
Seq is a sequence object that can be imported from Biopython using the following statement:
```Python
from Bio.Seq import Seq

If my_seq is a Seq object, what is the correct Biopython code to print the reverse complement of my_seq?

Hint. Use the built-in function help you find out the methods of the Seq object.
```
* print('reverse complement is %s' % my_seq.reverse_complement())
* print('reverse complement is %s' % reverse(my_seq.complement()))
* print('reverse complement is %s' % complement(my_seq.reverse()))
* print('reverse complement is %s' % my_seq.reverse())
```
Answer: print('reverse complement is %s' % reverse(my_seq.complement()))
```

## Question 5
Create a Biopython Seq object that represents the following sequence:
```Python
TGGGCCTCATATTTATCCTATATACCATGTTCGTATGGTGGCGCGATGTTCTACGTGAATCCACGTTCGAAGGACATCAT
  ACCAAAGTCGTAC
AATTAGGACCTCGATATGGTTTTATTCTGTTTATCGTATCGGAGGTTATGTTCTTTTTTGCTCTTTTTCGGGCTTCTTCT
  CATTCTTCTTTGGCAC
CTACGGTAGAG
```
Its protein translation is:
* ILASYLSYIPCSYGGAMFYVNPRSKDIIPKSYN*DLDMVLLFIVSEVMFFFALFRASSHSSLAPTV
* FWPHIYPIYHVRMVARCSTSIHVRRTSYQSRTIRTSIWFYCLSYRRLCSFLLFFGLLLILLWHLR*
* WASYLSYIPCSYGGAMFYVNPRSKDIIPKSYN*DLDMVLFCLSYRRLCSFLLFFGLLLILLWHLR* 
* FWPHIYPIYHVRMVARCSTSIHVRRTSYQSRTIRTSIWFYCLSYRRLCSFLLFFGLLLILLWHLR
```
Answer: WASYLSYIPCSYGGAMFYVNPRSKDIIPKSYN*DLDMVLFCLSYRRLCSFLLFFGLLLILLWHLR* 
```
