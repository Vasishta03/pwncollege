## DESCRIPTION

So now we know how to list, read, and create files. But how do we find them? We use the find command!

The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.).

Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it. Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there! Finally, find can take a while; be patient!

## APPROACH 
first i found all the files named with flag using the `flag` command and then i just read the file using the `cat` command to find the flag. 

![image](https://github.com/user-attachments/assets/1504d7b2-4bb1-49f2-8010-e5621d716ee6)
![image](https://github.com/user-attachments/assets/ad895072-59fe-4477-9419-ac3dfeac2dcf)
