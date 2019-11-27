---
layout: page
title: Install MongoDB
permalink: /mongodb/install/
---

{% include_relative /menu_mongodb.md install_mongodb="active" %}

## Install MongoDB

- [Install MongoDB Community Edition](https://docs.mongodb.com/manual/administration/install-community/)
- [Install MongoDB Enterprise](https://docs.mongodb.com/manual/administration/install-enterprise/)


### Install MongoDB Community Edition on Ubuntu

#### Install MongoDB Community Edition using .deb Packages (Package Manager)

[1. Import the public key used by the package management system]  
`wget -qO - https://www.mongodb.org/static/pgp/server-X.Y.asc | sudo apt-key add -`

Install **gnupg**  
`sudo apt-get install gnupg`

If you receive an error indicating that gnupg is not installed  
[Install gnupg]  
`sudo apt-get install gnupg`  
(Then retry the importing the public key)

[2. Create a /etc/apt/sources.list.d/mongodb-org-X.Y.list file for MongoDB]  
_(Distributions and versions can be found here [Index of dists](https://repo.mongodb.com/apt/ubuntu/dists/). Replace X.Y with a specific version e.g. 4.2)_

[Create the list file for Ubuntu 18.04 (Bionic)]  

`echo "deb [ arch=amd64 ] http://repo.mongodb.com/apt/ubuntu bionic/mongodb-enterprise/X.Y multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-enterprise.list`

[3. Reload local package database]  
`sudo apt-get update`  

[4. Install the MongoDB packages]  

[Install MongoDB]  
`sudo apt-get install -y mongodb-org`  

or

[Install a specific release of MongoDB]  
`sudo apt-get install -y mongodb-org=X.Y.Z mongodb-org-server=X.Y.Z mongodb-org-shell=X.Y.Z mongodb-org-mongos=X.Y.Z mongodb-org-tools=X.Z.Y`  

[Pin a specific version of MongoDB]  
_(Although you can specify any available version of MongoDB, apt-get upgrades the packages when a newer version becomes available. To prevent unintended upgrades, pin the package)_

`echo "mongodb-org hold" | sudo dpkg --set-selections`  
`echo "mongodb-org-server hold" | sudo dpkg --set-selections`  
`echo "mongodb-org-shell hold" | sudo dpkg --set-selections`  
`echo "mongodb-org-mongos hold" | sudo dpkg --set-selections`  
`echo "mongodb-org-tools hold" | sudo dpkg --set-selections`  

[Run MongoDB Community Edition]

[1. Start MongoDB]  
`sudo service mongod start`  

[2. Verify that MongoDB has started successfully]  
`sudo service mongod status`  

_(You can also check the log file for the current status of the mongod process, located at: /var/log/mongodb/mongod.log by default. A running mongod instance will indicate that it is ready for connections with the following line)_  
`[initandlisten] waiting for connections on port 27017`

[3. Stop MongoDB]  
`sudo service mongod stop`  

[4. Restart MongoDB]  
`sudo service mongod restart`  

[5. Begin using MongoDB]  
[Start a mongo shell]  
`mongo`

[Uninstall MongoDB]  
_Note:
This process will completely remove MongoDB, its configuration, and all databases. This process is not reversible, so ensure that all of your configuration and data is backed up before proceeding._

[1. Stop MongoDB]  
`sudo service mongod stop`  

[2. Remove Packages]  
`sudo apt-get purge mongodb-org*`  

[3. Remove Data Directories]  
`sudo rm -r /var/log/mongodb`  
`sudo rm -r /var/lib/mongodb`  

[MongoDB Packages]  
_(MongoDB provides officially supported packages in their own repository)_

Package Name	|	Description
--- | ---
**mongodb-org**	|	A metapackage that will automatically install the four component packages listed below.
**mongodb-org-server** |	Contains the mongod daemon, associated init script, and a configuration file (/etc/mongod.conf). You can use the initialization script to start mongod with the configuration file. For details, see Run MongoDB Community Edition.
**mongodb-org-mongos** |	Contains the mongos daemon.
**mongodb-org-shell** |	Contains the mongo shell.
**mongodb-org-tools** |	Contains the following MongoDB tools: mongoimport bsondump, mongodump, mongoexport, mongofiles, mongorestore, mongostat, and mongotop.
