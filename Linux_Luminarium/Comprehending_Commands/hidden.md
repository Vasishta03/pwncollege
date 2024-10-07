## DESCRIPTION

Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

> hacker@dojo:~$ touch pwn
> 
> hacker@dojo:~$ touch .college
> 
> hacker@dojo:~$ ls
> 
> pwn
> 
> hacker@dojo:~$ ls -a
> 
> .college	pwn
> 
> hacker@dojo:~$
> 
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.

## APPROACH

![image](https://github.com/user-attachments/assets/d2c5cf69-428a-4c6a-9963-1978109d0240)
