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

## CHALLENGE 6: GREPPING STORED RESULTS

-DOCUMENTATION:  
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!



-THOUGHT PROCESS:  
In this level,I have to,

Redirect the output of /challenge/run to /tmp/data.txt.
This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
Grep that for the flag!

-SOLUITION:  

I ran the following program:
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{81NcCNzOU71MlAEXMr7o-IdP_06.dhTM4QDLzgTN0czW}
```

## CHALLENGE 7: GREPPING LIVE OUTPUT

-DOCUMENTATION:  
It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can use this using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:

-THOUGHT PROCESS:  
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. Grep for the flag!

-SOLUITION:  

I ran the following program:
```
Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{0D7VtydG8XcoP-plxYs2tTE_Oux.dlTM4QDLzgTN0czW}
```

## CHALLENGE 8: GREPPING ERRORS

-DOCUMENTATION:  
You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)


-THOUGHT PROCESS:  
Like the last level, this level will overwhelm you with output, but this time on standard error. Grep through it to find the flag

-SOLUITION:  

I ran the following program:
```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{g7pEwkOzTVPSRFSNx6lQxH8D_Eo.dVDM5QDLzgTN0czW}
hacker@piping~grepping-errors:~$
```

## CHALLENGE 8: DUPLICATING PIPED DATA WITH TEE

-DOCUMENTATION:  
When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired: for example, you might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???").
Luckily, there is a solution! The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line

-THOUGHT PROCESS:  
This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!

-SOLUITION:  

I ran the following program:
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn |tee output | /challenge/college
Processing...
WARNING: you are overwriting file output with tee's output...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "4tfLWu_k"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret "4tfLWu_k"
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret "4tfLWu_k" | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{4tfLWu_k7adZwApNrJqngrg7-GO.dFjM5QDLzgTN0czW}
```


## CHALLENGE 9: WRITING TO MULTIPLE PROGRAMS

-DOCUMENTATION:  
Luckily, Linux follows the philosophy that "everything is a file". This is, the system strives to provide file-like access to most resources, including the input and output of running programs! The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line (such as tee) and hook it up to the input or output side of a program!

This is done using what's called Process Substitution. If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary file that it will create. This isn't a real file, of course, it's what's called a named pipe, in that it has a file name:


-THOUGHT PROCESS:  
In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!

-SOLUITION:  

I ran the following program:
```
root@DESKTOP-MPJ395R:~# ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{Ae2CSNZ9KT5mDWENsPh7LsX3K0h.dBDO0UDLzgTN0czW}
hacker@piping~writing-to-multiple-programs:~$
```

## CHALLENGE 10: SPLIT PIPING

-DOCUMENTATION:  
Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of >(), 2>, and |. How to do it is a task I'll leave to you.


-THOUGHT PROCESS:  
In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program

-SOLUITION:  

I ran the following program:
```
Connected!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{UmUy2jHPwsMIwxMyxMzWDHE37FV.dFDNwYDLzgTN0czW}
hacker@piping~split-piping-stderr-and-stdout:~$
```



