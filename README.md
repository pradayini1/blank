#!/bin/bash
# declare STRING variable
STRING="Hello World"
# print variable on a screen
echo $STRING 
---------------------------------------
#!/bin/bash
tar -czf myhome_directory.tar.gz /home/linuxconfig
--------------------------------------------------------

#!/bin/bash
STRING="HELLO WORLD!!!"
echo $STRING
----------------------------------------------------------
#!/bin/bash
OF=myhome_directory_$(date +%Y%m%d).tar.gz
tar -czf $OF /home/linuxconfig
--------------------------------------------------------------
#!/bin/bash
# Define bash global variable
# This variable is global and can be used anywhere in this bash script
VAR="global variable"
function bash { 
# Define bash local variable
# This variable is local to bash function only
local VAR="local variable"
echo $VAR
} 
echo $VAR
bash
# Note the bash global variable did not change
# "local" is bash reserved word
echo $VAR
---------------------------------------------------------------------------
#!/bin/bash
# use predefined variables to access passed arguments
#echo arguments to the shell
echo $1 $2 $3 ' -> echo $1 $2 $3'
# We can also store arguments from bash command line in special array
args=("$@")
#echo arguments to the shell
echo ${args[0]} ${args[1]} ${args[2]} ' -> args=("$@"); echo ${args[0]}
${args[1]} ${args[2]}'
#use $@ to print out all arguments at once
echo $@ ' -> echo $@'
# use $# variable to print out
# number of arguments passed to the bash script
echo Number of arguments passed: $# ' -> echo Number of arguments passed: $#' 
-------------------------------------------------------------------------------------
#!/bin/bash
# use a subshell $() to execute shell command
echo $(uname -o)
# executing bash command without subshell
echo uname -o
-------------------------------------------------------------------------------------
#!/bin/bash
echo -e "Hi, please type the word: \c "
read word
echo "The word you entered is: $word"
echo -e "Can you please enter two words? "
read word1 word2
echo "Here is your input: \"$word1\" \"$word2\""
echo -e "How do you feel about bash scripting? "
# read command now stores a reply into the default build-in variable $REPLY
read
echo "You said $REPLY, I'm glad to hear that! "
echo -e "What are your favorite colours ? "
# -a makes read command to read into an array
read -a colours
echo "My favorite colours are also ${colours[0]}, ${colours[1]} and
${colours[2]}:-)" 
------------------------------------------------------------------------------------------------------------
#!/bin/bash
# bash trap command
trap bashtrap INT
# bash clear screen command
clear;
# bash trap function is executed when CTRL-C is pressed:
# bash prints message => Executing bash trap subrutine !
bashtrap()
{
echo "CTRL+C Detected !...executing bash trap !"
}
# for loop from 1/10 to 10/10
for a in `seq 1 10`; do
echo "$a/10 to Exit."
sleep 1;
done
echo "Exit Bash Trap Example!!!" 
-----------------------------------------------------------------------------------------------
#!/bin/bash
#Declare array with 4 elements
ARRAY=( 'Debian Linux' 'Redhat Linux' Ubuntu Linux )
# get number of elements in the array
ELEMENTS=${#ARRAY[@]}
# echo each element in array
# for loop
for (( i=0;i<$ELEMENTS;i++)); do
echo ${ARRAY[${i}]}
done 
-----------------------------------------------------------------------------
#!/bin/bash
# Declare array
declare -a ARRAY
# Link filedescriptor 10 with stdin
exec 10<&0
# stdin replaced with a file supplied as a first argument
exec < $1 
let count=0
while read LINE; do
ARRAY[$count]=$LINE
((count++))
done
echo Number of elements: ${#ARRAY[@]}
# echo array's content
echo ${ARRAY[@]}
# restore stdin from filedescriptor 10
# and close filedescriptor 10
exec 0<&10 10<&- 
---------------------------------------------------------
#!/bin/bash
directory="./BashScripting"
# bash check if directory exists
if [ -d $directory ]; then
echo "Directory exists"
else
echo "Directory does not exist"
fi 
--------------------------------------------------------------------
#!/bin/bash
# Declare variable choice and assign value 4
choice=4
# Print to stdout
echo "1. Bash"
echo "2. Scripting"
echo "3. Tutorial"
echo -n "Please choose a word [1,2 or 3]? "
# Loop while the variable choice is equal 4
# bash while loop
while [ $choice -eq 4 ]; do
# read user input
read choice
# bash nested if/else
if [ $choice -eq 1 ] ; then
echo "You have chosen word: Bash"
else
if [ $choice -eq 2 ] ; then
echo "You have chosen word: Scripting"
else
if [ $choice -eq 3 ] ; then
echo "You have chosen word: Tutorial"
else
echo "Please make a choice between 1-3 !"
echo "1. Bash"
echo "2. Scripting"
echo "3. Tutorial"
echo -n "Please choose a word [1,2 or 3]? "
choice=4
fi
fi
fi
done
-----------------------------------------------------------------------------
#!/bin/bash
# declare integers
NUM1=2
NUM2=2
if [ $NUM1 -eq $NUM2 ]; then
 echo "Both values are equal"
else
 echo "Values are NOT equal"
fi 
-----------------------------------------------------------------------------------------
#!/bin/bash
# declare integers
NUM1=2
NUM2=1
if [ $NUM1 -eq $NUM2 ]; then
 echo "Both Values are equal"
else
 echo "Values are NOT equal"
fi 
--------------------------------------------------------------------
#!/bin/bash
# declare integers
NUM1=2
NUM2=1
if [ $NUM1 -eq $NUM2 ]; then
 echo "Both values are equal"
elif [ $NUM1 -gt $NUM2 ]; then
 echo "NUM1 is greater than NUM2"
else
 echo "NUM2 is greater than NUM1"
fi 
----------------------------------------------------------
#!/bin/bash
#Declare string S1
S1="Bash"
#Declare string S2
S2="Scripting"
if [ $S1 = $S2 ]; then
 echo "Both Strings are equal"
else
 echo "Strings are NOT equal"
fi
------------------------------------------------------------
#!/bin/bash
#Declare string S1
S1="Bash"
#Declare string S2
S2="Bash"
if [ $S1 = $S2 ]; then
echo "Both Strings are equal"
else
echo "Strings are NOT equal"
fi 
----------------------------------------------------------
#!/bin/bash
file="./file"
if [ -e $file ]; then
echo "File exists"
else
echo "File does not exist"
fi 
-------------------------
#!/bin/bash
while [ ! -e myfile ]; do
# Sleep until file does exists/is created
sleep 1
done 

