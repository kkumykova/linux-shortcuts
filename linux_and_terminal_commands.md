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










