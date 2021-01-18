---
title: "Connecting Programs"
teaching: 10
exerises: 0
questions: 
- "How to work with shell input and output streams"
objectives:
- "Begin navigating the shell"
- "Understand file permissions" 
keypoints:
- "Use `cd` and `ls` to navigate your file system"
- "Files have permissions indicated by `rwx`"
- "`mv`, `cp`, and `mkdir` are useful programs"
- "Check a program's usage with `man`"
---

## Connecting programs

We just mentioned a few handy programs in the shell. Programs have two primary "streams" associated with them: their input stream and theirr output stream. When the program tries to read input, it reads from the input stream, and when it prints something, it prints to its output stream. Normally, a program’s input and output are both in your terminal. That is, your keyboard as input and your screen as output. However, we can also rewire those streams!

The simplest form of redirection is `< file` and `> file`. These let you rewire the input and output streams of a program to a file respectively:
~~~
ludus:~$ echo hello > hello.txt
ludus:~$ cat hello.txt
hello
ludus:~$ cat < hello.txt
hello
ludus:~$ cat < hello.txt > hello2.txt
ludus:~$ cat hello2.txt
hello
~~~
{: .bash}

You can also use `>>` to append to a file. Where this kind of input/output redirection really shines is in the use of pipes. The `|` operator lets you “chain” programs such that the output of one is the input of another:
~~~
ludus:~$ ls -l / | tail -n1
drwxr-xr-x 1 root  root  4096 Jun 20  2019 var
ludus:~$ curl --head --silent google.com | grep --ignore-case content-length | cut -d=' ' -f2
219
~~~
{: .bash}

We will go into a little more detail about how to take advantage of pipes with future examples.

## Next steps:
At this point you know your way around a shell enough to accomplish basic tasks. You should be able to navigate around to find files of interest and use the basic functionality of most programs. In the next lecture, we will talk about how to perform and automate more complex tasks using the shell and the many handy command-line programs out there.