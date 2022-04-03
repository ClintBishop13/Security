The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

-   human-readable
-   1033 bytes in size
-   not executable

## Commands you may need to solve this level

ls, cd, cat, file, du, find

find -size c for bytes
eg. find -size 1033c

-type for file type
-type f for human readable
eg. find -type f

-executable for executible files
!-executable to turn false
eg. find ! -executable

bandit5@bandit:~$ ls  
inhere  
bandit5@bandit:~$ cd inhere  
bandit5@bandit:~/inhere$ find -size 1033c -type f ! -executable  
./maybehere07/.file2  
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2  
DXjZPULLxYr17uwoI01bNLQbtFemEgo7


