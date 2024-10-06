# COMPREHENDING COMMANDS #

## CHALLENGE 1: CAT: NOT THE PET, BUT THE COMMAND!

- DOCUMENTATION:
  The command 'cat' is used to read files in linux


- THOUGHT PROCESS:  
    As the instructions stated, I had to read the 'flag' file with the cat command

- SOLUTION:  
Following the instructions, I ran the following command
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
```
and I received the following output,
```
pwn.college{MKM6SNpkbdno5ZIC57HiGd_O4AM.dFzN1QDLyMDO0czW}
```
## CHALLENGE 2: CATTING ABSOLUTE PATHS

- DOCUMENTATION:  
  The documentation stated that we can specify an argument as 'cat's argument, that argument begin an absolute path

- THOUGHT PROCESS:  
As stated in the instructions, I had to read out the 'flag' file, which was located in the /file directory, using the absolute path as argument for the cat.

- SOLUTIONS:  
  I ran this command,
  ```
  hacker@commands~catting-absolute-paths:~$ cat /flag
  ```

  received this output,
  ```
  pwn.college{kQ00JVAXXjES5h54-oj7z93sGnZ.dlTM5QDLyMDO0czW}
  ```


## CHALLENGE 3: MORE CATTING PRACTICE

- DOCUMENTATION:   
This challenge is a practice of the recent command we learned

- THOUGHT PROCESS:  
Similiar thought process as to the previous challenge.
Howver this time, we weren't allowed to cd into other directories, I had to find out the location of the flag, and use that as an argument.
- SOLUTION:   
I ran this command,
```
hacker@commands~more-catting-practice:~$ cd
```
and I recieved this output,
```
You used 'cd'! In this level, I don't allow you to change the working directory 
--- you MUST chase pass 'cat' the absolute path of where I put it on the 
filesystem (which is /lib/x86_64-linux-gnu/elfutils/flag).
```
so I ran this command next,
```
hacker@commands~more-catting-practice:~$ cat /lib/x86_64-linux-gnu/elfutils/flag
```
and recieved this output,
```   
pwn.college{Q9iAGoA0hKNNHKvBCOTXz_H5x6U.dBjM5QDLyMDO0czW}
```

## CHALLENGE 4: GREPPING FOR A NEEDLE IN A HAYSTACK

- DOCUMENTATION:   
This also talks about the grep command, that allows us to search for contents we might need in a file. This allows to save time if the file is too big.

- THOUGHT PROCESS:  
The syntax works like this : hacker@dojo:~$ grep SEARCH_STRING /path/to/file
I know that each flag is of the format "pwn.college", so we could search for this particular pattern to find our flag.
Also, I was told that the flag was located in the file /challenge/data/txt. 

- SOLUTION:  
I ran this command,
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
```
and I received this output,
```
pwn.college{0jubnepqFl6JOD0g32W_EmVxwym.ddTM4QDLyMDO0czW}
```


  
## CHALLENGE 5: LISTING FILES

- DOCUMENTATION:  
The documentation talks about the command ls, which allows us to list the files in a particular directory.

- THOUGHT PROCESS:  
  In this challenge, the /challenge/run was named something randomly, we had to list the files in /challenge to find the files
  So I cd to the /challenge folder and listed the files, to get the flag file


- SOLUTION:  
I ran this command,
```
hacker@commands~listing-files:~$ cd /challenge
hacker@commands~listing-files:/challenge$ ls
```  
and recieved this output,   
```
29241-renamed-run-8678  DESCRIPTION.md
```
the 'description.md' file had the documentation for this challenge, so logically, the flag would be in '29241-renamed...'  
hence I ran this,
```
hacker@commands~listing-files:/challenge$ ./29241-renamed-run-8678
```
and I found the flag!
```
Yahaha, you found me! Here is your flag:
pwn.college{0XqzNBulk9Q0ZsY1UA470I4m51J.dhjM4QDLyMDO0czW}
```

  
## CHALLENGE 6: TOUCHING FILES

- DOCUMENTATION:  
This talks about the use of the 'touch' command in linux, which allows us to create files

- THOUGHT PROCESS:
  In this challenge, I had to create 2 files, /tmp/pwn and /tmp/college, and then run /challenge/run to get the flag

-SOLUTION:  
I ran these commands,
```
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
```
and I received the following output,
```
Success! Here is your flag:
pwn.college{Q-XzVEoIupNGU5Ey1DrNz_EZGEX.dBzM4QDLyMDO0czW}
```

## CHALLENGE 7: REMOVING FILES

- DOCUMENTATION:
  This talks about the usage of the rm command to remove files

- THOUGHT PROCESS:
  To get the flag I had to delete a file called "delete_me".

- SOLUTION:
  I ran this command,
  ```
  hacker@commands~removing-files:~$ rm delete_me
  hacker@commands~removing-files:~$ /challenge/check
  ```
  I received the following output,
  ```
  Excellent removal. Here is your reward:
  pwn.college{MZKYOqD-wlb0_7xnCDZKNufISCf.dZTOwUDLyMDO0czW}
  ```


# CHALLENGE 8: HIDDEN FILES

- DOCUMENTATION:  
  This part talks about the usage of -a as an argument for the 'ls' command, which allows us to view hidden files.

- THOUGHT PROCESS:  
  To get the flag, I had to run the ls command with -a to find a hidden file, to find the flag.
  It was also stated that the flag was hidden in the directory "/"
  

- SOLUTION:  
  I ran the following commands
  ```
  hacker@commands~hidden-files:~$ cd /
  hacker@commands~hidden-files:/$ ls -a
  ```
  and I received the following output,
  ```
  .           .flag-187222712814125  challenge  home   lib64   mnt  proc  sbin  tmp
  ..          bin                    dev        lib    libx32  nix  root  srv   usr
  .dockerenv  boot                   etc        lib32  media   opt  run   sys   var
  ```
  so I ran this,
  ```
  hacker@commands~hidden-files:/$ cat .flag-187222712814125
  ```
  and I received this output,
  ```
  pwn.college{8Ipr1b6vdVZx5sOPRrRXuU9JC_Z.dBTN4QDLyMDO0czW}
  ```
  

  
  

################# END OF MODULE 3 ##############



