## Level Goal

The password for the next level is stored **somewhere on the server** and has all of the following properties:

-   owned by user bandit7
-   owned by group bandit6
-   33 bytes in size

## Commands you may need to solve this level

ls, cd, cat, file, du, find, grep

find -user for owned by user
eg. find -user bandit7

find -user for owned by user
eg. find -group bandit6

find -size c for bytes
eg. find -size 33c

bandit6@bandit:~$ ls  
bandit6@bandit:~$ ls -a  
. .. .bash_logout  .bashrc  .profile  
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c  
find: ‘/root’: Permission denied  
find: ‘/home/bandit28-git’: Permission denied  
find: ‘/home/bandit30-git’: Permission denied  
find: ‘/home/bandit5/inhere’: Permission denied  
find: ‘/home/bandit27-git’: Permission denied  
find: ‘/home/bandit29-git’: Permission denied  
find: ‘/home/bandit31-git’: Permission denied  
find: ‘/lost+found’: Permission denied  
find: ‘/etc/ssl/private’: Permission denied  
find: ‘/etc/polkit-1/localauthority’: Permission denied  
find: ‘/etc/lvm/archive’: Permission denied  
find: ‘/etc/lvm/backup’: Permission denied  
find: ‘/sys/fs/pstore’: Permission denied  
find: ‘/proc/tty/driver’: Permission denied  
find: ‘/proc/4566/task/4566/fd/6’: No such file or directory  
find: ‘/proc/4566/task/4566/fdinfo/6’: No such file or directory  
find: ‘/proc/4566/fd/5’: No such file or directory  
find: ‘/proc/4566/fdinfo/5’: No such file or directory  
find: ‘/cgroup2/csessions’: Permission denied  
find: ‘/boot/lost+found’: Permission denied  
find: ‘/tmp’: Permission denied  
find: ‘/run/lvm’: Permission denied  
find: ‘/run/screen/S-bandit0’: Permission denied  
find: ‘/run/screen/S-bandit25’: Permission denied  
find: ‘/run/screen/S-bandit30’: Permission denied  
find: ‘/run/screen/S-bandit9’: Permission denied  
find: ‘/run/screen/S-bandit28’: Permission denied  
find: ‘/run/screen/S-bandit18’: Permission denied  
find: ‘/run/screen/S-bandit20’: Permission denied  
find: ‘/run/screen/S-bandit12’: Permission denied  
find: ‘/run/screen/S-bandit5’: Permission denied  
find: ‘/run/screen/S-bandit7’: Permission denied  
find: ‘/run/screen/S-bandit16’: Permission denied  
find: ‘/run/screen/S-bandit26’: Permission denied  
find: ‘/run/screen/S-bandit8’: Permission denied  
find: ‘/run/screen/S-bandit15’: Permission denied  
find: ‘/run/screen/S-bandit4’: Permission denied  
find: ‘/run/screen/S-bandit3’: Permission denied  
find: ‘/run/screen/S-bandit19’: Permission denied  
find: ‘/run/screen/S-bandit31’: Permission denied  
find: ‘/run/screen/S-bandit17’: Permission denied  
find: ‘/run/screen/S-bandit22’: Permission denied  
find: ‘/run/screen/S-bandit21’: Permission denied  
find: ‘/run/screen/S-bandit14’: Permission denied  
find: ‘/run/screen/S-bandit13’: Permission denied  
find: ‘/run/screen/S-bandit24’: Permission denied  
find: ‘/run/screen/S-bandit23’: Permission denied  
find: ‘/run/shm’: Permission denied  
find: ‘/run/lock/lvm’: Permission denied  
find: ‘/var/spool/bandit24’: Permission denied  
find: ‘/var/spool/cron/crontabs’: Permission denied  
find: ‘/var/spool/rsyslog’: Permission denied  
find: ‘/var/tmp’: Permission denied  
find: ‘/var/lib/apt/lists/partial’: Permission denied  
find: ‘/var/lib/polkit-1’: Permission denied  
/var/lib/dpkg/info/bandit7.password  
find: ‘/var/log’: Permission denied  
find: ‘/var/cache/apt/archives/partial’: Permission denied  
find: ‘/var/cache/ldconfig’: Permission denied


use  2>/dev/null to clean up errors and Permission denied
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null  
/var/lib/dpkg/info/bandit7.password  
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password  
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs