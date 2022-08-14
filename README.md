
#!/bin/bash
echo "This Script Works for Print content of current directory without ls."
cd /home/User/$1
echo "Navigating to the Current Directory"
pwd
echo "Listing to the Content of Current Directory"
for i in *; do echo $i; 
done


#!/bin/bash
functionfirstposition(){
echo "This Script Works for Print First Positional Argument"
echo "Hello I AM $1"
}
functionfirstposition KEERTHI SAI SOHA UST



#!/bin/bash

echo "This Script removes and provides the permissions to the Directory "
echo "Navigating to the Current Directory"
pwd
echo "Removing the permissions to the Directory "
chmod go-rwx $1
ls -ltr
echo "Providing the permissions to the Directory "
chmod 777 $1
ls -ltr
