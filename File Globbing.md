# FILE GLOBBING # 

## CHALLENGE 1: Matching with *

- DOCUMENTATION:
  This talks about the * operator and how it is used as a wildcard and replaces the argument with any pattern that matches
  
- THOUGHT PROCESS:
  IN this challenge we had to cd to the challenge directory but only using an argument of size 4

- SOLUTION:
  I ran this code,
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
```
and I received the following output,

  ```
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{IxrllSPwA27BHJvjMBCjUCCNzSE.dFjM4QDLyMDO0czW}
  ```
## CHALLENGE 2: Mathing with ?

- DOCUMENTATION:
  Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character
  
- THOUGHT PROCESS:
  Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag

- SOLUTIONS:  
  I ran this command,
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run

```

  received this output,
  ```
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{sZugMPQiFgxC4dV7I2B8qa5DCgj.dJjM4QDLyMDO0czW}
  ```


## CHALLENGE 3: Matching with [] 

- DOCUMENTATION:
  Next, we will cover []. The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

- THOUGHT PROCESS:
  I had to cd to /challenge/files and run a single arguemnt that will match with all file_b, file_a, file_s, and file_h, so I had to use the [], so I could check for all the values
  

- SOLUTION:   
I ran this command,
  ```
  hacker@globbing~matching-with-:~$ cd /challenge/files
  hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]

  ```
  and I recieved this output,
  ```
  You got it! Here is your flag!
  pwn.college{Myc6BiGQPHGDyMWjm6zyLFCtSR_.dNjM4QDLyMDO0czW}

  ```

## CHALLENGE 4: Mathing Paths with []  

- DOCUMENTATION:
  Globbing happens on a path basis, so you can expand entire paths with your globbed arguments
  
- THOUGHT PROCESS:
  IN this challenge I had to bracket glob into all the 4 files when I ran /challenge/run

- SOLUTION:
  I ran this code,
```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
```
and I received the following output,

  ```
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{IxrllSPwA27BHJvjMBCjUCCNzSE.dFjM4QDLyMDO0czW}
  ```
## CHALLENGE 2: Mathing with ?

- DOCUMENTATION:
  Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character
  
- THOUGHT PROCESS:
  Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag

- SOLUTIONS:  
  I ran this command,
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run

```

  received this output,
  ```
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{sZugMPQiFgxC4dV7I2B8qa5DCgj.dJjM4QDLyMDO0czW}
  ```


## CHALLENGE 3: Matching with [] 

- DOCUMENTATION:
  Next, we will cover []. The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

- THOUGHT PROCESS:
  I had to cd to /challenge/files and run a single arguemnt that will match with all file_b, file_a, file_s, and file_h, so I had to use the [], so I could check for all the values
  

- SOLUTION:   
I ran this command,
  ```
  hacker@globbing~matching-with-:~$ cd /challenge/files
  hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]

  ```
  and I recieved this output,
  ```
  You got it! Here is your flag!
  pwn.college{Myc6BiGQPHGDyMWjm6zyLFCtSR_.dNjM4QDLyMDO0czW}

  ```

  
## CHALLENGE 4: Matching paths with [] 

- DOCUMENTATION:
  Globbing happens on a path basis, so you can expand entire paths with your globbed arguments

- THOUGHT PROCESS:
  I had to cd to /challenge/files and run a single arguemnt that will match with all file_b, file_a, file_s, and file_h, so I had to use the [], so I could check for all the values
  

- SOLUTION:   
I ran this command,
  ```
  hacker@globbing~matching-with-:~$ cd /challenge/files
  hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]

  ```
  and I recieved this output,
  ```
  You got it! Here is your flag!
  pwn.college{Myc6BiGQPHGDyMWjm6zyLFCtSR_.dNjM4QDLyMDO0czW}

  ```

  ## CHALLENGE 5: Exclusionary Globbing 

- DOCUMENTATION:
  Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:

- THOUGHT PROCESS:
  In this challenge, I had to run all the files that didin't start with p w n. So I had to follow the syntax  

- SOLUTION:   
I ran this command,
```
 hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*

```
  and I recieved this output,
  ```
  You got it! Here is your flag!
pwn.college{w8YElXSjbpUoAwmAI1Snf7RipgE.dZjM4QDLyMDO0czW}

  ```
