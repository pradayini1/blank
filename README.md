#!/bin/bash
STRING="HELLO WORLD!!!"
echo $STRING
----------------------------------
#!/bin/bash
OF=myhome_directory_$(date +%Y%m%d).tar.gz
tar -czf $OF /home/linuxconfig
