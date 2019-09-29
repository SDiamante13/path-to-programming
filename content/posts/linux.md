---
title: "Linux"
date: 2018-09-27T01:46:38-05:00
draft: true
---

## Linux

In my three months of being a software developer I have grown to love the Linux Bash CLI.

In this post, we will explore some simple Linux commands that will help you get more comfortable working with the command line.

* `ls` (lists all non-hidden files in current directory)
* `ls -la` (lists **all files** in current directory)
* `cat filename.txt` (prints the contents of the file to the screen)
* `vim filename.txt` (opens up file in vim text editor)
* `[tab]` (pressing tab autocompletes path or filename if it is in the directory)
* `rm -rf images` (removes file or folder recursively and forced, use with caution!)
* `cp images/pic1.jpg .` (copies the jpg to the current directory)
* `mv images/pic1.jpg .` (moves the jpg to the current directory)
* `pwd` (prints current path)
* `mkdir temp` (makes a new directory)
* `touch file1.txt` (creates a new file)
* `cd folder1/folder2` (navigates to other directories)
* `cd ..` `cd ../..` (go back a number of directories)
* `cd -` (go back to the last directory you were in)
* `file filename.txt` (lists what type of file)
* `whatis vim` (lists usages of command, i.e. vim)
* `man (command)` (looks up the manual for a specific command)

## Piping
A very powerful feature of Linux is the function of piping. Most linux commands do one thing very well. If you would like to combine multiple function together you can use a pipe: `|`

If you would like to print a file, but only want the last 30 lines you would use:

`cat file1.txt | tail -n 30`

___

Now for some more advanced commands:

* `h | grep {keyword}` (lists history for all commands which use the keyword)
* `grep` in itself is a very useful command for filtering and searching for specific characters
* `ctrl+R` (reverse search, begin typing and this command will search in the history for something that fits this)
* `ps -aux` (lists all processes running on your machine)

