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
