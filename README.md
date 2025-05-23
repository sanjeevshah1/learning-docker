<ul>Day 1:</ul> 

# <p align = "center">Introduction to Docker</p>

`Docker` is a platform for building, running and shipping applications in a consistent manner so that if a application is running in our machine, it can run and function the same say in other machines.

During `software development`, there frequently comes a situation where a software  `runs in our machine` but it `doesn't work on other's machines`. There can be three reasons for such situation. They are: 

1. **One or more files are missing during sharing and deployment.**
2. **Software version mismatch between source and target machines.**
3. **Different configuration settings like environment variables are different across the machines.**

Docker saves us from the problems arising with these issues. It packages everything we need to run a application into a `package`. We can share and run this package everywhere. 

## Virtual Machines vs Container

A `container` is a `isolated environment` for running an application.
A `virtual Machine` is a abstraction of a machine (`physical hardware`). So, we can run several virtual machines in a real physical machine. For example, in a real Mac physical machine, we can run two virtual machines. One, running Windows and other running Linux. We do that with the help of "`Hypervisor`".

A `hypervisor` is a software we use to `create & manage virtual machines`. Some examples of hypervisor are `VMware` and `VirtualBox`. They are `cross-platform`, so they can run on Windows, MacOS and Linux. Another example is `Hyper-v` which works on `Windows only`.

With virtual machines, we can run applications in isolated environments (virtual machines). For example, in a real machine (Bare Metal) we initialise two Virtual Machines, each running different applications, and the applications may have different dependencies. For example , in a virtual machine an app may need Node version 9 while in another virtual machine the app may need Node version 10. 

`Problems` of Virtual Machines are :-
1. **Each VM needs a full blown OS.**
2. **Slow to start.**
3. **Resource intensive. (If we have 8GB RAM on real machine, we have to share and divide it between Virtual Machines)**


Now, talking about containers,
The `containers` provide us the same kind of `isolation` so that the apps can run in `isolated environment`. Containers are `lightweight`, they don't need a `full blown OS`. They use the single OS of the host, and since the OS is already started on the real machine, the containers `start up pretty quickly`. 

In summary, the advantages of Containes over Virtual Machines are :-
1. **Are lightweight.**
2. **Use OS of the host.**
3. **Start quickly.**
4. **Need less hardware resources.**


## Architecture of Docker :-

Docker has a `client-server architecture`. So it has a client talking with server using `RESTful APIs`. The `server` is also known as `Docker Engine`.
Technically, the containers are just `processes` like other processes running in our computers. As mentioned earlier, all containers share the same OS of the host. Specifically they `share` the `kernel` of the host.

What's kernel of the host OS?

`Kernel` is the `core of the OS`. It's like the engine of a car. It's the part of OS which manages `applications and hardware resources` like memory and CPU. Every Operating System has its own Kernel. These kernels have `different APIs`. So, we can't run a windows application on a Linux machine. So, on a linux machine we can only run Linux containers. However, in a `Windows machine`, we can run `both Windows Container and Linux Container` because Windows 10 is now shipped witha `custom built Linux kernel`. This is an addition to a Windows Kernel that has always been in a Windows OS. It's not an replacement. 

Talking about MacOs, it has its own Kernel which is different from Linux and Windows Kernels. It does `not have native support` for containers. So Docker on mac uses a `light weight Linux VM` to enable containers.


## Development Workflow with Docker.
To start off, we take an `application` (type of application doesn't matter) and dockerize it. To `dockerize`, we just add a Dockerfile to it. A `Dockerfile` is plaintext file that docker uses to package an application into a `Docker Image`.

A docker image contains everything our application needs to run. A docker image contains :-
1. **A cut-down OS.**
2. **A run-time environment.** (For eg. Node)
3. **Application files.**
4. **Third party libraries.**
5. **Environment variables.**
6. **and so on,**

Once we have a image, we tell docker to `start a container` using that image. A container is a special kind of process because it has its own "`file system`". 
Once we have a image, we can push it inside a `docker registry` like `docker hub`. A docker hub to docker is like github to git. Once our image is in docker hub, we can pull image from there into any machine we want to run.

## Dockerfile Introduction

A `Dockerfile` is a text file that contains a set of instructions to create a Docker image. Each instruction tells Docker how to build the image step-by-step.

### Example Dockerfile

```Dockerfile
FROM node:alpine           # Use a lightweight Node.js base image
COPY . /app                # Copy all files from the current directory to /app in the image
WORKDIR /app              # Set /app as the working directory
CMD node app.js           # Run the app using Node.js
```

### Explanation

FROM specifies the base image (here, a small Node.js Alpine image).

COPY copies the app code into the container.

WORKDIR sets the working directory inside the container.

CMD defines the default command to run when the container starts.

### To Build and Run the Container

#### Build the Docker Image
```bash
docker build -t my-node-app .
```

#### Run the Container
```bash
docker run my-node-app
```

#### Alternative: Run with Interactive Terminal
```bash
docker run -it my-node-app
```



# <p align="center">The Linux Command Line</p>
## Linux Distributions

Linux is open-source software, and over time, many individuals and communities have created their own versions of Linux, commonly known as `Linux Distributions` or `Distros`. These distributions are tailored to meet specific needs, such as running servers, desktop computers, mobile phones, and more.

### Popular Linux Distributions:

- **Ubuntu**  
- **Debian**  
- **Alpine**  
- **Fedora**  
- **CentOS**

... and there are **more than 1000** Linux distros available, each designed for different purposes!

### Why so many distros?  
Each distro serves a unique purpose and comes with different default tools, package managers, and system optimizations. Whether you're a developer, sysadmin, or casual user, there's a Linux distribution designed specifically for your needs.

From lightweight systems like **Alpine** to more user-friendly options like **Ubuntu**, the Linux ecosystem offers endless customization and flexibility! 🌍💻

Most of these distributions support almost same set of commands. But, there might be some differences sometimes.

## Running Linux

Steps: 
1. Go to hub.docker.com
2. Search for a linux distro image. (For eg: Ubuntu)
3. Copy the command to pull a image to our machine. (Docker pull ubuntu or Docker run ubuntu)
    If we do this, an container will run and close immediately because we didn't interact with it.

To interact with a container,
``` bash
docker run -it ubuntu
```

Doing this, a shell (terminal) will open. Shell takes an command and passes it to OS for execution.

root@bb7c31ed999c:/# This is called Shell Prompt.

Let's break it down into following parts.
- **"root" represents the currently logged in user. Be default, we've here logged in as root user who has the highest priviliges.**
- **"bb7c31ed999c" is the name of the machine. In this case, the id of container in which the linux is running.**
- **"/" represents where we are at the file system.**
- **"#" represents highest priviliges.**

## Managing Packages

For ubuntu, the package manager is "apt". The **Advanced Package Tool**. 

Before installing a package, always use the command
``` bash
apt update
```
first to update the package database.

Then use the command
``` bash
apt install <package-name>
```
to install the package.

## Linux File System

Just like windows, in Linux, the files & directories are stored in tree-like hierarachical structure.

In windows, we have hierarchical file structure like: 

##  `/C:\`

##  `/Program Files`

##  `/Windows`s

In Linux, **everything is a file** — including hardware devices, directories, and even processes. The Linux file system is hierarchical, starting from the root directory `/`.

## `/` - Root Directory
- The top-level directory in Linux.
- All other directories and files stem from here.
- Only root has full access to everything here.

---

## `/bin` - Essential User Binaries
- Contains essential binary executables needed for system boot and basic operations.
- Examples: `ls`, `cp`, `mv`, `cat`, `bash`.

---

## `/boot` - Boot Loader Files
- Contains files required for booting the system.
- Includes the Linux kernel (`vmlinuz`), initial RAM disk (`initrd`), and bootloader config files like `grub`.

---

## `/dev` - Device Files
- Contains device files representing hardware devices.
- Example: `/dev/sda` for hard drives, `/dev/tty` for terminals.
- These files provide a way for software to interact with hardware.

---

## `/etc` - Configuration Files
- Contains all system-wide configuration files and shell scripts.
- Examples: `/etc/passwd`, `/etc/fstab`, `/etc/hostname`.

---

## `/home` - User Home Directories
- Each user has a personal directory here, like `/home/ram`.
- Contains user files, documents, downloads, and personal configs.

---

## `/root` - Root User's Home
- Home directory for the superuser (root).
- Separate from `/home` for security and system integrity.

---

## `/lib` - Essential Shared Libraries
- Stores shared libraries (.so files) needed to boot the system and run commands in `/bin` and `/sbin`.
- Also contains kernel modules in subdirectories like `/lib/modules`.

---

## `/proc` - Process and Kernel Info
- A virtual filesystem that provides a view into the kernel and running processes.
- Each process has a directory like `/proc/1234`, where 1234 is the PID.
- Also includes system information like `/proc/cpuinfo` and `/proc/meminfo`.

---

> **Note**: This is only a subset of the full Linux file system hierarchy. Other important directories include `/sbin`, `/usr`, `/var`, `/tmp`, etc.

## Navigating the File System

For navigating the linux file system, some of the commands are:

### Present Working Directory
```
pwd
```
It displays where we are currently in the file system.

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

## Manipulating Files and Directories

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

## Editing and Viewing Files

We can use vim or nano or other text editors to edit files.

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

## Redirection
One of the standard concepts of linux is the concept of standard input and output. Standard Input means keyboard & Standard output means screen.
We can change the source of input and output. This is known as `Redirection`.

To do that we can use redirection operator like `>` to redirect.
For eg: 
``` bash
cat [filename] > [another filename]
```

This `>` operator redirects the output of `filename` from screen to `another filename`.

Now, we can use the combination of `cat` command and `>` operator the combine multiple files into a file.
``` bash
cat [file1] [file2] [file3] ...[fileN] > [another filename]
```

Similarly, the redirection operator `>` can work with `echo` command as well.
``` bash
echo [filename] > [another filename]
```
### Searching for Text

To search for text, we use the `grep` command. It stands for `Global Regular Expression Print`.
To search for text `hello` in a file named `test.txt`, we write the command:
``` bash
grep hello test.txt
``` 
But, this is case sensitive. So, if there is `Hello` in `test.txt` it won't be matched with `hello`. To make it case insenitive, we have to add the flag -i to the command.
``` bash
grep -i hello test.txt
```

We can also search in multiple files using a single command.
``` bash
grep -i hello test1.txt test2.txt
```

We can also search in directories
``` bash
grep -i -r <directory path>
```
OR
``` bash
grep -ir <directory path>
```

## Finding Files and Directories

In linux, the find files & directories, we use the `find` command. If we execute the `find` command without any argument, we see all the files and directories in the current working directory `pwd`. 
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

## Chaining Commands

In linux, there are different ways of `chaining or combining` multiple commands. 
One such way is using `;` to separate commands in a single line then hitting `Enter`.
``` bash
mkdir test-directory ; cd test-directory ; echo testing
```
If some of the commands in chain fail, other commands still execute.

To make it like if one command fails, other commands following stop executing operation, we use the `&&` operator instead of `;` operator.
``` bash
echo hi  && mkdir test-directory &&  echo testing
```

We also have a or chaining schema in which we use `||`.
``` bash
mkdir test-directory ||  echo testing
```
Here, if first command succeeds, then second command doesn't execute. But, if first command fails, then second command executes.

Another of way of chaining commands is using `Piping` => `|`.
In piping, succesive ouput of each command in chain is feeded as input to next command.
``` bash
ls /bin | head -n 5
```

## Environment Variables
Just like we've `variables` in `programming languages` where we can set and store values, we have `environment variables` in Linux where can set and store `configuration settings` for our applications. Our applications can read configuration settings from these environment variables. For eg: we can set `Port Number` for our node js backend inside a environment variable.

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

To set a environment variable, we use the `export` command. This saves the environment variable in current terminal session only. If we close this terminal session, and open a new terminal session, this environment variable will not exist.
``` bash
export <variable>=<value>
```

To permanently store environment variables, we have to write it into `.bashrc` file.
``` bash
cd / ; echo DB_USER=Ram >> .bashrc
```
> Even though `.bashrc` has `DB_USER=RAM`, it hasn't been sourced yet in the current shell session. .bashrc is not automatically executed in `non-interactive` or `non-login shells` (which Docker usually starts with).  To fix this and load the variable, run:
``` bash
source .bashrc
```
Then
``` bash
echo $DB_USER
```

## Managing Processes
A process is the `instance` of a running program. To see all the running processes, we use the `ps` command.
``` bash
ps
```

To kill a process, we use the `kill` command.
``` bash
kill <PID>
```
## Managing Users
In linux we have the commands `useradd`, `usermod`, and, `userdel` for `adding`, `modifying`, and , `deleting` a user.

To add a user
``` bash
useradd -m <username>
```

The users are stored in `/etc/passwd`. To see the users, use
``` bash
cat /etc/passwd
```
To modify the user using `usermod`, let's modify the default shell when user logs in.
``` bash
usermod -s /bin/bash <username>
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
It automatically creates a group with name of username and places the newly created user in the group, creates a home directory, and asks for password.
``` bash
root@970b0b05e309:/# adduser ram
info: Adding user `ram' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group `ram' (1001) ...
info: Adding new user `ram' (1001) with group `ram (1001)' ...
warn: The home directory `/home/ram' already exists.  Not touching this directory.
New password:
```
## Managing Groups

In linux we have the commands `groupadd`, `groupmod`, and, `groupdel` for `adding`, `modifying`, and , `deleting` a group.

To add a group
``` bash
groupadd <groupname>
```

The groups are stored in `/etc/group`. To see the groups, use
``` bash
cat /etc/group
```
> In linux every user has a `primary` group and 0 or more `Supplementary groups`

A user is assigned to a `primary group` of name same as of user's name when the user is created.

To assign users to supplementary groups, we use the command:
``` bash
usermod -G <groupname> <username>
```

To see which groups a user is part of, use the command:
``` bash
groups <username>
```

## File Permissions
To see the file permissions of a file, use the command:
``` bash
ls -l <file>
```
-rw-r--r-- 

The order for permission is `read, write and execute`.
This is an example of file permissions on a file. It consists of 9 letters divided into `three units or parts`. 

- **First part represents the permissions for user who `owns` this file.**
- **Second part represents the permissions for group who `owns` this file.**
- **Third part represents the permissions for everyone else.**

Here, in this example, in the first part, `user who owns the file`, we have read and write permission but don't have execute permission.

To change the permissions on a file, we use the `chmod` command with tags `u`, or `g` or, `o` for ``users`, or `groups`, or `others`.

To add the execute permission for the owner of the file, use the command:
``` bash
chmod u+x <file>
```

<ul>Day 2</ul>

# <p align = "center">Building Images</p>

## Images and Containers

An `image` contains everything an applications need to run and operate. A docker image contains :-
1. **A cut-down OS.**
2. **A run-time environment.** (For eg. Node)
3. **Application files.**
4. **Third party libraries.**
5. **Environment variables.**
6. **and so on,**

Once, we have a image, we can start a `container` from it. A container is like a `virtual machine` in a sense that it provides an `isolated environment` to run an application. Similar to virtual machines, it can be stopped and restarted. A container is a special type of `process` of `Operating System`. It's `special` because it has its own `file system` provided by the `image`. 

To start a container from an image,
``` bash
docker run -it <image>
```

## Sample Web Application

Here, let's `dockerize !!!` an front-end application built with `React`. 

## Dockerfile Instructions

The first step to `dockerize` an application is to add a `Dockerfile` to it.

A Dockerfile contains a set of instructions for building an image. The various instructions available are :-

- **`FROM`**
        
        It specifies the base image for building an image. For eg: A base `node` image to build an image of a node application.
        
- **`WORKDIR`**
        
        It specifies the working directory. Once we specify a `WORKDIR` all the following commands will be executed inside the working directory.
        
- **`COPY`** & **`ADD`**
        
        They are used for copying files and directories.

- **`RUN`**
        
        It's used to execute operating system commands.

- **`ENV`**
        
        It's used to set environment variables.

- **`EXPOSE`**
        
        It's used to tell the docker that our container is starting in the given port.

- **`USER`**
        
        It specifies the user who should run the application.

- **`CMD`** & **`ENTRYPOINT`**
        
        They specify the command that should be executed when we start the container.


## Choosing the Right Base Image
Let's start by adding a `Dockerfile` to the sample project `Front-End-Application`.

The first instruction we write in Dockerfile is `FROM`, it specifies the base image on top of which the docker image should be built on. The base image can be a `OS` like `LINUX`, `MAC` OR `WINDOWS`. It can also be a `OS + Runtime Environment`

Now, to build the docker image. we hit the command:
``` bash
docker build -t <image tag> .
```

To run the image,
``` bash
docker run -it <image tag>
```

To run the image with shell session,
``` bash
docker run -it <image tag> sh
```

To run the image with bash session,
``` bash
docker run -it <image tag> bash
```

## Copying Files and Directories
Now that we have the base image, the next step is to copy the necessary application files to the docker image. We do that using `COPY` or `ADD` instruction.

### `COPY instruction`
To copy the package.json and README.md file to image,
we use the instruction:
``` DOCKER
COPY package.json README.md /app/
```
in the Dockerfile

To set the working directory,
``` DOCKER
WORKDIR /app
```
To all files and directories in working directory to image,
we use the instruction:
``` DOCKER
COPY . /app/
```
`OR`

``` DOCKER
COPY . .
```

For the case where file name consistes of space in between, we use the other form of `COPY` instruction.
``` DOCKER
COPY ["hello world.txt","."]
```

### `ADD instruction`
Now, talking about the `ADD` instruction, it provides us some additional features. 

One such feature is, it lets us add files from a url into a directory.
``` DOCKER
ADD <url> .
```

Another feature is, it automatically de-compresses a compressed file <`zip`> into a directory then copy to the specified directory.
``` DOCKER
ADD <zip> .
```
## Excluding Files and Directories
## Running Commands
## Setting Environment Variables
## Exposing Ports
## Defining Entrypoints
## Speeding Up Builds
## Removing Images
## Tagging Images
## Sharing Images
## Saving and Loading Images


# <p align = "center">Working with Containers</p>
# <p align = "center">Running Multi-container Applications</p>
# <p align = "center">Deploying Applications</p>