- Terminal Text Editors
Edit "task3" located in "tryhackme"'s home directory using Nano. What is the flag?
THM{TEXT_EDITORS}

- General/Useful Utilities
Download the file [http://10.10.138.103:8000/.flag.txt](http://10.10.138.103:8000/.flag.txt)[](https://assets.tryhackme.com/additional/linux-fundamentals/part3/flag.txt) onto the TryHackMe AttackBox[](https://assets.tryhackme.com/additional/linux-fundamentals/part3/flag.txt)
What are the contents?
THM{WGET_WEBSERVER}

- Processes 101
  If we were to launch a process where the previous ID was "300", what would the ID of this new process be?
  301
  If we wanted to **cleanly** kill a process, what signal would we send it?
  SIGTERM
  Locate the process that is running on the deployed instance (10.10.138.103). What flag is given?
  ps aux | grep THM
What command would we use to stop the service "myservice"?
systemctl Stop myservice
 What command would we use to start the same service on the boot-up of the system?
 systemctl enable myservice  
What command would we use to bring a previously backgrounded process back to the foreground?
fg