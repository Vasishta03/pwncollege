# Practicing Piping
---

## Redirecting Output
### Decsription
First, let's look at redirect stdout to files. You can accomplish this with the > character, as so:

> hacker@dojo:~$ echo hi > asdf
> 
This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:

> hacker@dojo:~$ cat asdf
> 
> hi
> 
In this challenge, you must use this input redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

### Approach
![image](https://github.com/user-attachments/assets/3e8c6219-c706-461c-9efa-e2453d47152b)

---

## Redirecting More Output
### Description
Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!

### Approach 

I need to redirect the output from `/challenge/run` to a file called `myflag`.

After this, I found that the redirection is successful and I can directly read the flag by the command `cat myflag`.

![image](https://github.com/user-attachments/assets/c68ff425-dce7-4193-8c79-e730806a55c3)
---

## Appending Output
### Description
A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.

You can redirect input in append mode using >> instead of >, as so:

> hacker@dojo:~$ echo pwn > outfile
> 
> hacker@dojo:~$ echo college >> outfile
> 
> hacker@dojo:~$ cat outfile
> 
> pwn
> 
> college
> 
> hacker@dojo:$
> 
To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

Go for it now!

### Approach

![image](https://github.com/user-attachments/assets/94fd0087-2b8d-4d12-9799-df46b7fdc14c)

---

## Redirecting Errors
### Description
When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). Thus, the following two commands are equivalent:

> hacker@dojo:~$ echo hi > asdf
> 
> hacker@dojo:~$ echo hi 1> asdf
> 
Redirecting errors is pretty easy from this point. If you have a command that might produce data via standard error (such as /challenge/run), you can do:

> hacker@dojo:~$ /challenge/run 2> errors.log
> 
That will redirect standard error (FD 2) to the errors.log file. Furthermore, you can redirect multiple file descriptors at the same time! For example:

> hacker@dojo:~$ some_command > output.log 2> errors.log
> 
That command will redirect output to output.log and errors to errors.log.

Let's put this into practice! In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions. You'll notice that nothing will be printed to the terminal, because you have redirected everything! You can find the instructions/feedback in instructions and the flag in myflag when you successfully pull this off!

### Approach
![image](https://github.com/user-attachments/assets/2e720ecc-62c4-43a8-aba3-25081fa067ba)

---

## Redirecting Input
### Description
Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:

> hacker@dojo:~$ echo yo > message
> 
> hacker@dojo:~$ cat message
> 
> yo
> 
> hacker@dojo:~$ rev < message
> 
> oy
> 
You can do interesting things with a lot of different programs using input redirection! In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

### Approach 
Redirect the COLLEGE Value with the PWN file and then in turn with the /challenge/run command.

![image](https://github.com/user-attachments/assets/d882013a-d562-4ecb-b1f2-7507a8ad6fdd)
---

## Grepping Stored Results
### Description 
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

In preparation for more complex levels, we want you to:

1. Redirect the output of /challenge/run to /tmp/data.txt.
2. This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
3. Grep that for the flag!
### Approach
![image](https://github.com/user-attachments/assets/3d86bd7e-0111-4f70-a264-7e58d229c37f)

---
## Grepping Live Output
### Description
It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can use this using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:

> hacker@dojo:~$ echo no-no | grep yes
> 
> hacker@dojo:~$ echo yes-yes | grep yes
> 
> yes-yes
> 
> hacker@dojo:~$ echo yes-yes | grep no
> 
> hacker@dojo:~$ echo no-no | grep no
> 
> no-no
> 
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. Grep for the flag!

### Approach 
![image](https://github.com/user-attachments/assets/86b98d77-0d00-4afd-986f-bc9a6ccca16a)
----

## Grepping Errors
### Description
You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

Try it now! Like the last level, this level will overwhelm you with output, but this time on standard error. Grep through it to find the flag!

### Approach 

![image](https://github.com/user-attachments/assets/1248a674-13bc-4243-b1f2-338d9619d21d)
----

## Duplicating pipe data with tee
### Description
When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired: for example, you might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???").

Luckily, there is a solution! The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line. For example:

> hacker@dojo:~$ echo hi | tee pwn college
> 
> hi
> 
> hacker@dojo:~$ cat pwn
> 
> hi
> 
> hacker@dojo:~$ cat college
> 
> hi
> 
> hacker@dojo:~$
> 
As you can see, by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file. You can imagine how you might use this to debug things going haywire:

> hacker@dojo:~$ command_1 | command_2
> 
> Command 2 failed!
> 
> hacker@dojo:~$ command_1 | tee cmd1_output | command_2
> 
> Command 2 failed!
> 
> hacker@dojo:~$ cat cmd1_output
> 
> Command 1 failed: must pass --succeed!
> 
> hacker@dojo:~$ command_1 --succeed | command_2
> 
> Commands succeeded!
> 
Now, you try it! This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!

### Approach 

![image](https://github.com/user-attachments/assets/5046cf8e-8c9d-463c-b4f2-216fdf108f64)
---

## Writing to multiple Programs
### Description
The observant learner will realize that the following are equivalant:

> hacker@dojo:~$ echo hi | rev
> 
> ih
> 
> hacker@dojo:~$ echo hi > >(rev)
> 
> ih
> 
> hacker@dojo:~$
> 
More than one way to pipe data! Of course, the second route is way harder to read and also harder to expand. For example:

> hacker@dojo:~$ echo hi | rev | rev
> 
> hi
> 
> hacker@dojo:~$ echo hi > >(rev | rev)
> 
> hi
> 
> hacker@dojo:~$
> 
That's just silly! The lesson here is that, while Process Substitution is a powerful tool in your toolbox, it's a very specialized tool; don't use it for everything!

### Approach 
![image](https://github.com/user-attachments/assets/b805ef42-ec2a-4236-9816-35107a1b9677)

----

## Split-Piping stderr and stdout
### Description 
Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of >(), 2>, and |. How to do it is a task I'll leave to you.

In this challenge, you have:

- /challenge/hack: this produces data on stdout and stderr
- /challenge/the: you must redirect hack's stderr to this program
- /challenge/planet: you must redirect hack's stdout to this program
Go get the flag!

### Approach 

![image](https://github.com/user-attachments/assets/ebb0bc84-2aed-459b-8276-5c3a7cf01561)
---

