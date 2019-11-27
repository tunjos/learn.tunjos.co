---
layout: page
title: Install MongoDB
permalink: /mongodb/install/
---

{% include_relative /menu_mongodb.md install_mongodb="active" %}

## Install MongoDB

- [Install MongoDB Community Edition](https://docs.mongodb.com/manual/administration/install-community/)
- [Install MongoDB Enterprise](https://docs.mongodb.com/manual/administration/install-enterprise/)

___

### Install MongoDB Community Edition on Ubuntu

#### Install MongoDB Community Edition using .deb Packages (Package Manager)
_IMPORTANT:
The **mongodb-org** package is officially maintained and supported by MongoDB Inc. and kept up-to-date with the most recent MongoDB releases. This installation procedure uses the **mongodb-org** package.  
The **mongodb** package provided by Ubuntu is **not** maintained by MongoDB Inc. and conflicts with the **mongodb-org** package. To check if Ubuntu’s **mongodb** package is installed on the system, run `sudo apt list --installed | grep mongodb`. You can use `sudo apt remove mongodb` and `sudo apt purge mongodb` to remove and purge the **mongodb** package before attempting this procedure._

[1. Import the public key used by the package management system]  
`wget -qO - https://www.mongodb.org/static/pgp/server-X.Y.asc | sudo apt-key add -`

_(If you receive an error indicating that gnupg is not installed)_  
[Install **gnupg**]  
`sudo apt-get install gnupg`  
(Then retry the importing the public key)

[2. Create a /etc/apt/sources.list.d/mongodb-org-X.Y.list file for MongoDB]  
_(Distributions and versions can be found here [Index of dists](https://repo.mongodb.org/apt/ubuntu/dists/). Replace X.Y with a specific version e.g. 4.2)_

[Create the list file for Ubuntu 18.04 (Bionic)]  
`echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/X.Y multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-X.Y.list`

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
_WARNING:
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

Package Name | Description
--- | ---
**mongodb-org**	|	A metapackage that will automatically install the four component packages listed below.
**mongodb-org-server** | Contains the [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) daemon, associated init script, and a [configuration file](https://docs.mongodb.com/manual/reference/configuration-options/#conf-file) (**/etc/mongod.conf**). You can use the initialization script to start [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) with the configuration file. For details, see [Run MongoDB Community Edition](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#run-mongodb-community-edition).
**mongodb-org-mongos** | Contains the [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos) daemon.
**mongodb-org-shell** |	Contains the [mongo](https://docs.mongodb.com/manual/reference/program/mongo/#bin.mongo) shell.
**mongodb-org-tools** |	Contains the following MongoDB tools: [mongoimport](https://docs.mongodb.com/manual/reference/program/mongoimport/#bin.mongoimport) [bsondump](https://docs.mongodb.com/manual/reference/program/bsondump/#bin.bsondump), [mongodump](https://docs.mongodb.com/manual/reference/program/mongodump/#bin.mongodump), [mongoexport](https://docs.mongodb.com/manual/reference/program/mongoexport/#bin.mongoexport), [mongofiles](https://docs.mongodb.com/manual/reference/program/mongofiles/#bin.mongofiles), [mongorestore](https://docs.mongodb.com/manual/reference/program/mongorestore/#bin.mongorestore), [mongostat](https://docs.mongodb.com/manual/reference/program/mongostat/#bin.mongostat), and [mongotop](https://docs.mongodb.com/manual/reference/program/mongotop/#bin.mongotop).

___

### Install MongoDB Enterprise Edition on Ubuntu

#### Using .deb Packages (Recommended) (Package Manager)

[1. Import the public key used by the package management system]  
`wget -qO - https://www.mongodb.org/static/pgp/server-X.Y.asc | sudo apt-key add -`

_(If you receive an error indicating that gnupg is not installed)_  
[Install **gnupg**]  
`sudo apt-get install gnupg`  
(Then retry the importing the public key)

[2. Create a /etc/apt/sources.list.d/mongodb-enterprise.list file for MongoDB]  
_(Distributions and versions can be found here [Index of dists](http://repo.mongodb.com/apt/ubuntu/dists/). Replace X.Y with a specific version e.g. 4.2)_  

[Create the list file for Ubuntu 18.04 (Bionic)]  
`echo "deb [ arch=amd64 ] http://repo.mongodb.com/apt/ubuntu bionic/mongodb-enterprise/X.Y multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-enterprise.list`

[3. Reload local package database]  
`sudo apt-get update`  

[4. Install the MongoDB Enterprise packages]  

[Install MongoDB Enterprise]  
`sudo apt-get install -y mongodb-enterprise`

or

[Install a specific release of MongoDB Enterprise]  
`sudo apt-get install -y mongodb-enterprise=X.Y.Z mongodb-enterprise-server=X.Y.Z mongodb-enterprise-shell=X.Y.Z mongodb-enterprise-mongos=X.Y.Z mongodb-enterprise-tools=X.Y.Z`

[Pin a specific version of MongoDB Enterprise]  
_(Although you can specify any available version of MongoDB, apt-get upgrades the packages when a newer version becomes available. To prevent unintended upgrades, pin the package)_  

`echo "mongodb-enterprise hold" | sudo dpkg --set-selections`  
`echo "mongodb-enterprise-server hold" | sudo dpkg --set-selections`  
`echo "mongodb-enterprise-shell hold" | sudo dpkg --set-selections`  
`echo "mongodb-enterprise-mongos hold" | sudo dpkg --set-selections`  
`echo "mongodb-enterprise-tools hold" | sudo dpkg --set-selections`  

[Run MongoDB Enterprise]

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
_WARNING:
This process will completely remove MongoDB, its configuration, and all databases. This process is not reversible, so ensure that all of your configuration and data is backed up before proceeding._

[1. Stop MongoDB]  
`sudo service mongod stop`  

[2. Remove Packages]  
`sudo apt-get purge mongodb-enterprise*`

[3. Remove Data Directories]  
`sudo rm -r /var/log/mongodb`  
`sudo rm -r /var/lib/mongodb`

[MongoDB Packages Enterprise]  
_IMPORTANT:
The **mongodb-enterprise** package is officially maintained and supported by MongoDB Inc. and kept up-to-date with the most recent MongoDB releases. This installation procedure uses the **mongodb-enterprise** package.  
The **mongodb** package provided by Ubuntu is **not** maintained by MongoDB Inc. and conflicts with the **mongodb-enterprise** package. To check if Ubuntu’s **mongodb** package is installed on the system, run `sudo apt list --installed | grep mongodb`. You can use `sudo apt remove mongodb` and `sudo apt purge mongodb` to remove and purge the **mongodb** package before attempting this procedure._

(MongoDB provides officially supported Enterprise packages in their own repository. This repository contains the following packages)

Package Name | Description
--- | ---
**mongodb-enterprise** | A metapackage that will automatically install the four component packages listed below.
**mongodb-enterprise-server** |	Contains the [mongod](https://docs.mongodb.com/manual/reference/program/mongod/#bin.mongod) daemon and associated configuration and init scripts.
**mongodb-enterprise-mongos** | Contains the [mongos](https://docs.mongodb.com/manual/reference/program/mongos/#bin.mongos) daemon.
**mongodb-enterprise-shell** |	Contains the [mongo](https://docs.mongodb.com/manual/reference/program/mongo/#bin.mongo) shell.
**mongodb-enterprise-tools** | Contains the following MongoDB tools: [mongoimport](https://docs.mongodb.com/manual/reference/program/mongoimport/#bin.mongoimport) [bsondump](https://docs.mongodb.com/manual/reference/program/bsondump/#bin.bsondump), [mongodump](https://docs.mongodb.com/manual/reference/program/mongodump/#bin.mongodump), [mongoexport](https://docs.mongodb.com/manual/reference/program/mongoexport/#bin.mongoexport), [mongofiles](https://docs.mongodb.com/manual/reference/program/mongofiles/#bin.mongofiles), [mongorestore](https://docs.mongodb.com/manual/reference/program/mongorestore/#bin.mongorestore), [mongostat](https://docs.mongodb.com/manual/reference/program/mongostat/#bin.mongostat), and [mongotop](https://docs.mongodb.com/manual/reference/program/mongotop/#bin.mongotop).

___

### Install MongoDB Community/MongoDB Enterprise on Ubuntu using .tgz Tarball
