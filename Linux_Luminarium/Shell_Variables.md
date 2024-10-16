# Shell Variables 
---

## Printing Variables
### Description 
You can also print out variables with echo, by prepending the variable name with a $. For example, there is a variable, PWD, that always holds the current working directory of the current shell. You print it out as so:

> hacker@dojo:~$ echo $PWD
> 
> /home/hacker
> 
Now it's your turn. Have your shell print out the FLAG variable and solve this challenge!

### Approach 
As mentioned in the challenge, we need to have my shell print the variable called `FLAG` to get the flag!.

![image](https://github.com/user-attachments/assets/0eb7a3d7-8215-44a9-a8b8-6aee628d0f0e)
----

## Setting Variables
### Description 
Naturally, as well as reading values stored in variables, you can write values to variables. This is done, as with many other languages, using =. To set variable VAR to value 1337, you would use:

> hacker@dojo:~$ VAR=1337
> 
Note that there are no spaces around the =! If you put spaces (e.g., VAR = 1337), the shell won't recognize a variable assignment and will, instead, try to run the VAR command (which does not exist).

Also note that this uses VAR and not $VAR: the $ is only prepended to access variables. In shell terms, this prepending of $ triggers what is called variable expansion, and is, surprisingly, the source of many potential vulnerabilities (if you're interested in that, check out the Art of the Shell dojo when you get comfortable with the command line!).

After setting variables, you can access them using the techniques you've learned previously, such as:

> hacker@dojo:~$ echo $VAR
> 
> 1337
> 
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

### Approach 
![image](https://github.com/user-attachments/assets/c77db0ae-8a34-4091-8955-1f0529fe6724)
----

## Multi word Variables
### Description 
In this level, you will learn about quoting. Spaces have special significance in the shell, and there are places where you can't use them spuriously. Recall our variable setting:

> hacker@dojo:~$ VAR=1337
> 
That sets the VAR variable to 1337, but what if you wanted to set it to 1337 SAUCE? You might try the following:

> hacker@dojo:~$ VAR=1337 SAUCE
> 
This looks reasonable, but it does not work, for similar reasons to needing to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word (SAUCE in this case) as a command. To set VAR to 1337 SAUCE, you need to quote it:

> hacker@dojo:~$ VAR="1337 SAUCE"
> 
Here, the shell reads 1337 SAUCE as a single token, and happily sets that value to VAR. In this level, you'll need to set the variable PWN to COLLEGE YEAH. Good luck!

### Approach 
![image](https://github.com/user-attachments/assets/3369eb70-ef41-434f-9f71-ddbb77f462db)
----

##  Exporting Variables
### Description 
Here, the child shell received the value of VAR and was able to print it out! You can also combine those first two lines.

> hacker@dojo:~$ export VAR=1337
> 
> hacker@dojo:~$ sh
> 
> $ echo "VAR is: $VAR"
> 
> VAR is: 1337
> 
In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported (e.g., not inherited by /challenge/run). Good luck!

### Approach
![image](https://github.com/user-attachments/assets/0ccd2464-7e9a-443d-86fa-db6c1a37b843)
---

## Printing Exported Variables
### Description 
There are multiple ways to access variables in bash. echo was just one of them, and we'll now learn at least one more in this challenge.

Try the `env` command: it'll print out every exported variable set in your shell, and you can look through that output to find the `FLAG` variable!
### Approach

![image](https://github.com/user-attachments/assets/2430a275-ad56-421c-bc57-be1d85f111ef)
---

## Storing Command Output
### Description 
In the course of working with the shell, you will often want to store the output of some command into a variable. Luckily, the shell makes this quite easy using something called Command Substitution! Observe:

> hacker@dojo:~$ FLAG=$(cat /flag)
> 
> hacker@dojo:~$ echo "$FLAG"
> 
> pwn.college{blahblahblah}
> 
> hacker@dojo:~$
> 
Neat! Now, you practice. Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!
### Approach 
![image](https://github.com/user-attachments/assets/689026a4-8e08-445b-ac08-2c6a9edc663c)
---

## Reading Input 
We'll start with reading input from the user (you). That's done using the aptly named read builtin, which reads input!

Here is an example using the -p argument, which lets you specify a prompt (otherwise, it would be hard for you, reading this now, to separate input from output in the example below):

> hacker@dojo:~$ read -p "INPUT: " MY_VARIABLE
> 
> INPUT: Hello!
> 
> hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
> 
> You entered: Hello!
> 
Keep in mind, read reads data from your standard input! The first Hello!, above, was inputted rather than outputted. Let's try to be more explicit with that. Here, we annotated the beginning of each line with whether the line represents INPUT from the user or OUTPUT to the user:

>  INPUT: hacker@dojo:~$ echo $MY_VARIABLE
> 
> OUTPUT:
> 
>  INPUT: hacker@dojo:~$ read MY_VARIABLE
> 
>  INPUT: Hello!
> 
>  INPUT: hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
> 
> OUTPUT: You entered: Hello!
> 
In this challenge, your job is to use read to set the PWN variable to the value COLLEGE. Good luck!

### Approach 
![image](https://github.com/user-attachments/assets/7cdcc802-620f-42ce-8870-819db9977788)
---

## Raeding Files
### Description 
Often, when shell users want to read a file into an environment variable, they do something like:

> hacker@dojo:~$ echo "test" > some_file
>
> hacker@dojo:~$ VAR=$(cat some_file)
> 
> hacker@dojo:~$ echo $VAR
> 
> test
> 
This works, but it represents what grouchy hackers call a "Useless Use of Cat". That is, running a whole other program just to read the file is a waste. It turns out that you can just use the powers of the shell!

Previously, you read user input into a variable. You've also previously redirected files into command input! Put them together, and you can read files with the shell.

> hacker@dojo:~$ echo "test" > some_file
> 
> hacker@dojo:~$ read VAR < some_file
> 
> hacker@dojo:~$ echo $VAR
> 
> test
> 
What happened there? The example redirects some_file into the standard input of read, and so when read reads into VAR, it reads from the file! Now, use that to read /challenge/read_me into the PWN environment variable, and we'll give you the flag! The /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command!

### Approach 

<img width="542" alt="image" src="https://github.com/user-attachments/assets/33eacef7-9cd2-451b-a5c0-d548e69a6f07">
---
