---
layout: page
title: Install Composer
permalink: /php/composer/install/
---

{% include_relative /menu_php.md install_composer="active" %}

## Install Composer

- [https://getcomposer.org/download](https://getcomposer.org/download/){:target="_blank"}
- [How do I install Composer programmatically? - Composer](https://getcomposer.org/doc/faqs/how-to-install-composer-programmatically.md){:target="_blank"}

___

### Install Composer on Ubuntu

[1. Install dependencies]  
`sudo apt install curl php php-mbstring php-xml`

[2. Create an installation and temporary directory for Composer]  
`sudo mkdir -p /opt/Composer`
`mkdir -p ~/Composer`

[2. Download the installer script]  
`cd ~/Composer`  
`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"`

[3. Verify the integrity of the installer script]  
(Stores the latest signature of the installer script)  
`HASH="$(curl -Ss https://composer.github.io/installer.sig)"`

[Verify the installer script]  
`php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"`

You should get the following output  
`Installer verified`

If you get the output `Installer corrupt`, then you will need to redownload the installer script and rerun the verification command above.

_This installer script will simply check some php.ini settings, warn you if they are set incorrectly, and then download the latest **composer.phar** in the current directory._

[4. Install Composer]  
`php composer-setup.php --filename=composer`

[Installing a specific version of Composer]  
`php composer-setup.php --version=<version_no>`  

e.g. `php composer-setup.php --version=1.9.1` to install **Composer 1.9.1**  
All available versions can be found here [https://getcomposer.org/download/](https://getcomposer.org/download/)

[5. Move Composer to a protected directory]  
`sudo move composer.phar /opt/Composer/composer.phar`

[6. Add the composer binary to your $PATH]  
`echo "export PATH=\"/opt/Composer/:\$PATH\"" >> ~/.bash_profile`

[7. Reload the changes]  
`source ~/.bash_profile`

[8. Cleanup the temporary directory]  
`rmdir ~/Composer`

[9. Verify the installation]  
`composer --verson`  
_(An output showing the installed Composer version will be displayed)_

[Updating Composer]  
(This will update Composer to the latest stable version)  
`composer self-update`

[Upate to a specific version of composer]  
`php composer self-update <version_no>`  

e.g. `php composer self-update 1.9.1` to update to **Composer 1.9.1**
