---
title: "Assignment"
teaching: 0
exercises: 20
---

## Assignment
The following are instructions. Go to the [course website's Week 1 assignment page](https://wcm-datascibasics.github.io/assignments/chapter1.html) for the list of questions to be answered and submitted.

1. For this course, you need to be using a Unix shell like Bash or ZSH. If you are on Linux or macOS, you don’t have to do anything special. If you are on Windows, you need to make sure you are not running cmd.exe or PowerShell; you can use Windows Subsystem for Linux or a Linux virtual machine to use Unix-style command-line tools. To make sure you’re running an appropriate shell, you can try the command `echo $SHELL`. If it says something like `/bin/bash` or `/usr/bin/zsh`, that means you’re running the right program.

2. Create a new directory called `spring2021` under `/tmp`.

3. Look up the `touch` program. Remember that the `man` program is your friend.

4. Use `touch` to create a new file called `datascibasics` in `spring2021`.

5. Write the following into that file, one line at a time. The first line might be tricky to get working. It’s helpful to know that `#` starts a comment in Bash, and `!` has a special meaning even within double-quoted (`"`) strings. Bash treats single-quoted strings (`'`) differently: they will do the trick in this case. See the [Bash quoting](https://www.gnu.org/software/bash/manual/html_node/Quoting.html) manual page for more information.

    ~~~
    #!/bin/sh
    curl --head --silent https://wcm-datascibasics.github.io
    ~~~
    {: .bash}

6. Try to execute the file, i.e. type the path to the script (`./datascibasics`) into your shell and press enter. Understand why it doesn’t work by consulting the output of `ls` (hint: look at the permission bits of the file).

7. Run the command by explicitly starting the `sh` interpreter, and giving it the file `datascibasics` as the first argument, i.e. `sh datascibasics`. Why does this work, while `./datascibasics` didn’t?
 
8. Look up the `chmod` program (e.g. use `man chmod`). This online interactive [chmod calculator](https://chmod-calculator.com/) is a handy tool to have book marked in your browser.

9. Use `chmod` to make it possible to run the command `./datascibasics` rather than having to type `sh datascibasics`. How does your shell know that the file is supposed to be interpreted using `sh`? See this page on the [shebang line](https://en.wikipedia.org/wiki/Shebang_(Unix)) for more information.

10. Use `|` and `>` to write the “last modified” date output by `datascibasics` into a file called `last-modified.txt` in your home directory.
