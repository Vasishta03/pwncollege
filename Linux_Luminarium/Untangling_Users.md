# Untangling Users 
---
## Becoming root with su
### Description 
In this challenge, we will cover the older one, su (the switch user command). This is not typically used to elevate to root access anymore, but it is an elegant utility from a more civilized time, and we'll cover it first.
This check against the root password is what obsoletes su. Modern systems very rarely have root passwords, and different mechanisms (that we will learn later) are used to grant administrative access.

But THIS challenge (and only this challenge) does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag!
### Approach 
the passowrd is `hack-the-planet`
![image](https://github.com/user-attachments/assets/8815ec87-a40f-4a0f-86bb-0a74038e3311)
---
## Other users with su
### Description 
With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root. For example:

> hacker@dojo:~$ su some-user
> 
> Password:
> 
> some-user@dojo:~$
> 
Awesome! In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me. Good luck!

### Approach
the password is `dont-hack-me`

![image](https://github.com/user-attachments/assets/006312e5-a091-4503-b9e9-73faf9ba4189)
---

## Cracking Passwords
### Description 
If a hacker gets their hands on a leaked /etc/shadow, they can start cracking passwords and wreaking havoc. The cracking can be done via the famous John the Ripper.
Here, John the Ripper cracked Zardus' leaked password hash to find the real value of password1337. Poor Zardus!

This level simulates this story, giving you a leak of /etc/shadow (in /challenge/shadow-leak). Crack it (this could take a few minutes), su to zardus, and run /challenge/run to get the flag!

### Approach 

![image](https://github.com/user-attachments/assets/0082712e-d061-41c3-aa39-26f6994d4be6)
---

## Using Sudo

### Description 
Also unlike su, rather than authenticating via password, sudo relies on policies that it checks to determine the user's authorization run things as root. These policies are defined in /etc/sudoers, and though it's mostly out of scale for our purposes, there are plenty of resources for learning about this!

So, the world has moved to sudo and has (for the purposes of system administration) left su behind. In fact, even pwn.college's Practice Mode works by giving you sudo access to elevate privileges!

In this level, we will give you sudo access, and you will use it to read the flag. Nice and easy!
### Approach

![image](https://github.com/user-attachments/assets/2cd2d8be-5d8a-489b-99c7-dff1e7e2c46d)



