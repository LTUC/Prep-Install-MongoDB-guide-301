# MongoDB 3.6 for WSL2 | Ubuntu

## install MongoDB in WSL

1. Update your Ubuntu packages.  
`sudo apt-get update`

2. Install MongoDB packages.  
`sudo apt-get install mongodb`

3. Confirm installation and get the version number.  
`mongo --version`

4. Run the server.  
`sudo service mongodb start`

5. Start mongo console.  
`mongo`

* Check the service status.  
`sudo service mongodb status`

### Start MongoDB using the operating system's built-in init system

In the example above we ran MongoDB directly. Other tutorials may start MongoDB using the operating system's built-in init system. You might see the command `sudo systemctl status mongodb` used in tutorials or articles. Currently WSL does not have support for systemd (a service management system in Linux).

You shouldn't notice a difference, but if a tutorial recommends using sudo systemctl, instead use: `sudo /etc/init.d/`.

* For example:  
`sudo systemctl status mongodb`, for WSL would be `sudo /etc/init.d/mongodb status` ...or you can also use `sudo service mongodb status`.

### Repair

* In some cases, you may have a problem while starting the service.  
Try to do a repair by following these steps:

  1. Remove lock file.  
    `sudo rm /var/lib/mongodb/mongod.lock`

  2. Repair mongodb.  
    `mongod --repair`

  3. Start mongodb.  
    `sudo service mongodb start`

  4. Start mongo console.  
    `mongo`
    
* When you do a repair and see this error " exception in initAndListen: NonExistentPath: Data directory /data/db not found "
in this case, you shoud do the following:
  1. Make a directory to store data:   
  `mkdir -p data/db`
  2. Run a Mongo instance:   
  `sudo mongod --dbpath ~/data/db`
  3. Repair mongodb.  
    `mongod --repair`
  4. Start mongodb:    
  `sudo service mongodb start`

* If you have error " Unit mongodb.service is masked ":    
  * run this: `sudo systemctl unmask mongodb` or `sudo /etc/init.d/mongodb unmask`


If that did not works, you probably faced a problem during the installation.  
Try to uninstall and install it again by following the steps [Here]().




