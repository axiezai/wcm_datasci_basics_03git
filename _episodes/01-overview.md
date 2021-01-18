---
title: "What is the Shell?"
teaching: 10 
exerises: 0
questions: 
- "What is the Shell?"
objectives:
- "Familiarize with your own shell prompt"
- "Interact with basic shell programs" 
keypoints:
- "Begin using `bash` or `zsh`"
- "Shells search for available programs listed in `$PATH` variable"
---

## What is the shell?
Computers these days have a variety of interfaces for giving them commands; fancyful graphical user interfaces, voice interfaces, and even AR/VR are everywhere. These are great for 80% of use-cases, but they are often fundamentally restricted in what they allow you to do — you cannot press a button that isn’t there or give a voice command that hasn’t been programmed. To take full advantage of the tools your computer provides, we have to go old-school and drop down to a textual interface: The Shell.

Nearly all platforms you can get your hand on has a shell in one form or another, and many of them have several shells for you to choose from. While they may vary in the details, at their core they are all roughly the same: they allow you to run programs, give them input, and inspect their output in a semi-structured way.

To open a shell promt, you first need a terminal, your device probably shipped with one installed, or you should have installed one fairly easily by following the set-up guide from the syllabus. In this lecture, we will focus on the most widely used shells: Bourne Again Shell (bash) or Z shell (zsh). Bash is the most widely used shells, Zsh recently became the default shell for Macs after an OS Update. Both shells share a very similar syntax, and their synatx is similar to what you will see in many other shells. 

## Using the shell
When you launch your terminal, you will see a prompt that often looks a little like this:
~~~
ludus:~$
~~~
{: .bash}

This is the main textual interface to the shell. It tells you that you are on the machine `ludus` and that your "current working directory", or where you are currently operating the shell, is `~` (short for "home"). The `$` tells you that you are not the root user (more on that later). At this prompt you can type a *command*, which will then be interpreted by the shell. The most basic command is to execute a program:

~~~
ludus:~$ date
Sat Dec 26 15:57:06 EST 2020
ludus:~$
~~~
{: .bash}

Here we executed the `date` program, which (perhaps unsurprisingly) prints the current date and time. The shell then asks us for another command to execute. We can also excute a command with *arguments*:

~~~
ludus:~$ echo hello
hello
~~~
{: .bash}

In this case, we told the shell to execute the program `echo` with the argument `hello`. The `echo` program simply prints out its arguments. The shell parses the command by splitting it by whitespace, and then runs the program indicated by the first word, supplying each subsequent word as an argument that the program can access. If you want to provide an argument that contains spaces or other special characters (e.g., a directory named “My Photos”), you can either quote the argument with `'` or `"` (`"My Photos"`), or escape just the relevant characters with `\` (`My\ Photos`).

But how does the shell know how to find the `date` or `echo` programs? Well, the shell is a programming environment, just like Python or Ruby, and so it has variables, conditionals, loops, and functions (next lecture!). When you run commands in your shell, you are really writing a small bit of code that your shell interprets. If the shell is asked to execute a command that doesn’t match one of its programming keywords, it consults an environment variable called `$PATH` that lists which directories the shell should search for programs when it is given a command:

~~~
ludus:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ludus:~$ which echo
/bin/echo
ludus:~$ /bin/echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
~~~
{: .bash}

When we run the `echo` command, the shell sees that it should execute the program `echo`, and then searches through the `:`-separated list of directories in `$PATH` for a file by that name. When it finds it, it runs it (assuming the file is executable; more on that later). We can find out which file is executed for a given program name using the `which` program. We can also bypass `$PATH` entirely by giving the path to the file we want to execute.

The `$PATH` input we used is one of the many environment variables available to Linux and macOS systems, these dynamically named values are stored within the system and are used by applications launched in the shell. We will talk about how environment variables can allow you to customize your system behavior in the next chapter, but for now here's a list of common environment variables for you to explore in your own shell:

 - **`USER`** - your current username.
 - **`SHELL`** - the path to the current command shell.
 - **`PWD`** - the current working directory.
 - **`HOSTNAME`** - the hostname of the computer.
 - **`HOME`** - your home directory (`~`).
 - **`LANG`** - your current language.
 - **`TZ`** - your time zone.
 - **`PS1`** - your default bash prompt.
 - **`TERM`** - your current terminal type.
 - **`HISTFILESIZE`** - the maximum number of lines in the history file.
 - **`OSTYPE`** - the type of operating system.