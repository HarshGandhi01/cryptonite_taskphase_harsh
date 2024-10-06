### COMPREHENDING COMMANDS ####

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


## CHALLENGE 3: POSITION THY SLEF

- DOCUMENTATION:
This introcued the 'cd' command which allows us to change directories at out convinence.
This works by invoking cd with the directory path as the argument, if no argument is given, then cd goes to the home directory

- THOUGHT PROCESS:
The instructions stated that once I invoke the '/challenge/run' it will tell me which directory to go to to get the flag, so I did that

- SOLUTION: 
I ran this command,
```
hacker@paths~position-thy-self:~$ /challenge/run
```
and recieved this output,
```
Incorrect...
You are not currently in the /var/log directory.
Please use the `cd` utility to change directory appropriately.
```

Hence, then I ran this,
```
hacker@paths~position-thy-self:~$ cd /var/log
hacker@paths~position-thy-self:/var/log$ /challenge/run
```

and I recieved this output,
```
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{41Eiu9MPrhcvtJtcBb7HTCc08Mb.dZDN1QDLyMDO0czW}
```


## CHALLENGE 4: POSITION ELSEWHERE

- DOCUMENTATION: 
This also talks about the cd command, which changes the current working directory of the user, in the shell, we have to once again, run the /challenge/run program from a directory specified by the program

- THOUGHT PROCESS:
The instruction specified to run the /challenge/run program from the directory specified by the program, so I did that

- SOLUTION:
I ran the following command, to find the real directory of the /challenge/run
```hacker@paths~position-elsewhere:~$ /challenge/run```

and recieved this output,
```
Incorrect...
You are not currently in the /sys/kernel directory.
Please use the `cd` utility to change directory appropriately.
```

so then I ran this,
```
hacker@paths~position-elsewhere:~$ cd /sys/kernel
hacker@paths~position-elsewhere:/sys/kernel$ /challenge/run
```

and recieved this output,
```
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QzN7Z9xGDT0L4puioWePpZpFVoE.ddDN1QDLyMDO0czW}
```


## CHALLENGE 5: POSITION YET ELSEWHERE

- DOCUEMENTATION:
This has the same documentation as the previous question

- THOUGHT PROCESS:
Same thought process as the previous question

- Solution:
Similiar solution to previous challenge


## CHALLENGE 6: IMPLICTI RELATIVE PATHS, FROM /

- DOCUMENTATION:
The documentation talks about how it dosen't matter what directory the user is in, if he is using absolute paths, but the CWD does matter for relative paths

- THOUGHT PROCESS:
We have to run /challenge/run using a relative path, using the cwd of /
So I first CDd to the the root directory, from there I ran the challenge/run, as that is a relative path and not an absolute

- SOLUTION:
I ran these 2 commands,
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
```

and I recieved this output,
```
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{c0aiDmTZpuusHUx905o7lABFlEK.dlDN1QDLyMDO0czW}
```


## CHALLENGE 7: EXPLICIT RELATIVE PATHS, FROM /

- DOCUMENTATION:
This talks about the uses of '.' and '..' in file systems for linux and windows.

- THOUGHT PROCESS:
We have to use . and .. to call the /challenge/run command, so first I CDd to the root directory and then I ran the challenge-run using ./

-S OLUTION:
I ran the following commands,
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
```

and I recieved the following output,
```
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{o2xKln7XBzZiJhrOajWDnXKlYif.dBTN1QDLyMDO0czW}
```


## CHALLENGE 8: IMPLICIT RELATIVE PATH

- DOCUMENTAION:
This talks about how to explicit define a path for the file so that the linux file system does not accidentally run all the programs with the same name

- THOUGHT PROCESS:
As we have to execute the run program specifically using '.', I tried to run the /challenge/run command to see what it shows, I recieved the follwoing output
```
Incorrect...
You are not currently in the /challenge directory.
Please use the `cd` utility to change directory appropriately
```

so, after that I ran the following set of code,
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
the second command explicitely run the run program from the challenge directory
```

I recieved the follwoing output
```
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wXosx4JAoxKdgKjbMk0kHTJml3r.dFTN1QDLyMDO0czW}
```


# CHALLENGE 9: HOME SWEET HOME

- DOCUMENTATION:
This part talk about the usage of ~ in file systems, ~ expands to /home/hacker

- THOUGHT PROCESS:
In this challenge we have to invoke the /challenge/run command with an argument, with 3 constraints,
Hence, we have to use ~ as ~ expands to /home/hacker

- SOLUTION:
Since we know that the argument can only be 3 characters or less, I tried doing this
```
hacker@paths~home-sweet-home:~$ /challenge/run ~a
```

however this apporach was wrong as,
The argument you provided is not an absolute path!

After trying with many different combinations, I was stuck, then I realized the ~ expands to /home/hacker and not /home/hacker/
hence afterwards I tried this,
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
```
and I recieved the following output,
```
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{UFYlCdXE_A8izs3F3qpzGxKmZh-.dNzM4QDLyMDO0czW}
```


################# END OF MODULE 2 ##############



