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

  ## CHALLENGE 5: PRINTING EXPORTED VARIABLES

  - DOCUMENTATION:
    There are multiple ways to access variables in bash. echo was just one of them, and we'll now learn at least one more in this challenge.
    Try the env command: it'll print out every exported variable set in your shell, and you can look through that output to find the FLAG variable!
    
- THOUGHT PROCESS:
  AS was said in the documentation, I had to run the env command, to get all the exported variables in the system

- SOLUTION:
  I ran this command
  ```
  hacker@variables~printing-exported-variables:~$ env
  ```
  I recieved this output,
```
  SHELL=/run/dojo/bin/bash
COLORTERM=truecolor
TERM_PROGRAM_VERSION=1.89.1
HOSTNAME=variables~printing-exported-variables
VSCODE_PROXY_URI=https://pwn.college/workspace/code/proxy/{{port}}/
PWD=/home/hacker
DOJO_AUTH_TOKEN=a409579e1daf2b44cc0f21020e310a914539a624a61b475f658c0afdfc794e93
VSCODE_GIT_ASKPASS_NODE=/nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node
HOME=/home/hacker
LANG=C.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=
01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90:                                                                  GIT_ASKPASS=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/extensions/git/dist/askpass.sh
FLAG=pwn.college{kegg_aErvGLPaGeJKPr4WWFEqr6.dhTN1QDLyMDO0czW}
VSCODE_GIT_ASKPASS_EXTRA_ARGS=
LESSCLOSE=/usr/bin/lesspipe %s %s
TERM=xterm-256color
LESSOPEN=| /usr/bin/lesspipe %s
VSCODE_GIT_IPC_HANDLE=/tmp/vscode-git-97ce16f00b.sock
SHLVL=2
LC_CTYPE=C.UTF-8
VSCODE_GIT_ASKPASS_MAIN=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/extensions/git/dist/askpass-main.js
BROWSER=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/helpers/browser.sh
PATH=/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/s
bin:/bin                                                                                                                                                                                             NODE_EXEC_PATH=/nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node
TERM_PROGRAM=vscode
VSCODE_IPC_HOOK_CLI=/tmp/vscode-ipc-81874345-ed56-4b9b-930c-aabf34b0f373.sock
_=/run/workspace/bin/env
```
and the flag was present in that output,

## CHALLENGE 6: SORTING COMMAND OUTPUT

- DOCUMENTATION:
  

  
  
