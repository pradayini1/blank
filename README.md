#!/bin/bash
# bash for loop
for f in $( ls /var/ ); do
echo $f 
done
-------------------------
#!/bin/bash
COUNT=6
# bash while loop
while [ $COUNT -gt 0 ]; do
echo Value of count is: $COUNT
let COUNT=COUNT-1
done 
--------------------------
#!/bin/bash
COUNT=0
# bash until loop
until [ $COUNT -gt 5 ]; do
echo Value of count is: $COUNT
let COUNT=COUNT+1
done
-----------------------------
#!/bin/bash
# This bash script will locate and replace spaces
# in the filenames
DIR="."
# Controlling a loop with bash read command by redirecting STDOUT as
# a STDIN to while loop
# find will not truncate filenames containing spaces
find $DIR -type f | while read file; do
# using POSIX class [:space:] to find space in the filename
if [[ "$file" = *[[:space:]]* ]]; then
# substitute space with "_" character and consequently rename the file
mv "$file" `echo $file | tr ' ' '_'`
fi;
# end of while loop
done 
