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
