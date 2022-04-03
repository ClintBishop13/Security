- Accessing Your Linux Machine Using SSH (Deploy)
ssh tryhackme@10.10.11.212

- Introduction to Flags and Switches  
What directional arrow key would we use to navigate down the manual page?  
down
What flag would we use to display the output in a "human-readable" way?
-h

- Filesystem Interaction Continued
How would you create the file named "newnote"?
 $ touch newnote
On the deployable machine, what is the file type of "unknown1" in "tryhackme's" home directory?
   ASCII text
How would we move the file "myfile" to the directory "myfolder"
   mv myfile myfolder
What are the contents of this file?
   THM{FILESYSTEM}
   
 - Permissions 101
On the deployable machine, who is the owner of "important"?
user2
Now switch to this user "user2" using the password "user2"
$ su user2
Output the contents of "important", what is the flag?
THM{SU_USER2}

 - Common Directories
What is the directory path that would we expect logs to be stored in?  
/var/log
What root directory is similar to how RAM on a computer works?  
/tmp
Name the home directory of the root user
/root