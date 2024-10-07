# Digesting Documentation

---

## Learning From Documentation
### Description 
The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, in the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation.

### Approach 

![image](https://github.com/user-attachments/assets/2e6e784a-2068-4d5b-9fbc-571de67ce07a)

---
## Learning Complex Usage
### Description
While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

> Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument.
> The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!

### Approach

![image](https://github.com/user-attachments/assets/0a271e8a-9ae7-49c8-b594-732a0218573a)

---

## Reading Manuals
### Description 
This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):
Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!

### Approach

![image](https://github.com/user-attachments/assets/ca193aa2-cfa4-474b-95cf-7e7be7842dad)

---

## Searching Manuals
### Description 
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.

### Approach

I opened man challenge and then i searched for the argument containing the flag so then i pressed `n` to find the flag and then i pressed `/challenge/challenge --name` to get the final flag.
![image](https://github.com/user-attachments/assets/ce9942a1-844e-40d0-b755-82110e722772)

---

## Searching for Manuals
### Description

This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the man pages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right man page, read the man page manpage by doing: man man!

### Approach 

![image](https://github.com/user-attachments/assets/ac321c79-498e-41e6-a4af-59ce0cd53d52)
By reading the manual i found that `man -k` command which is used for searching for man page names and descriptions for that specific word.

![image](https://github.com/user-attachments/assets/6277287d-bf87-4c4a-90cf-9da95f2aa11c)

![image](https://github.com/user-attachments/assets/9a2d02a2-a80b-4a57-8f8f-be427f73ec74)

---

## Helpful Programs
### Description

Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!

### Approach

![image](https://github.com/user-attachments/assets/d9d5ecfe-4dd7-43dc-9335-d37cc5a7e4b2)

---

## Help For Builtins

### Description

Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help

Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!

### Approach 

![image](https://github.com/user-attachments/assets/92467d24-755e-49d7-b79e-85d3022da357)

---
