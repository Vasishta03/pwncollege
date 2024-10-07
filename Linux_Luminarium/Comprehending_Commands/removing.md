## DESCRIPTION

Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:

> hacker@dojo:~$ touch PWN
> 
> hacker@dojo:~$ touch COLLEGE
> 
> hacker@dojo:~$ ls
> 
> COLLEGE     PWN
> 
> hacker@dojo:~$ rm PWN
> 
> hacker@dojo:~$ ls
> 
> COLLEGE
> 
> hacker@dojo:~$
> 
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!

## APPROACH 
I moved to the home directory first and then i deleted the `delete_me` file using the `rm` command and then i ran the `/challenge/check` command to get the flag.
![image](https://github.com/user-attachments/assets/9e0760e3-0251-419e-a44d-c68a66f03e14)
