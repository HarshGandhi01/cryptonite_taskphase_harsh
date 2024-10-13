# SHELL VARIABLES

## CHALLENGE 1: PRINTING VARIABLES  

- DOCUMENTATION: Let's start with printing variables out. The /challenge/run program will not, and cannot, give you the flag, but that's okay, because the flag has been put into the variable called "FLAG"! Just have your shell print it out!

You can accomplish this using a number of ways, but we'll start with echo. This command just prints stuff. For example:

hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
You can also print out variables with echo, by prepending the variable name with a $. For example, there is a variable, PWD, that always holds the current working directory of the current shell. 

- THOUGHT PROCESS
  As is given in the challenge, we have to run the echo shell command using the arguemnt of '$' as we are using a variable

- SOLUTION:
  I ran this commandm
  ```
  hacker@variables~printing-variables:~$ echo $FLAG
  ```

## CHALLENGE 3: MULTI-WORD VARIABLE

- DOCUMENTATION:
  In this level, you will learn about quoting. Spaces have special significance in the shell, and there are places where you can't use them spuriously. Recall our variable setting:

hacker@dojo:~$ VAR=1337
That sets the VAR variable to 1337, but what if you wanted to set it to 1337 SAUCE? You might try the following:

hacker@dojo:~$ VAR=1337 SAUCE
This looks reasonable, but it does not work, for similar reasons to needing to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word (SAUCE in this case) as a command. To set VAR to 1337 SAUCE, you need to quote it:


- THOUGHT PROCESS
  As is given in the challenge, we have to run the shell command to assign the value of 'COLLEGE YEAH' to the varialbe 'PWN', to get the flag

- SOLUTION:
  I ran this commandm
  ```
  hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
  ```
  and recieved this output,
  ```
  You've set the PWN variable properly! As promised, here is the flag:
  pwn.college{AZo8BaUOEMWxehtiWT4sz3vFdMQ.dlTN1QDLyMDO0czW}
  ```## CHALLENGE 3: MULTI-WORD VARIABLE

- DOCUMENTATION:
  In this level, you will learn about quoting. Spaces have special significance in the shell, and there are places where you can't use them spuriously. Recall our variable setting:

hacker@dojo:~$ VAR=1337
That sets the VAR variable to 1337, but what if you wanted to set it to 1337 SAUCE? You might try the following:

hacker@dojo:~$ VAR=1337 SAUCE
This looks reasonable, but it does not work, for similar reasons to needing to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word (SAUCE in this case) as a command. To set VAR to 1337 SAUCE, you need to quote it:


- THOUGHT PROCESS
  As is given in the challenge, we have to run the shell command to assign the value of 'COLLEGE YEAH' to the varialbe 'PWN', to get the flag

- SOLUTION:
  I ran this commandm
  ```
  hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
  ```
  and recieved this output,
  ```
  You've set the PWN variable properly! As promised, here is the flag:
  pwn.college{AZo8BaUOEMWxehtiWT4sz3vFdMQ.dlTN1QDLyMDO0czW}
  ```


    ## CHALLENGE 2: SETTING VARIABLES  

- DOCUMENTATION: Naturally, as well as reading values stored in variables, you can write values to variables. This is done, as with many other languages, using =. To set variable VAR to value 1337, you would use:

hacker@dojo:~$ VAR=1337
Note that there are no spaces around the =! If you put spaces (e.g., VAR = 1337), the shell won't recognize a variable assignment and will, instead, try to run the VAR command (which does not exist).

Also note that this uses VAR and not $VAR: the $ is only prepended to access variables. In shell terms, this prepending of $ triggers what is called variable expansion, and is, surprisingly, the source of many potential vulnerabilities (if you're interested in that, check out the Art of the Shell dojo when you get comfortable with the command line!).

After setting variables, you can access them using the techniques you've learned previously, such as:

hacker@dojo:~$ echo $VAR
1337
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

You can accomplish this using a number of ways, but we'll start with echo. This command just prints stuff. For example:

hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
You can also print out variables with echo, by prepending the variable name with a $. For example, there is a variable, PWD, that always holds the current working directory of the current shell. 

- THOUGHT PROCESS
  As is given in the challenge, we have to run the shell command to assign the value of 'COLLEGE' to the varialbe 'PWN'

- SOLUTION:
  I ran this commandm
  ```
  hacker@variables~setting-variables:~$ PWN=COLLEGE 
  ```
  and recieved this output,
  ```
  You've set the PWN variable properly! As promised, here is the flag:
  pwn.college{AZo8BaUOEMWxehtiWT4sz3vFdMQ.dlTN1QDLyMDO0czW}
  ```

## CHALLENGE 4: EXPORTING VARIABLES

- DOCUMENTATION:
  By default, variables that you set in a shell session are local to that shell process. That is, other commands you run won't inherit them. You can experiment with this by simply invoking another shell process in your own shell, like so:

hacker@dojo:~$ VAR=1337
hacker@dojo:~$ echo "VAR is: $VAR"
VAR is: 1337
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is: 
In the output above, the $ prompt is the prompt of sh, a minimal shell implementation that invoked as a child of the main shell process. And it does not receive the VAR variable!

This makes sense, of course. Your shell variables might have sensitive or weird data, and you don't want it leaking to other programs you run unless it explicitly should. How do you mark that it should? You export your variables. When you export your variables, they are passed into the environment variables of child processes. You'll encounter the concept of environment variables in other challenges, but you'll observe their effects here. Here is an example:

hacker@dojo:~$ VAR=1337
hacker@dojo:~$ export VAR
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is: 1337
Here, the child shell received the value of VAR and was able to print it out! You can also combine those first two lines.

hacker@dojo:~$ VAR=1337
That sets the VAR variable to 1337, but what if you wanted to set it to 1337 SAUCE? You might try the following:

hacker@dojo:~$ VAR=1337 SAUCE
This looks reasonable, but it does not work, for similar reasons to needing to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word (SAUCE in this case) as a command. To set VAR to 1337 SAUCE, you need to quote it:


- THOUGHT PROCESS
  As is given in the challenge, we have to run the shell command to assign the value of 'COLLEGE YEAH' to the varialbe 'PWN', to get the flag

- SOLUTION:
  I ran this commandm
  ```
  hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
  ```
  and recieved this output,
  ```
  You've set the PWN variable properly! As promised, here is the flag:
  pwn.college{AZo8BaUOEMWxehtiWT4sz3vFdMQ.dlTN1QDLyMDO0czW}
  ```
  
