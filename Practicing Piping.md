# PRACTICING PIPING #

## CHALLENGE 1: Redirecting Output

- DOCUMENTATION:
  First, let's look at redirect stdout to files. You can accomplish this with the > character, as so:
  This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:

- THOUGHT PROCESS:
  In this challenge, you must use this input redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase). So all I had to do was to run the syntax
  

- SOLUTION:   
I ran this command,
  ```
  hacker@piping~redirecting-output:~$ echo PWN > COLLEGE

  ```
  and I recieved this output,
```
  Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{YLcLA2WW9Wv5eN0WK3YDZPv0M11.dRjN1QDLyMDO0czW}

```

## CHALLENGE 2: Redirecting more output

- DOCUMENTATION:
  Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level,
  /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

- THOUGHT PROCESS:
  I had to redirect the output of /challenge/run to myflag file
  

- SOLUTION:   
I ran this command,
  ```
  hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
  hacker@piping~redirecting-more-output:~$ cat myflag

  ```
  and I recieved this output,
  ```
  [FLAG] Here is your flag:
  [FLAG] pwn.college{wbZpA9lXB0IPBSF-wXkT6sZtvJB.dVjN1QDLyMDO0czW}

  ```
## CHALLENGE 3: APPENDING OUTPUT

-DOCUMENTATION:  

A common use-case of output redirection is to save off some command results for later analysis. Often times, 
you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.

You can redirect input in append mode using >> instead of >, as so:

THOUGHT PROCESS:  
I had to run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file.
To solve this, I had to follow the syntax

-SOLUTION:  
```bash
hacker@piping~appending-output:~$ /challenge/run >> ~/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat ~/the-flag
 |
\|/ This is the first half:
 v
pwn.college{UX7o86zRTky3yokzi0Tl4zebzb6.ddDM5QDLzgTN0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

## CHALLENGE 4: REDIRECTING ERRORS

-DOCUMENTATION:  
Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File Descriptor numbers. A File Descriptor (FD) is a number the describes a communication channel in Linux. You've already been using them, even though you didn't realize it.
Redirecting errors is pretty easy from this point. If you have a command that might produce data via standard error (such as /challenge/run)
You can redirect standard error (FD 2) to the errors.log file. Furthermore, you can redirect multiple file descriptors at the same time! For example:

-THOUGHT PROCESS:  
In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions

-SOLUITION:  

I ran the following program:
```
Connected!
hacker@piping~redirecting-errors:~$ /challenge/run 2> instructions
hacker@piping~redirecting-errors:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[FAIL] You did not satisfy all the execution requirements.
[FAIL] Specifically, you must fix the following issue:
[FAIL]   You have not redirected anything for this process' stderr.
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{IkpkmVehCZoshS-CdRLDKvdMvjB.ddjN1QDLzgTN0czW}
```

## CHALLENGE 5: REDIRECTING INPUT

-DOCUMENTATION:  
Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:

-THOUGHT PROCESS:  
In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

-SOLUITION:  

I ran the following program:
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{080Okrpb5OlFcGleRr4RZNn2hR3.dBzN1QDLzgTN0czW}
hacker@piping~redirecting-input:~$
```
