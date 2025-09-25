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
- `{dir1,dir2}` : putting curly braces around multiple directories creates subdirectories in a directory of your choice
  ### Packaging and Compression
  `cut` : ONLY USED ON FILES! extract portions of lines (use a delimiter `-d:` uses a colon for fields since that is what separates fields in the program. you can select portions by fields -f 1,6 (fields 1 and 6 or by character positions `-c 1-5` shows 1-5 characters for each line in a file)

## Useful commands
- `head -n 6` : displays the first 6 lines in a file
- `wc` : word count -l count lines -w count words
- `sort` : sorts alphabetically. (-t defines the delimiter -n sort numerically -k3 sort by 3rd field (k specifies the key or field)
- `uniq` : removes or identifies duplicate lines. -c prefixes lines with the number of occurences
  

## File Archiving and Compression
- `tar` : used to create an archive
  - `-cvf` : c tells tar to create a new archive, v (verbose) prints out the names of the files going in the archive (optional) f is followed by the name of    the archive
  - the archive name needs to have the extension `.tar` Ex. tar -cvf test_archive.tar test_dir
  - to view the contents of the archive, just remove the name of the folder you are archiving
  - `-xvf` : x extracts the archive. -C nameofadirectory added after extracting adds the extracted files to the new directory. (tar -xvf test_archive.tar -C    extracted_tar)
  - `gzip` : use before the name of the directory you want to compress to compress it. The new directory will end in .tar.gz
  - `ls -lh nameofarchive.tar.gz` : shows the size of the archive in a readable format.
  - You can also compress and archive at the same time (tar -czvf test_combined.tar.gz test_dir)
  - Change the c for t to view the contents without extracting (tar -czvf test_combined.tar.gz test_dir)
 - `zip` : to create a zip archive (more compatible for Windows)
   - `-r` : tells zip to work recursively
   - `unzip -d` : unzips the file (-d specifies the directory the zip files will go into, just name after the d. If there is no name, unzip will create it)

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
- `$(date +%Y-%m-%d)` : to get todays date. Remove the dollar sign and parentheses if alone
- `^d` : means starts with the letter d
- `wc -l` : outputs number of lines

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
- `export` : used to create an env variable (export MY_ENV_VAR="Hello!") export makes the variable available to child processes
- `PATH` : tells the system where to look for executable files
  - to add a directory to the PATH (export PATH="$PATH:$HOME/my_scripts") adds my_scripts path from your home directory to the PATH env variable
- `source` : executes and reads commands without restarting the terminal
- `$SHELL` : specifies the shell you ae using
- `TERM` : Specifies the type of terminal to emulate when running the shell
- `unset` : used to unset a variable (even if you unset a var that was added to your bash file, it will recreate in a new terminal)

## Disk Management
- `df ~` : check disk space usage (add -h to make it more readable)
- `du ~` : lists the space usage for every file in home (add -sh before ~ to "summarize" to show total size of everything in the directory)
- `du -h --max-depth=1 ~` : shows size of subdirectories 1 level deep
- `du -sh ~/*` : shows size of all non-hidden files and directories under home

  ### Virtual Disks
  - `dd if=/dev/zero of=virtual.img bs=1M count=256` : `dd` to copy and convert files `if=/dev/zero` input file that provides endless zeros `of=virtual.img` is the output file `bs=1M` block size is 1 megabyte therefore `count=256` will result in 256MB for the file
  - `sudo mkfs.ext4 virtual.img` : after setting up a virtual disk you need to add a filesystem to it. Here we added the ext4 filesystem
  - `sudo mkdir mnt/vdisk` : make a directory for the virtual disk (`mnt` is a directory commonly used to mounting filesystems)
  - `sudo mount -o loop virtual.img /mnt/virtualdisk` : command to mount the vdisk.img (the filesystem) to the directory you created (`-o loop` tells the system to treat the file as if it were a real disk)
  - `sudo umount /mnt/virtualdisk` : to unmount the filesystem from the directory
 
## Pipelines
  - `&&` : logical AND operator, used in between commands to run commands in order if the preceding command succeeds
  - `||` : or operator
  - `which` : checks if a program is installed when you name the program after which


