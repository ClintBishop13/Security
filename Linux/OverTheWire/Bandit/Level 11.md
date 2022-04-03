## Level Goal

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd

base64 to decode base64 to text
eg. base64 data.txt --decode

bandit10@bandit:~$ ls  
data.txt  
bandit10@bandit:~$ base64 data.txt  
VkdobElIQmhjM04zYjNKa0lHbHpJRWxHZFd0M1MwZHpSbGM0VFU5eE0wbFNSbkZ5ZUVVeGFIaFVU  
a1ZpVlZCU0NnPT0K
bandit10@bandit:~$ base64 data.txt --decode  
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR