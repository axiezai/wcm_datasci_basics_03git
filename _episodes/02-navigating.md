---
title: "Navigating the shell"
teaching: 10 
exerises: 0
questions: 
- "How to navigate your computer in the shell"
objectives:
- "Begin navigating the shell"
- "Understand file permissions" 
keypoints:
- "Use `cd` and `ls` to navigate your file system"
- "Files have permissions indicated by `rwx`"
- "`mv`, `cp`, and `mkdir` are useful programs"
- "Check a program's usage with `man`"
---

## Navigating the shell
A path on the shell is a delimited list of directories; separated by `/` on Linux and macOS and `\` on Windows. On Linux and macOS, the path `/` is the “root” of the file system, under which all directories and files lie, whereas on Windows there is one root for each disk partition (e.g., `C:\`). We will generally assume that you are using a Linux filesystem in this class. A path that starts with `/` is called an absolute path. Any other path is a relative path. Relative paths are relative to the current working directory, which we can see with the `pwd` command and change with the `cd` command. In a path, `.` refers to the current directory, and `..` to its parent directory:

~~~
ludus:~$ pwd
/home/ludus
ludus:~$ cd /home
ludus:/home$ pwd
/home
ludus:/home$ cd ..
ludus:/$ pwd
/
ludus:/$ cd ./home
ludus:/home$ pwd
/home
ludus:/home$ cd ludus
ludus:~$ pwd
/home/ludus
ludus:~$ ../../bin/echo hello
hello
~~~
{: .bash}

Notice that our shell prompt kept us informed about what our current working directory was. You can configure your prompt to show you all sorts of useful information, which we will cover in a later lecture.

In general, when we run a program, it will operate in the current directory unless we tell it otherwise. For example, it will usually search for files there, and create new files there if it needs to.

To see what lives in a given directory, we use the `ls` command:

~~~
ludus:~$ ls
ludus:~$ cd ..
ludus:/home$ ls
ludus
ludus:/home$ cd ..
ludus:/$ ls
bin
boot
dev
etc
home
...
~~~
{: .bash}

Unless a directory is given as its first argument, `ls` will print the contents of the current directory. Most commands accept flags and options (flags with values) that start with `-` to modify their behavior. Usually, running a program with the `-h` or `--help` flag will print some help text that tells you what flags and options are available. For example, `ls --help` tells us:

~~~
-l                         use a long listing format
~~~
{: .bash}

~~~
ludus:~$ ls -l /home
drwxr-xr-x 1 ludus  users  4096 Jun 15  2019 ludus
~~~
{: .bash}

or on a macOS `zsh`:
~~~
 ~ ls -l /home
lrwxr-xr-x  1 root  wheel  25 Dec 16 20:18 /home -> /System/Volumes/Data/home
~~~

This gives us a bunch more information about each file or directory present. First, the `d` at the beginning of the line tells us that `ludus` is a directory (or `l` for a symbolic link in macOS example). Then follow three groups of three characters (`rwx`). These indicate what permissions the owner of the file (`ludus`), the owning group (`users`), and everyone else respectively have on the relevant item. A `-` indicates that the given principal does not have the given permission. Above, only the owner is allowed to modify (`w`) the ludus directory (i.e., add/remove files in it). To enter a directory, a user must have “search” (represented by “execute”: `x`) permissions on that directory (and its parents). To list its contents, a user must have read (`r`) permissions on that directory. For files, the permissions are as you would expect. Notice that nearly all the files in `/bin` have the `x` permission set for the last group, “everyone else”, so that anyone can execute those programs.

Some other handy programs to know about at this point are `mv` (to rename/move a file), `cp` (to copy a file), and `mkdir` (to make a new directory).

If you ever want more information about a program’s arguments, inputs, outputs, or how it works in general, give the `man` program a try. It takes as an argument the name of a program, and shows you its manual page. Press `q` to exit.

~~~
ludus:~$ man ls
~~~
{: .bash}