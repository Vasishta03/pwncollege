## DESCRIPTION
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

> hacker@dojo:~$ cd /some/new/directory
> 
> hacker@dojo:/some/new/directory$ cd /some/new/directory
> 
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!
## APPROACH
![image](https://github.com/user-attachments/assets/a4489976-025f-4d95-bc45-d0d26c941a26)
