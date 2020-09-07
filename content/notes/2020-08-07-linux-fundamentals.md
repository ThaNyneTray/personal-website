---
title: Linux Fundamentals
author: Desmond Tuiyot
date: '2020-08-07'
slug: linux-fundamentals
categories: []
tags:
  - linux
  - ubuntu
---

## Getting Started w/ the Linux Command Line

### Working w/ Linux Command Line: Basics

**Using Linux Help Resources**  
* **man wget** is a command that takes another command as a parameter and displays a well organized reference showing its syntax, usage patterns, and command line arguments
* **wget** is a command that takes a link and downloads the file being identified by that url
* **apt** - I assume apt is just a command to install packages, and **sudo** allows privileged users to run single programs with admin privileges without running the whole shell session as root.
* **sudo apt update** - this makes sure that *apt* knows all about the latest packages
* **sudo apt upgrade** - upgrades packages with newer versions
* **info** - this command lists out a menu of major topics including a list of installed programs
* **/** - the forward slash allows you to search
* **/usr/share/doc/wget** - many commands keep documentation and sample configuration files in this directory
* **less README** - this command opens the given file for viewing
* **wget --help | less** - this outputs the help text of that command to the less text reader?
* **type wget** - this command tells us how *wget* will be interpreted by bash

**The Linux Terminal**
* **ls -a** - it lists out all the files/folders in the current directory, including the hidden stuff
* **.bashrc** - when you open the terminal, a new *shell session* is created with settings from this file called *.bashrc* 
  * If you want to change the shell settings, this is one of the files to edit
  * These settings will only be applied to non-login GUI sessions
* When logging in through an **ssh**, for example, you get a *login session* which gets its settings and values from a bunch of different files including **.profile**

**Linux Command Syntax Patterns and Shortcuts**
* **Arguments**
  * argument often have a short form, like *-a*, and have longer form equivalents like **--all**
  * there are some exceptions to the *dash* notation. 
    * **ip addr** or just **ip a** shows the ip addresses associated with my system's network interfaces.
  * **combining multiple short arguments**
    * **ls -lht**   
      **-l** displays the directory's contents in long form, showing object permissions, ownership size, and age details  
      **-h** displays the size in human readable format  
      **-t** organizes the contents in descending chronological order  
* **Command Line Shortcuts** - systems admins are profoundly lazy it seems
  * the **Tab** key for autocomplete
  * **cd** typing just this anywhere takes you back to the user home directory
  * **arrow keys** for cycling through command history
  * **history** displays the 1000 most recent commands, which is stored in hidden file in the user home dir called **.bash_history**
  
## Navigating the Linux File System

**Working w/ Files and Directories**
* Absolute paths vs relative paths - **./** and **../** 
* **pwd** - prints out the current directory location
* **mkdir** - creates a directory
* **nano file1** - nano is a file editor. Calling it with a file name such as the one given either opens up a existing file or creates one if that file does not exist. 
* **touch file1** either creates a new file or updates the date timestamp if file exists
* **cp file1 newdir/** - copies the file to the directory specified
* **mv file1 newdir/** - moves the file to the directory specified
* **globbing** - spreading an action across a global target
  * **cp file* newdir/** - this copies all the files that are prefixed with **file** into the specified directory - the * matches either 0 or more characters. 
  * **cp file? newdir/** - like above but limits the number of characters after **file** to just 1. the ? matches exactly 1 character
* **rm file** deletes the specified file
* **rm * ** deletes everything inside that directory
* **rmdir dire** deletes the specified directory

**Searching the Linux File System**
* **etc directory** - this is where most config files are kept
* **locate** - this command locates and prints out the paths to the file specified
  * locate reads a pre-compiled index of all the files and directories in the system
  * you can manually update that index using **sudo updatedb**
* **cat file1** displays the contents of *file1*
  * **cat >file2** creates a new file called file2
* Linux functionality is heavily dependent on text data, and therefore linux has a full set of **text manipulation tools** to read, transform, and redirect text
  * **|** - the pipe operator. This allows for multiple manipulation/search commands to be executed on a piece of text to filter it
  * **grep** - tool for searching text and that matches a regular expression
  * **>** - redirects text output to a new/existing file. If file exists, the text on there previously is overwritten
  * **>>** - same as **>** but if file exists, it appends to the file instead of overwriting it
  * **head** , **tail** - prints out the first/last 10 lines of a file
  * **cut -d: -f3 some_file** - cut splits each line of the output at the delimeter specified by *-d*.
    * **-f3** specifies that we are only interested in processing the contents of the 3rd field
  * **sort -rn** - *-n* sorts in ascending order and adding *-r* reverses that
  * **wc some_file** shows the number of lines, words, and characters in the specified file
* **Standard Streams & Redirects**
  * **stdin** - this accepts input from the keyboard through which it's made available to Bash.
    * A standard input redirect (symbol used is **<**) would accept data from an alternate source 
  * **stdout** - by default, this would send data to the terminal
    * **>>**, **>** - standard output redirects sends that output to a file
  * **stderr** - writes any errors generated by a command to the terminal
    * **some_cmd_with_error 2> some_file** - the redirect is done using **2>**. The number 2 is a designation for standard error. 
  * **stderr**

**Working w/ Archives**
* **tar** - this is the most common tool for compression and archiving. Used to stand for *tape archives*
* **some_file.tar.gz** - most archives in linux are compressed using those 2 tools- *tar* and *gzip*
* **tar xzf file.tar.gz** - this is a command to unzip an archive
  * **x** specifies that we want to extract the archive
  * **z** specifies that the file is zipped
  * **f** indicates that the file name will follow immediately after
* **tar czf newfile.tar.gz some_dir/** - this command zips the specified folder into the archive specified. Really the only difference in this command is that we use *c* for *compress* vs *x* for *extract*
* **gzip some_file** - zips the file using the gzip algorithm. Use this if you forgot to add *z* it the tar command
* **bzip2** - a different compression algorithm, similar to gzip.
* **unzip** - some files come in *.zip* format. *unzip* is used when handling these.
* **zip newname.zip * ** - this command creates a new zip file containing all the files inside the current directory

**Linux Kernel Modules and Peripherals**
* When troubleshooting peripherals, there's 2 main steps
  1. Is the device recognized by Linux?
  2. Are there appropriate kernel modules loaded that'll allow Linux to communicate with the device and expose it to the user?
* Commands to see what's available to the users
  * **lsusb** - shows devices connected using USB port
  * **lspci** - shows those connected using PCI slots
  * **lshw** - shows the whole hardware range in one output. There's a ton of these. 
* If there's a device that isn't available to the users, it's possible that there's a missing kernel module/one that hasn't been loaded. 
  * Most modules are stored in the directory **/lib/modules/**
  * However, what modules you want to load are dependent on the kernel version you're running at the moment.
  * You find that using **uname -r**
  * **command substitution** - Using backticks, it's possible to substitute the results of a particular command into the operation of another.
  * **ls /lib/modules/`uname -r`**
  * Kernel modules usually have a **.ko** extension
  * **lsmod** lists out all the modules currently loaded
  * **modprobe module_name** this command loads the specified module


