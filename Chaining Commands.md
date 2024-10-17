### CHAINING COMMANDS

## CHALLENGE 1: CHAINING WITH SEMI COLON

- DOCUMENTATION:
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines

- THOUGHT PROCESS:
In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon

- SOLUTION:
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{4banYDHON5XHN-w0dQbpzfB8LHQ.dVTN4QDLyMDO0czW}
```

## CHALLENGE 2: FIRST SHELL SCRIPT

- DOCUMENTATION:
We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix):
```
echo COLLEGE > pwn
cat pwn
```
And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.

- THOUGHT PROCESS:
   Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash
- SOLUTION:
![image](https://github.com/user-attachments/assets/252df380-1b5c-4dd2-8874-149a99c4346b)

## CHALLENGE 3: REDIRECTING SCRIPT OUTPUT
- DOCUMENTATION:
Let's try something a bit trickier! You've piped output between programs with |, but so far, this has just been between one command's output and a different command's input. But what if you wanted to send the output of several programs to one command? There are a few ways to do this, and we'll explore a simple one here: redirecting output from your script!

As far as the shell is concerned, your script is just another command. That means you can redirect its input and output just like you did for commands in the Piping module! For example, you can write it to a file
- THOUGHT PROCESS:
In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command

- SOLUTION:
![image](https://github.com/user-attachments/assets/5bd36761-6bf1-4b33-b736-0c6bec406df3)

## CHALLENGE 4: EXECUTABLE SHELL SCRIPTS

- DOCUMENTATION:
You have written your first shell script, but calling it via bash script.sh is a pain. Why do you need that bash?

When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.
- THOUGHT PROCESS:
Try that here! Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash

- SOLUTION:
```
hacker@chaining~executable-shell-scripts:~$ chmod a+x x.sh
hacker@chaining~executable-shell-scripts:~$ /x.sh
bash: /x.sh: No such file or directory
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{IT9rFdr5VaE9DfCo5-YuiBn8Avd.dRzNyUDLyMDO0czW}
```

