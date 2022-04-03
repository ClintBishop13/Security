## Level Goal

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

sort data.txt to sort the text alphabetically 
eg.  sort data.txt

uniq -u data.txt remove duplicate text

bandit8@bandit:~$ ls  
data.txt  
bandit8@bandit:~$ sort data.txt | uniq -u  
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR