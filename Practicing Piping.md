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
