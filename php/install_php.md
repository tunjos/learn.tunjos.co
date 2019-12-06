---
layout: page
title: Install PHP
permalink: /php/install/
---

{% include_relative /menu_php.md install_php="active" %}

## Install PHP

- [PHP: Installation and Configuration - Manual ](https://www.php.net/manual/en/install.php){:target="_blank"}

___

### Installation PHP on Ubuntu

[Install PHP]  
_(This is install the latest available version of PHP on Ubuntu's official apt repositories)_  
`sudo apt-get install php`

[Install a specific version of PHP]  
You can install a specific version of PHP by appending the version number.  
`sudo apt-get install php<version_no>`

e.g. `sudo apt-get install php7.2` to install **PHP 7.2**.

[Verify the installation]  
`php -v`  
_(An output showing the installed PHP version will be displayed)_
