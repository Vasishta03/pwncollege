# File Globbing

## Matching with *
### Description 

The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern.
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one.
When zero files are matched, by default, the shell leaves the glob unchanged.
The * matches any part of the filename except for / or a leading . character.
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!

### Approach

![image](https://github.com/user-attachments/assets/60b1e05a-5f9d-453d-ab8a-155647820401)

---

## Matching with ?

### Description 
Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character.
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!

### Approach 

![image](https://github.com/user-attachments/assets/6780db04-3cd7-4ea4-9a2e-0511fbc743c6)
---

## Matching with []

### Description 
Next, we will cover []. The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n.
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!

### Approach 

![image](https://github.com/user-attachments/assets/fa415d12-e91c-4985-afc7-6b1e756e4f48)
---

## Matching paths with []
### Description 
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:

> hacker@dojo:~$ touch file_a
> 
> hacker@dojo:~$ touch file_b
> 
> hacker@dojo:~$ touch file_c
> 
> hacker@dojo:~$ ls
> 
> file_a	file_b	file_c
> 
> hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
> 
> Look: /home/hacker/file_a /home/hacker/file_b
> 
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!

### Approach 
![image](https://github.com/user-attachments/assets/d36da714-1741-430b-b480-c2c9d7a3677b)
---

## Mixing globs
### Description

Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that will match the files "challenging", "educational", and "pwning"!

### Approach

First need to move to the directory `/challenge/files` and then used the `ls` command to list all the files present in it.

Since challenging,educational and pwning we used the argument `[cep]*`
![image](https://github.com/user-attachments/assets/c018458e-f0d7-48fc-ba23-857a1021affd)

---

## Exclusionary Globbing

### Description
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:

> hacker@dojo:~$ touch file_a
> 
> hacker@dojo:~$ touch file_b
> 
> hacker@dojo:~$ touch file_c
> 
> hacker@dojo:~$ ls
> 
> file_a	file_b	file_c
> 
> hacker@dojo:~$ echo Look: file_[!ab]
> 
> Look: file_c
> 
> hacker@dojo:~$ echo Look: file_[^ab]
> 
>Look: file_c
> 
> hacker@dojo:~$ echo Look: file_[ab]
> 
> Look: file_a file_b
> 
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.

### Approach 
To filter the glob paths, we use `[]` in this challenge.

Shift to `/challenge/files` directory and then we run the command `/challenge/run [!pwn]*` to exclude pwn. 

![image](https://github.com/user-attachments/assets/39b8056f-b1ac-462b-ab29-12a467e02954)

---
