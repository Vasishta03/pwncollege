# Chaining Commands

## Chaining with Semicolons
### Description 
Basically, when you hit Enter, your shell executes your typed command and, after that command terminates, give you the prompt to input another command. The semicolon is analogous, just without the prompt and with you entering both commands before anything is executed.

Give it a try now! In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.
### Approach 
![image](https://github.com/user-attachments/assets/5fa6a500-d4a7-41bb-bfba-cf195db891ba)
---

## You First Shell script
### Description 
As you combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell script, and run them by executing the file!
You can see that the shell script executed both commands, creating and printing the pwn file.

Now, it's your turn! Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!
### Approach 
In the Nano file i entered the following:
> /challenge/pwn
>
> /challenge/college
> 
![image](https://github.com/user-attachments/assets/9a097428-18d5-4311-9e89-6b0e50bd82ae)
---

## Redirecting script Output
### Description
Let's try something a bit trickier! You've piped output between programs with |, but so far, this has just been between one command's output and a different command's input. But what if you wanted to send the output of several programs to one command? There are a few ways to do this, and we'll explore a simple one here: redirecting output from your script!

As far as the shell is concerned, your script is just another command. That means you can redirect its input and output just like you did for commands in the Piping module!
All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors, and | for piping to another command.

In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command!

### Approach 

<img width="610" alt="image" src="https://github.com/user-attachments/assets/e0eb3fba-5ba1-4543-a654-f2f0c1984086">
---

## Executable shell scripts
### Description 
You have written your first shell script, but calling it via bash script.sh is a pain. Why do you need that bash?

When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.

It turns out that you can avoid the need to manually invoke bash. If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path! For example, if you create script.sh in your home directory and make it executable, you can invoke it via /home/hacker/script.sh or ~/script.sh or (if your working directory is /home/hacker) ./script.sh.

Try that here! Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

### Approach 
In the solve.sh I entered the command `/challenge/solev` and saved it. 
![image](https://github.com/user-attachments/assets/18951516-1338-432e-b427-3d88a4a4a4ee)
