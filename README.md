# Useful and common Linux shell commands

##### how to check Hidden Files and Directories
- `ls -a`

##### The Manual, Flags
- Flags are additional specification that can be added to a command, they are usually in the form `-a`. Flags and other tools for a command can be usually found by running `COMMAND -help`

##### what is a wildcard and How to use Wildcards
- `*` any string of any length
- `?` single character
- `(STRING)` matches a specific string
- `[CHARACTER/S]` matches any character or characters within the brackets
- `[^CHARACTER/S]` excludes any character or characters within the brackets
- `!WILDCARD` excludes the wildcard selected

##### how can you do Process Management
- launching a process requires typing the name of the process: `NAME_OF_PROCESS`
- or it can be done through systemctl: `sudo systemctl start NAME_OF_PROCESS`
- stopping a process can be done with `sudo systemctl stop NAME_OF_PROCESS`
- running a process in the background (it doesn't wait for user input: `NAME_OF_PROCESS &`
- visualising background processes requires running `jobs`
- `pidof NAME_OF_PROCESS` gives the id of the process, but that can also be found with `ps aux | more` and `top` 
- processes can be suspended to the background by pressing CTRL+Z
- suspended processes can be run in the background with `bg NAME_OF_PROCESS`
- or they can be moved to the foreground with `fg %PROCESS_ID`

##### What is Currently Running on your system
- It's possible to find out what processes are currently running on a machine with `top`

##### Killing a process/Crashed Process
- It's possible to kill a process with `kill %PROCESS_ID`
	
##### What are daemon processes?
- They are special types of background processes that start at system startup and keep running forever as a service. They are started as system tasks (run as services) spontaneously. However, they can be controlled by a user via the init process.
- A diagram for daemon processes:
- ![img](https://www.tecmint.com/wp-content/uploads/2017/03/ProcessState.png)
	
##### what do 777, 400, 600, r, w, x mean?
- The the flags `+/-r`, `+/-w`, and `+/-x` stand for (add/remove) read permission, (add/remove) write permission, and (add/remove) execute permission.
- a table with the numerical meaning:

| Octal Mode Number | Description |
| ----- 			| ------ |
| 0400 | Allows the owner to read |
| 0200 | Allows the owner to write |
| 0100 | Allows the owner to execute files and search in the directory |
| 0040 | Allows group members to read |
| 0020 | Allows group members to write |
| 0010 | Allows group members to execute files and search in the directory |
| 0004 | Allows everyone or the world to read |
| 0002 | Allows everyone or the world to write |
| 0001 | Allows everyone or the world to execute files and search in the directory |

##### how to check permission for files/dir
- `ls -l NAME_OF_FILE`
- here's a diagram to interpret the output:
- ![img](https://i.imgur.com/enB6IAY.jpg)
- `stat -c %a NAME_OF_FILE` gives the permissions in numeric form.

##### How to change permissions with chmod command
- Permissions can be changed by the administrator with `sudo chmod (+/-)FLAGS`

##### how to use head, tail, sort, nl (number line), wc (word count)
- in all of the following examples, `FILE_NAME` can be substituted with `FILE_PATH/FILE_NAME`, `WILDCARD`, or `FILE_PATH/WILDCARD`
- `find FILE_NAME` returns a file matching the name, or a list of files maching the wildcard
- `cat FILE_NAME` prints to screen the contents of a file
- `head -NUMBER_OF_LINES FILE_NAME` selects (and/or prints) the first lines of a file
- `tail -NUMBER_OF_LINES FILE_NAME` selects (and/or prints) the last lines of a file
- `sort FILE_NAME` selects (and/or prints) the contents of a file in alphabetical order
- `head -NUMBER_OF_LINES FILE_NAME` prints the first lines of a file
- `nl FILE_NAME` prints the file with the lines preceded by a progressive number
- `wc FILE_NAME` prints the word count of a file
- `sed "[options/options/options/options]"` allows for the substitution of strings, in files or outputs. 

##### what are piping and redirection
- The pipe, `|`, tells the shell that we want to use the output of the command on the left as the input to the command on the right.
- To be more precise, pipes connect the `stdout` of one command to the `stdin` of the next.
- redirect, `>/>>` has the same function, but instead of passing the output to a command, it passes it to a file. The single version `>` overwrites the file contents, while the double version `>>` appends the output to the file

##### what is STDIN standard input and output
- `stdin` and `stdout` are the default input and output locations of the current session (and sessions in general). When a command with an output is run, the session trasmits it to `stdout`, and then from there to the screen. In a similar way, the session retrieves inputs from the `stdin` location.