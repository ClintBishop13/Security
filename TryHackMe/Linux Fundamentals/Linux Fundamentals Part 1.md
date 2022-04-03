- A Bit of Background on Linux
Research: What year was the first release of a Linux operating system?
1991

- Running Your First few Commands
If we wanted to output the text "**TryHackMe**", what would our command be?
$ echo TryHackMe
What is the username of who you're logged in as on your deployed Linux machine?
$ whoami
tryhackme

- Interacting With the Filesystem
On the Linux machine that you deploy, how many folders are there?
$ ls 
4
Which directory contains a file?
folder4
What is the contents of this file?
$ cat note.txt
Hello World!
Use the cd command to navigate to this file and find out the new current working directory. What is the path?
$ pwd
/home/tryhackme/folder4

- Searching for Files
  Use grep on "access.log" to find the flag that has a prefix of "THM". What is the flag?
  THM{ACCESS}
  
-  An Introduction to Shell Operators
If we wanted to run a command in the background, what operator would we want to use?
&
If I wanted to replace the contents of a file named "passwords" with the word "password123", what would my command be?
$ echo pasword123 > passwords
Now if I wanted to add "tryhackme" to this file named "passwords" but also keep "passwords123", what would my command be
echo tryhackme >> passwords