## Linux ls command options

The **ls** is the list command in Linux. It will show the full list or content of your directory. Just type _ls_ and press the enter key. The whole content will be shown.

ls option

Description

[ls -a](https://www.javatpoint.com/linux-ls#linux-ls-a)

In Linux, hidden files start with . (dot) symbol and they are not visible in the regular directory. The (ls -a) command will enlist the whole list of the current directory including the hidden files.

[ls -l](https://www.javatpoint.com/linux-ls#linux-ls-l)

It will show the list in a long list format.

ls -lh

This command will show you the file sizes in human readable format. Size of the file is very difficult to read when displayed in terms of byte. The (ls -lh)command will give you the data in terms of Mb, Gb, Tb, etc.

ls -lhS

If you want to display your files in descending order (highest at the top) according to their size, then you can use (ls -lhS) command.

[ls -l - -block-size=[SIZE]](https://www.javatpoint.com/linux-ls#linux-ls-l-block-size)

It is used to display the files in a specific size format. Here, in [SIZE] you can assign size according to your requirement.

[ls -d */](https://www.javatpoint.com/linux-ls#linux-ls-d-asterisk-slash)

It is used to display only subdirectories.

[ls -g or ls -lG](https://www.javatpoint.com/linux-ls#linux-ls-g)

With this you can exclude column of group information and owner.

ls -n

It is used to print group ID and owner ID instead of their names.

[ls --color=[VALUE]](https://www.javatpoint.com/linux-ls#linux-ls-color)

This command is used to print list as colored or discolored.

ls -li

This command prints the index number if file is in the first column.

ls -p

It is used to identify the directory easily by marking the directories with a slash (/) line sign.

ls -r

It is used to print the list in reverse order.

ls -R

It will display the content of the sub-directories also.

ls -lX

It will group the files with same extensions together in the list.

ls -lt

It will sort the list by displaying recently modified filed at top.

[ls ~](https://www.javatpoint.com/linux-ls#linux-ls-tilde)

It gives the contents of home directory.

[ls ../](https://www.javatpoint.com/linux-ls#linux-ls-dot-dot-slash)

It give the contents of parent directory.

ls --version

It checks the version of ls command.