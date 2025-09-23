# Basic Linux Commands

## Navigation
- `pwd` : print working directory
- `ls` : list what is in the current directory (ls .. - lists files in parent directory)
- `cd` : use cd to go to home directory (use cd to move to any directory)
- `mkdir` : make directory
- `ls *.txt` : list all files ending with .txt (`* is a wildcard`)
- `mv` : move file (mv hello_world.txt ..)
- `..` : parent directory (helps move up the tree)
- `~` : home directory
- `-` : go to previous directory
  
## File commands
- `touch newfile.txt` : create an empty file (named newfile.txt)
- `echo` : use echo "Hello World" > hello.txt (add the text "Hello World" to the file named hello.txt) (also creates the file if not created yet)
- `cat` : used to view the text in a file
- `cp` : copy (cp hello.txt goodbye.txt - adds the text from hello.txt to goodbye.txt)
- `rm` : remove (deleted files don't go to recycle)
- `>>` : adds a new line to a file (echo "New line created" >> hello_linux.txt)
- `tree` : visualizes directories
- `-p` : makes a parent directory if there isnt one
- `cp -r` : copy directory and add to another
- `cat << EOF > nameofdocument.txt` : creates a multiline document
- `nano` : edit a file text editor
- `find` : searches for files (find . -name "*.txt" -- find all .txt files) find all in the current directory the name that ends with .txt
- `which` : find the location of executable files

## Wildcards
- `*` : matches any number of characters
- `?` : matches any single character
- `[abc]` : Matches any one character listed in the brackets

## Shortcuts
- `cat h (plus tab)` : autocompletes to cat hello.txt after you press tab
- `cat /etc` : displays file contents in etc
  - add `| sort` to sort alphabetically
  - add `|grep -E "admin" to find lines containing the word "admin"
- `Ctrl+C` : stop a running command
- `Ctrl+L` or `clear`: clear terminalls /home

## Help
- `man` : guide for commands (q to quit)
  - Use up and down keys to move through manual
  - Use `space` to move forward on page
  - use `b` to move back a page
  - `/` by a word to find that word
    - `n` to move to next occurance of word
    - `N` to move to previous occurance of word
- `--help` : brief description of a command (ls --help)
- `apropos` : lists commands and descriptions based off the word provided (used when you aren't sure what command to use)
  - `apropos file | grep create` : show commands related to file that also mention create
 
## User Groups and File Permissions
- `whoami` : what is the username of the person logged in
- `sudo` : allows regular users to execute commands as the superuser
- `sudo adduser` : adds a user
- `sudo groupadd` : adds a group
- `id` : lists user ID, group ID, and any groups that the user belongs to
- `sudo usermod -aG party beth` : adds user to a supplementary group (usermod modifies user accounts -aG adds user to a supp group -g adds use to primary group)
- `groups` : lists what groups a user is in
- `chown` : change owndership of a file (sudo chown beth:beth /pathToFile)
- `chmod` : change file permissions (sudo chmod 750 /pathToFile -- Owner(7) = Read(4) + Write(2) + Execute(1) Group(5) = Read(4) + Execute(1))

## Environment Variables
-`my_var="Hello, Linux` : to create a **shell** variable
  - use `$` to echo the variable (echo $my_var)
- `env` : used to find all environment variables

