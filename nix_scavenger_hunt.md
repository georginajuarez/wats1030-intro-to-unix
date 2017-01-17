# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*
/home/cabox/workspace

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*
LICENSE  README.md  challenge_files  nix_scavenger_hunt.md  nix_scavenger_hunt_stretch.md 

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*
It provides more detailed information. It also shows me hidden files (the ones that start with .), tells me the size of each file and where it is located.

total 36K                                                                                                                     drwxrwxr-x  4 cabox cabox 4.0K Jan 16 02:28 .                                                                                 drwxr-xr-x 10 cabox cabox 4.0K Jan 16 02:28 ..                                                                                 drwxrwxr-x  8 cabox cabox 4.0K Jan 16 02:28 .git                                                                               -rw-rw-r--  1 cabox cabox 1.1K Jan 16 02:28 LICENSE                                                                           -rw-rw-r--  1 cabox cabox 2.7K Jan 16 02:28 README.md                                                                         drwxrwxr-x  7 cabox cabox 4.0K Jan 16 02:28 challenge_files                                                                   -rw-rw-r--  1 cabox cabox 5.5K Jan 16 02:28 nix_scavenger_hunt.md                                                             -rw-rw-r--  1 cabox cabox  317 Jan 16 02:28 nix_scavenger_hunt_stretch.md


* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://linux.die.net/man/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*
ls = list
a = --all
do not ignore entries starting with .
l = use a long listing format
h = --human-readable
with -l, print sizes in human readable format (e.g., 1K 234M 2G)

* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?* 
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  sbin  selinux  srv  sys  tmp  usr  var  
tmp was highlighted. I imagine it is because I'm in a container that I added and is housed in the "temporary" root directory.

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*
/home/cabox 

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*
/home/cabox 

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*
I found 3 files.

[cabox@box-codeanywhere challenge_files]$ find . -type f -name "*.demo"                                                       ./scooter-double-mamba.demo                                                                                                   ./2015_special_stuff.demo                                                                                                     ./cloaked-wookie.demo

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*
[cabox@box-codeanywhere challenge_files]$ pwd                                                                                 /home/cabox/workspace/challenge_files                                                                                         [cabox@box-codeanywhere challenge_files]$ cd ..                                                                               [cabox@box-codeanywhere workspace]$ pwd                                                                                       
/home/cabox/workspace  <--- I AM HERE, IN THE WORKSPACE DIRECTORY.


* Press the up arrow on your keyboard. *What just happened?*
I was given my last command to re-enter.

* Press the up arrow a few more times. *What do you see?*
I see the listed command shift to previously used commands, in the order they were last used. Almost like an undo/redo shortcut.

* Run the `history` command. *What do you see?*
An ordered (numbered) list of all the commands requeested during this session.

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*
cabox 

* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*
No.
cabox    pts/0        Jan 16 02:30 (54.186.244.104) 

* How long has your system been running? Use `uptime` to see, and *paste the result here:*
03:12:32 up 44 min,  1 user,  load average: 0.00, 0.00, 0.00

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*
It reports a snapshot of the current processes. I can see recent snapshot of what was going on in my system, who the user was and what command was executed, in addition to start time and a few others.

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*
It's hard to review the results until you get out of the app. The man tells me that this command displays tasks. I looks like a longer (and continually updated) version of the ps aux. 


### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*
Two files.

[cabox@box-codeanywhere challenge_files]$ find credit* 
credit_cards.txt
credit_cards2.txt 

* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*
01-15-2015

* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*
[cabox@box-codeanywhere challenge_files]$ find . -name 'modi_laboriosam.txt'      
./tmp/modi_laboriosam.txt   <--- LOCATED HERE. IN THE SUB DIR TMP

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*
I found 2 files.
[cabox@box-codeanywhere challenge_files]$ grep "WA" *.user                                                                     Britt-Erdman.user:O'Harachester, WA 37261                                                                                     Lissie-Strosin.user:Jewessfurt, WA 00816-7241 

* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*  
[cabox@box-codeanywhere challenge_files]$ grep -r "Waldo" *                                                                   serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt consectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*
I see a partial list (21%) of files that are located in the file files.txt, so a it's a list of files for my files?!

[cabox@box-codeanywhere challenge_files]$ more "files.txt"                                                                     01                                                                                                                             2015_special_stuff.demo                                                                                                       Afton-Jast.user                                                                                                               Aimee-Maggio.user                                                                                                             Alfonso-Gottlieb.user                                                                                                         Allen-Kemmer.user                                                                                                             Almina-Cormier.user                                                                                                           Alta-Lemke.user                                                                                                               Amina-McGlynn.user                                                                                                             Anabel-Hammes.user                                                                                                             Ancel-Conn.user                                                                                                               Anjali-Halvorson.user                                                                                                         Ardath-Kuvalis.user                                                                                                           Avah-Dickinson.user                                                                                                           Ayaan-Stiedemann.user                                                                                                         Aylin-Grant.user                                                                                                               Bedford-Sipes.user                                                                                                             Benita-King.user                                                                                                               Benito-Stoltenberg.user                                                                                                       Beverlee-Moen.user                                                                                                             Brad-Thiel.user                                                                                                               Brayan-Douglas.user                                                                                                           Bria-Satterfield.user                                                                                                         Bridgette-Reichel.user                                                                                                         --More--(21%)

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*
I see a silmilar list to the one run by 'ls -alh' but it only shows me a partial list. Doesn't highlight hidden files or folders(directories), and give option to view more of the hidden list if desired.

* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*
[cabox@box-codeanywhere challenge_files]$ ps aux | grep cabox                                                                 root      1651  0.0  0.6  69184  3488 ?        Ss   20:12   0:00 sshd: cabox [priv]                                           cabox     1653  0.0  0.2  69184  1476 ?        S    20:12   0:00 sshd: cabox@pts/0                                             cabox     1654  0.0  0.6  12916  3240 pts/0    Ss   20:12   0:00 -bash                                                         cabox     1874  0.0  0.2  13368  1060 pts/0    R+   21:02   0:00 ps aux                                                       cabox     1875  0.0  0.1   6384   680 pts/0    S+   21:02   0:00 grep cabox 
