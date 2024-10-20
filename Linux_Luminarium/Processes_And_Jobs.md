# Processes and Jobs

## Listing Processes
### Description 
As ps is a very old utility, its usage is a bit of a mess. There are two ways to specify arguments.

"Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.

"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.

These two methods, ps -ef and ps aux result in slightly different, but cross-recognizable output.
There are many commonalities between ps -ef and ps aux: both display the user (USER column), the PID, the TTY, the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND). ps -ef additionally outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in question, while ps aux outputs the percentage of total system CPU and Memory that the process is utilizing. Plus, there's a bunch of other stuff we won't get into right now.

Anyways! Let's practice. In this level, I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory! But I also launched it, so can find it in the running process list, figure out the filename, and relaunch it directly for the flag! Good luck!

### Aproach
![image](https://github.com/user-attachments/assets/2fe7cc74-40db-47cf-8255-74d6cffb3786)
---

## Killimg Processes
### Description 
You've launched processes, you've viewed processes, now you will learn to terminate processes! In Linux, this is done using the aggressively-named kill command. With default options (which is all we'll cover in this level), kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

Let's say you had a pesky sleep process (sleep is a program that simply hangs out for the number of seconds specified on the commandline, in this case, 1337 seconds) that you launched in another terminal, like so:

> hacker@dojo:~$ sleep 1337
> 
How do we get rid of it? You use kill to terminate it by passing the process identifier (the PID from ps) as an argument, like so:

> hacker@dojo:~$ ps -e | grep sleep
>
>  342 pts/0    00:00:00 sleep
>
> hacker@dojo:~$ kill 342
> 
> hacker@dojo:~$ ps -e | grep sleep
> 
> hacker@dojo:~$
> 
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission. Good luck.

### Approach 
PID 74 is for sleep so we kill PID 74 to get the payment.
![image](https://github.com/user-attachments/assets/f98bcc57-395d-4877-805a-e560da255558)
---

## Interrupting Processes
### Description 
You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

Try it here! /challenge/run will refuse to give you the flag until you interrupt it. Good luck!

### Approach 
When the process in running we enter `Ctrl + c ` to interrupt the process to get the flag.
![image](https://github.com/user-attachments/assets/2c745cfd-a72d-43b5-82df-3e9c0695202e)
---

## Suspending Processes
### Description 
You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this works and, in the next level, we'll figure out how to resume those suspended processes!

This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!

### Approach 

![image](https://github.com/user-attachments/assets/9eb5d590-9244-475e-90b6-65683da86522)
---

## Resuming Processes
### Description
Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

Go try it out! This challenge's run needs you to suspend it, then resume it. Good luck!

### Approach 

![image](https://github.com/user-attachments/assets/db7263bb-b828-4260-afb8-e4fafcd8975e)
---

## Backgrounding Processes
### Description 
You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command! This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

This level's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background!
The sleep process is now suspended in the background.
Boom! The sleep now has an S. It's sleeping while, well, sleeping, but it's not suspended! It's also in the background and thus doesn't have the +.

### Approach 

![image](https://github.com/user-attachments/assets/ca4358d4-079f-4105-a4b9-f376a5ae1ad4)
---

## Foregrounding Processes
### Description
Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level will walk you through that!
### Approach 

![image](https://github.com/user-attachments/assets/9d899ff7-2eac-4761-9554-6ea2115e03d8)
---

## Starting Backgrounded Processes
### Description 
Of course, you don't have to suspend processes to background them: you can start the backgrounded right off the bat! It's easy; all you have to do is append a & to the command, like so:

> hacker@dojo:~$ sleep 1337 &
> 
> [1] 1771
> 
> hacker@dojo:~$ ps -o user,pid,stat,cmd
> 
> USER         PID STAT CMD
> 
> hacker      1709 Ss   bash
> 
> hacker      1771 S    sleep 1337
> 
> hacker      1782 R+   ps -o user,pid,stat,cmd
> 
> hacker@dojo:~$
> 
Here, sleep is actively running in the background, not suspended. Now it's your turn to practice! Launch /challenge/run backgrounded for the flag!

### Approach 

![image](https://github.com/user-attachments/assets/a22273c0-4773-4d3d-bda7-4548de0051ba)
---

## Process Exit Codes
### Description 
Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates, This can be used by the shell, or the user of the shell (that's you!) to check if the process succeeded in its functionality (this determination, of course, depends on what the process is supposed to do in the first place).

You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value!):

> hacker@dojo:~$ touch test-file
> 
> hacker@dojo:~$ echo $?
> 
> 0
> 
> hacker@dojo:~$ touch /test-file
> 
> touch: cannot touch '/test-file': Permission denied
> 
> hacker@dojo:~$ echo $?
> 
> 1
> 
> hacker@dojo:~$
> 
As you can see, commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument. Good luck!

### Approach 

![image](https://github.com/user-attachments/assets/59ac5e46-e14c-4fa6-8915-e428ad771aee)



