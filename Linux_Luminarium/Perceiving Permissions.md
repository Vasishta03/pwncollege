# Perceiving Permissions
## Changing File Ownership
### Description 
college_file's owner has been changed to the hacker user, and how hacker can do with it whatever root had been able to do with it! If this was the /flag file, that means that the hacker user would be able to read it!

In this level, we will practice changing the owner of the /flag file to the hacker user, and then the flag. For this challenge only, I made it so that you can use chown to your heart's content as the hacker user (again, typically, this requires you to be root). Use this power wisely and chown away!
### Approach 
![image](https://github.com/user-attachments/assets/b8d58933-4b7e-4440-8a2b-0ee67eb93b2a)
---

## Groups and Files
### Description
Here, the flag file is owned by the root user and the root group, and the hacker user is neither the root user nor a member of the root group, so the file cannot be accessed. Luckily, group ownership can be changed with the chgrp (change group) command! Unless you have write access to the file and membership in the new group, this typically requires root access.
In this level, I have made the flag readable by whatever group owns it, but this group is currently root. Luckily, I have also made it possible for you to invoke chgrp as the hacker user! Change the group ownership of the flag file, and read the flag!
### Approach
![image](https://github.com/user-attachments/assets/a3fe826f-e4e1-4617-aa20-27ea8b3b3816)
---

## Fun With Group Names
### Description 
In the previous levels, you may have noticed that your hacker user is a member of the hacker group, and that zardus is a member of the zardus group. There is a convention in Linux that every user has their own group, but this does not have to be the case. For example, many computer labs will put all of their users into a single, shared users group.

The point is, you've used hacker for the group before, but in this level, that is not going to work. I'll still allow you to use chgrp, but I have randomized the name of the group that your user is in. You will need to use the id command to figure that name out, then chgrp to victory!
### Approach
![image](https://github.com/user-attachments/assets/c28ec364-bbb2-4f88-ad40-251049bf7bad)
---

## Changing Permissions
### Description 
In this challenge, you must change the permissions of the /flag file to read it! Typically, you need to have write access to the file in order to change its permissions, but I have made the chmod command all-powerful for this level, and you can chmod anything you want even though you are the hacker user. This is an ultimate power. The /flag file is owned by root, and you can't change that, but you can make it readable. Go and solve this!

### Approach 
![image](https://github.com/user-attachments/assets/94f90e95-5359-4d33-80a4-54d196f88d3f)
---

## Executable Files
### Description
In this case, /challenge/run runs because it is executable by the hacker user. Because the file is owned by the root user and root group, this requires that the execute bit is set on the other permissions). If we remove these permissions, the execution will fail!
In this challenge, the /challenge/run program will give you the flag, but you must first make it executable! Remember your chmod, and get /challenge/run to tell you the flag!
### Approach 
![image](https://github.com/user-attachments/assets/aa1a8aad-31c3-4633-a65a-addb0b3d64b5)
---

## Permission Tweaking Practice
### Description 
You think you can chmod? Let's practice!

This challenge will ask you to change the permissions of the /challenge/pwn file in specific ways a few times in a row. If you get the permissions wrong, the game will reset and you can try again. If you get the permissions right eight times in a row, the challenge will let you chmod /flag to make it readable for yourself :-) Launch /challenge/run to get started!
### Approach 

---
## Permission Setting Practice
### Description 
In addition to adding and removing permissions, as in the previous level, chmod can also simply set permissions altogether, overwriting the old ones. This is done by using = instead of - or +. 
Keep in mind, that -, appearing after = is in a different context than if it appeared directly after the u, g, or o (in which case, it would cause specific bits to be removed, not everything).

This level extends the previous level by requesting more radical permission changes, which you will need = and ,-chaining to achieve. Good luck!
### Approach 

---

## The SUID Bit 
### Description 
There are many cases in which non-root users need elevated access to do certain system tasks. The system admin can't be there to give them the password every time a user wanted to do a task that only root/sudoers can do. The "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file.

This is actually the exact mechanism used to let the challenge programs you run read the flag or, outside of pwn.college, to enable system administration tools such as su, sudo, and so on. The permission of a file with SUID list look like this:

> hacker@dojo:~$ ls -l /usr/bin/sudo
>
> -rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/sudo
>
> hacker@dojo:~$
>
The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program (as long as they have executable permissions), the program will execute as the owner user (in this case, the root user).

As the owner of a file, you can set a file's SUID bit by using chmod:

> chmod u+s [program]
> 
But be careful! Giving the SUID bit to an executable owned by root can give attackers a possible attack vector to become root. You will learn more about this in the Program Misuse module.

Now, we are going to let you add the SUID bit to the /challenge/getroot program in order to spawn a root shell for you to cat the flag yourself!
### Approach 
![image](https://github.com/user-attachments/assets/036a5a71-971b-4bf9-b580-7dfac0b56126)



