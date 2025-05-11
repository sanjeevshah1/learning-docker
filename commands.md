## List the running containers or processes 
``` bash
docker ps
```

## List the running containers or processes (Stopped Containers as well)
``` bash
docker ps -a
```

## Run or pull a image
``` bash
docker pull ubuntu
```

## Run a image interactively
```bash
docker run -it ubuntu 
```

## Start a container
``` bash
docker run <image-tag>
```

## Build an image
``` bash
docker build -t <image-tag> .
```

##History Command for Linux
``` bash
history
```

This returns a history of linux commands we entered previously

To run a command from history, 
``` bash
![history number]
```

To update the package database:
``` bash
apt update
```

To install the package:
``` bash
apt install <package-name>
```

To uninstall the package:
``` bash
apt remove <package-name>
```

### List
``` bash
ls
```
It displays the list of files and directories in current working directory/

### List `1 item per line`
``` bash
ls -1
```

### List `Long Listing`
``` bash
ls -l
```
It includes more details.

### Change working directory
``` bash
cd [target directory]
```

### Change working directory to `Home Directory`
``` bash
cd ~
```

To make a directory:
``` bash
mkdir [directory-name]
```

To rename a directory (Use move command):
``` bash
mv [directory-name] [new-directory-name]
```

To create a file:
``` bash
touch [filename].[extension]
```

To rename a file:
``` bash
mv [old name] [new name]
```

To delte a file:
``` bash
rm [filename]
```

To delte multiple files
``` bash
rm [file1] [file2] [file3] ...[fileN]
```

To create multiple files (chain multiple files):
``` bash
touch [file1] [file2] [file3] ...[fileN]
```


To delte a directory
``` bash
rm -rf [directory name]
```

To edit a file using nano
``` bash
nano [filename]
```

To view the contents of a file (only useful when the file is small)
``` bash
cat [filename]
```

For larger files
``` bash
more [filename]
```
OR
``` bash
less [filename]
```

For displaying the first few lines of a file
``` bash
head -n [number of lines] [filename]
```

For displaying the last few lines of a file
``` bash
tail -n [number of lines] [filename]
```

Redirection operator like `>` to redirect.
``` bash
cat [filename] > [another filename]
```

Combination of `cat` command and `>` operator the combine multiple files into a file.
``` bash
cat [file1] [file2] [file3] ...[fileN] > [another filename]
```

Redirection operator `>` can work with `echo` command as well.
``` bash
echo [filename] > [another filename]
```

Search for text `hello` in a file named `test.txt`, we write the command:
``` bash
grep hello test.txt
```

Case insensitive search
``` bash
grep -i hello test.txt
```

Search in multiple files using a single command.
``` bash
grep -i hello test1.txt test2.txt
```

Search in directories
``` bash
grep -i -r <directory path>
```
OR
``` bash
grep -ir <directory path>
```

Find
``` bash
find
```

To only find the directories:-
``` bash
find -type d
```

To only find the files:-
``` bash
find -type f
```

To chain commands using `;`
``` bash
mkdir test-directory ; cd test-directory; echo testing
```

To chain commands using `&&`
``` bash
mkdir test-directory && cd test-directory && echo testing
```

To chain commands using `||`
``` bash
mkdir test-directory || cd test-directory || echo testing
```

Piping `|`

In piping, succesive ouput of each command in chain is feeded as input to next command.
``` bash
ls /bin | head -n 5
```

To see all the environment variables in the machine, we can use the command : `printenv`.
``` bash
printenv
```
To see value of a particular environemnt variable,
``` bash
printenv <variable>
```
OR
``` bash
echo $<variable>
```

To see all the running processes, we use the `ps` command.
``` bash
ps
```
To kill a process, we use the `kill` command.
``` bash
kill <PID>
```

To add a user
``` bash
useradd -m <username>
```

The users are stored in `/etc/passwd`. To see the users, use
``` bash
cat /etc/passwd
```

To start a docker container, and log in as a user we use the commmand,
``` bash
docker exec -it -u <username> <container-id> bash
```

To delete a user
``` bash
userdel <username>
```

A newer and more interactive version of the `useradd` command is available. It's `adduser`. 

``` bash
adduser <username>
```
To add a group
``` bash
groupadd <groupname>
```

The groups are stored in `/etc/group`. To see the groups, use
``` bash
cat /etc/group
```

To assign users to supplementary groups, we use the command:
``` bash
usermod -G <groupname> <username>
```

To see which groups a user is part of, use the command:
``` bash
groups <username>
```

To see the file permissions of a file, use the command:
``` bash
ls -l <file>
```

To add the execute permission for the owner of the file, use the command:
``` bash
chmod u+x <file>
```


