## Level Goal

The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Commands you may need to solve this level

grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir, cp, mv, file

## Helpful Reading Material

-   [Hex dump on Wikipedia](https://en.wikipedia.org/wiki/Hex_dump)]

bandit12@bandit:~$ mkdir /tmp/clint  
bandit12@bandit:~$ ls  
data.txt  
bandit12@bandit:~$ cd /tmp/clint  
bandit12@bandit:/tmp/clint$ cp ~/data.txt /tmp/clint/  
bandit12@bandit:/tmp/clint$ ls  
data.txt  
bandit12@bandit:/tmp/clint$ mv data.txt hex
bandit12@bandit:/tmp/clint$ ls  
hex
bandit12@bandit:/tmp/clint$ xxd -r data.txt > hex  
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex  
bandit12@bandit:/tmp/clint$ file hex  
hex: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, f  
rom Unix  
bandit12@bandit:/tmp/clint$ mv hex hex.gz
bandit12@bandit:/tmp/clint$ gzip -d hex.gz
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex
bandit12@bandit:/tmp/clint$ file hex  
hex: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/clint$ mv hex hex.bz2
bandit12@bandit:/tmp/clint$ bzip2 -d hex.bz2  
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex
bandit12@bandit:/tmp/clint$ file hex  
hex: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, f  
rom Unix
andit12@bandit:/tmp/clint$ mv hex hex.gz   
bandit12@bandit:/tmp/clint$ gzip -d hex   
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex  
bandit12@bandit:/tmp/clint$ file hex  
hex: POSIX tar archive (GNU)
bandit12@bandit:/tmp/clint$ mv hex hex.tar  
bandit12@bandit:/tmp/clint$ tar xf hex.tar   
bandit12@bandit:/tmp/clint$ ls  
data5.bin  data.txt  hex.tar  
bandit12@bandit:/tmp/clint$ file data5.bin  
data5.bin: POSIX tar archive (GNU)  
bandit12@bandit:/tmp/clint$ rm hex.tar  
bandit12@bandit:/tmp/clint$ mv data5.bin hex.tar  
bandit12@bandit:/tmp/clint$ tar xf hex.tar  
bandit12@bandit:/tmp/clint$ ls  
data6.bin  data.txt  hex.tar  
bandit12@bandit:/tmp/clint$ file data6.bin  
data6.bin: bzip2 compressed data, block size = 900k  
bandit12@bandit:/tmp/clint$ rm hex.tar   
bandit12@bandit:/tmp/clint$ mv data6.bin hex.bz2   
bandit12@bandit:/tmp/clint$ bzip2 -d hex.bz2   
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex
bandit12@bandit:/tmp/clint$ mv hex hex.gz  
bandit12@bandit:/tmp/clint$ gzip -d hex  
bandit12@bandit:/tmp/clint$ mv hex hex.tar  
bandit12@bandit:/tmp/clint$ tar xf hex.tar  
bandit12@bandit:/tmp/clint$ ls  
data5.bin  data.txt  hex.tar  
bandit12@bandit:/tmp/clint$ rm hex.tar  
bandit12@bandit:/tmp/clint$ mv data5.bin hex.tar  
bandit12@bandit:/tmp/clint$ tar xf hex.tar  
bandit12@bandit:/tmp/clint$ rm hex.tar  
bandit12@bandit:/tmp/clint$ mv data6.bin hex.bz2  
bandit12@bandit:/tmp/clint$ bzip2 -d hex.bz2  
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex  
bandit12@bandit:/tmp/clint$ file hex  
hex: POSIX tar archive (GNU)  
bandit12@bandit:/tmp/clint$ mv hex hex.tar  
bandit12@bandit:/tmp/clint$ tar xf hex.tar  
bandit12@bandit:/tmp/clint$ ls  
data8.bin  data.txt  hex.tar  
bandit12@bandit:/tmp/clint$ file data8.bin  
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compress  
ion, from Unix  
bandit12@bandit:/tmp/clint$ rm hex.tar
bandit12@bandit:/tmp/clint$ mv data8.bin hex.gz  
bandit12@bandit:/tmp/clint$ gzip -d hex.gz   
bandit12@bandit:/tmp/clint$ ls  
data.txt  hex  
bandit12@bandit:/tmp/clint$ file hex  
hex: ASCII text  
bandit12@bandit:/tmp/clint$ cat hex  
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL