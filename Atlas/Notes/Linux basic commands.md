---
date: 2025-07-15:00
up:
  - "[[linux]]"
---
## echo
```zsh
#print
echo hello
```
## pwd
```
#where you are
pwd
```
## cd
```
#change directory
cd .. #parent directory
cd ~ #home directory
cd - #last directory
```
## ls
```
#list directories
#-a for all file
#-l for information
ls
```
## touch
```
#create file
touch hello
```
## file 
```
#description of file
file hello
```
## cat
```
#print file content
cat hello
```
## less
```
#read file
less hello
```
## history
```
history
```
## clear
```
clear

```
## cp

```zsh
cp hello /home/pete
cp -r #copy over the directory and files inside
cp -i #prompt you before overwriting
```
### Wildcards
- *  represent all single characters or any string.
- ? used to represent one character
- [] used to represent any character within the brackets
```zsh
cp *.jpg /home/pete/Pictures
```
## mv
```zsh
mv helle hello #rename
mv hello user/kevin #move
mv -i #prompt you berfore overwriting
mv -b #overwrite and make a backup
```
## mkdir
create directory
```zsh
mkdir books
mkdir -p books/harry #make the subdirectories at the same time
```
## rm
```zsh
rm -f #force
rm -i #prompt you before removing
rm -r #remove directory and all files in it
rmdir #remove directory
```
## find
```
find /home -type d -name MyFolder
```
## helping commands
```
help ls
man ls
whatis ls
```
## alias
## exit
# Reference
https://linuxjourney.com/lesson/the-shell