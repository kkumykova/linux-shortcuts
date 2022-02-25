whoami

man 

clear / Ctrl + l

pwd

The Root Directory/Folder - the starting point for the file system is "/".

~ is my own directory

mkdir -p winter/seeds/lettuce for "make any needed parent dirs along the way" / make nested dirs.

touch - change file stamps / create an empty file

rmdir -to delete empty dirs only!

rm - removes files or directories.  By default, it does not remove directories!

To remove dirs with rm you need to use flag -r.

It will remove dirs and their contents.

rm -ri  for remove files interactively which allows you to make decisions with Y or N.

rm -v cat, dog with v for "verbose" which tells what was done to the files


xdg-open - opens a file or dir

xdg-open . for open current dir



mv - use to move an existing file around

mv pear new_pear - renames an existing file

mv new_pear /Stuff - as long as the destination folder comes last, the file(s) will be moved into this folder.



cp - copy files/folders

cp file-you-want-to-copy.txt destination.txt

If you want to cope a dir with all the contents -> use -r, --recursive for "copy dirs recursively"

cp -r folder-to-copy destination-folder

You can COPY and MOVE file at the same time:
cp file.txt Stuff/new_file.txt # a copy of file.txt was created under new_file.txt in the Stuff folder

head - output the first part of files

head song.txt -n 100 # prints out the first 100 lines of the file

tail - output the last part of files

tail song.txt # prints out the last 10 lines of the file

tail song.txt -n 20 # prints out the last 20 lines of the file


">" redirect command output date > today.txt # runs date command and outputs the result to the today.txt file
date > today.txt # adds the output to today.txt; if there is no today.txt it will create a new file and add the time to it.

IMPORTANT! This command replaces the content of the file, it is not adding to it.
to append, use >>

cat file.txt # returns the entire content of the file

cat file.txt file_two.txt # prints out the content of both files

cat file.txt file_two.txt > all.txt # saves the content of both files to all.txt

You can also use number lines in the output by adding -n:
can -n all.txt

less -  shows the content of a file in a nice interactive way

less all.txt

To search through the output: /search-word

q to quit 


echo - it takes the argument you pass and prints it out. It is useful if you create config files with initial text.

echo "hello" > hello.txt # writes "hello" to a newly created hello.txt file



wc - word count (also, lines, (words), bytes)

wc -l all.txt # show nr of lines

wc -w all.txt # show nr of words



Piping - run a command and use it's output as an input in another command:

ls -l | wc # list the content of current working dir and count the lines, words and bytes



sort all.txt # sorts the contents of the file all.txt alphabetically but not changing the content

sort -n nums.txt # sort data numerically

sort -nr nums.txt # sort data numerically in reverse order

sort -nu nums.txt # sort data numerically and remove duplicate values; use "u" for unique

sort -un nums.txt | wc -l # sort unique values numerically and count the number of lines

cat butcher.txt groceries.txt | sort # concatenate both files and sort what it received as an input - the combined content


UNIQ - a command useful to sort lines of text.

It reports or omits repeated lines.

It only removes duplicate values that are found next to each other.

It is normally used in conjunction with SORT. E.g.: sort flavors.txt | uniq

sort flavors.txt | uniq -d # will only display duplicate values found in the file

sort flavors.txt | uniq -u # will only display NON-duplicate values

sort flavors.txt | uniq -c # show NON-duplicate values and count them

sort flavors.txt | uniq -c | sort -n # ...and sort by number


EXPANSION

Path name expansion 

echo * # matches every path in the current working dir

? matches a single character 

{} expansion

touch app.{js, css, py} # will create app.js, app.css and app.py files 

ech {1..99} # will expand to numbers between those two digits

DIFF - show the diff b/w files

-u # show with some context around the changed lines


FIND 

find . -name '*.js' # find all js files in the current dir

find . -type d -name '*E*' # find dirs in the current folder with "E" in them

find . -type d -iname '*E*' # same as above but case-insensitive because of the use of "i"


GREP - global regular expression print; searches inside the files

grep search-pattern where-to-search-file

grep -r "chicken" . # find "chicken" in files in all sub-dirs of the current folder

grep -ri "chicken" . # same as above but case-insensitive  


du for disk usage - will calculate the size of the dir as a whole


df - get disk usage information

df -h Desktop

history - shows the history of your commands

ps for process status to view processes on your pc

top - show top most CPU intensive processes

killall -9 # stops all the processes

killall -9 name-of-the-program-to-kill # stops this particular process; it can be used if it is difficult to find ps ID as it does not require process ID.


gzip to compress individual files

gzip - k file.txt # compresses the input file in a separate file and keeps the original one.

gzip -d filename.txt.gz # decompress the file

gunzip == gzip command plus -d option is always enabled by default:

gunzip filename.txt.gz

tar - to create an archive and group multiple files in a single file WITHOUT compressing them

tar -cf archive.tar file1 file2

-c is for "create"

"f" is the way to provide file name - the name of the destination archive/end result name

To extract files from the archive we use -x option, "x" for extract: 

tar -xf file-to-un-archive.tar # the files will be extracted in teh current folder

You can specify destination with -C:

tar -xf file-to-un-archive.tar -C directory

To compress an archive folder:

gzip -k archive.tar 

To combine and compress files at the same time:

tar -czf archive.tar.gz file1 file2 # "z" is the option that does the compression

To unzip and un-archive at the same time:

tar -xf archive.tar.gz 


nano - a beginner friendly editor.

nano filename.txt


alias - to create custom shortcuts; it only exists in the current window; to make permanent alias - update bash config file.

alias myls='ls-la'


xargs - the output of one command will be used as an input for another command:

command1 | xargs command2

The "|" does not pass the output from one command as an input to another one with all commands, e.g. with those that require to take additional input: rm

But xargs does resolve the above by acting as an "adapter":

cat file.txt | xargs rm # read file and pass it to rm for removal

ln - creates hard (these are rarely used due to some limitations) and soft links.

With these links you can have a file that links to another file. 

Use -s (--symbolic) option to make soft link.

With the hard link, even if the original file is gone, the hard link with still have the contents of the original one as both were pointing to the same place of memory.

With the symbolic link, if the original is gone, no contents will be found in the file link. The link will be pointing to a non-existing file even if the link is there.

who - displays the users logged in to the system;

su - switch user


sudo for "super user do" to run a command as root;

chown for "change the owner"; use with sudo even if you are changing the permissions of your own files/folders.

sudo chown owner filename

To change the ownership of all nested files/folders, use -R:

sudo chown -R kitty CatStuff/


chmod - change permissions 

chmod g-r file.txt # remove read permissions for the group

chmod o-rwx file.txt # remove read, write and execute permissions for the others

chmod a=r file.txt # set permissions to read ONLY, do it for all















