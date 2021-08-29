## Uninstall the MongoDB

1. Stop MongoDB.  
Stop the mongod process by issuing the following command.  
`sudo service mongodb stop`

2. Remove Packages.  
Remove any MongoDB packages that you had previously installed.  
`sudo apt-get purge mongodb-org*`

3. Remove Data Directories.  
Remove MongoDB databases and log files.  
`sudo rm -r /var/log/mongodb`  
`sudo rm -r /var/lib/mongodb`  
or by using one command  
`sudo rm -r /var/log/mongodb /var/lib/mongodb`

* Extra commands to make sure everything is uninstalled.  
`sudo apt-get purge mongodb mongodb-clients mongodb-server mongodb-dev`  
`sudo apt-get purge mongodb-10gen`  
`sudo apt-get autoremove`  

Some of those commands may fail, depending on what packages you actually have installed, but that's okay.

This should also remove your config from /etc/mongodb.conf.

### Note

if you did the steps in the [Microsoft’s directions](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-database#install-mongodb), you may have created a directory named "data".  
remove this directory for now by:
`rm -rf data`
