The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## Commands you may need to solve this level

[ls], [cd], [cat], [file], [du], [find]

eg. bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1

e.g. bandit0@bandit:~$ find readme  
readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1


bandit0@bandit:~$ logout  
Connection to bandit.labs.overthewire.org closed.  
(base) [clintb@clint-ms7b85 ~]$ ssh bandit.labs.overthewire.org -p 2220 -l bandit1
