ownCloud 10.0.10: A Quick Start Guide
==============

**Author:** *Suzanne Burns* 


# Overview 

ownCloud is a file sharing server that puts the control and security of your own data back into your hands. It includes the ownCloud server, which runs on Linux, client applications for Microsoft Windows, Mac OS X and Linux, and mobile clients for the Android and Apple iOS operating systems.

This quick start serves as a step-by-step guide to installing it from ownCloud's Open Build Service packages. It also covers how to configure the proxy server, set the user in ownCloud, and how users can install the Desktop Sychronization Client to access the server:

+ [Installing ownCloud](#install)
+ [Setting Up the Proxy Server](#proxy) 
+ [Setting Up a User in ownCloud](#user)
+ [Installing the Desktop Synchronization Client](#deckofficer) 

> Need enterprise features? See [Installing & Upgrading ownCloud Enterprise Edition](https://doc.owncloud.org/server/10.0/admin_manual/enterprise/installation/install.html).

<a name="install"></a>
# Installing ownCloud 

Installing ownCloud on Linux from our Open Build Service packages is the preferred method. These are maintained by ownCloud engineers, and you can use your package manager to keep your ownCloud server up-to-date. The recommended package to use is *owncloud-files*. See [Linux Package Manager Installation](https://doc.owncloud.org/server/10.0/admin_manual/installation/linux_installation.html) for more information about package managers. 

1. Download the package manager you want to use from ownCloud's [Download Center](https://owncloud.org/download/). 

> Note: The package manager only installs ownCloud; it does not install Apache, a database, or any of the required PHP dependencies. These must be installed using a classic LAMP stack (Linux, Apache, MySQL/MariaDB, PHP). 

2. Install the LAMP stack. If there are no packages for your Linux distribution, you may prefer to install from source. This allows you to create your own custom LAMP stack without dependency conflicts with the ownCloud package. See [Manual Installation on Linux](https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html) for a step by step guide to installing your own LAMP stack and installing from source.  

3. After you have installed the LAMP stack, you must then update the [package manager's configuration](http://download.owncloud.org/download/repositories/10.0/owncloud/). Configurations  are available for the following Linux distributions:

   + Ubuntu 14.04 & 16.04
   + Debian 7 & 8
   + RHEL 6 & 7
   + CentOS 7.2 & 7.3
   + SLES 11SP4 & 12SP2
   + openSUSE Leap 42.2 & 42.3

4.  Once your package manager's configuration has been updated, follow the instructions included in the configuration to install ownCloud. 

5.  When all ownCloud files are installed, the last step to completing the installation is running the Installation Wizard. This involves just three steps:

   1. Point your web browser to http://localhost/owncloud.
   2. Enter your desired administrator’s username and password.
   3. Click the Finish Setup button.

> Warning: If you are planning to use the installation wizard, we strongly encourage you to protect it, through some form of password authentication, or access control. If the installer is left unprotected when exposed to the public internet, there is the possibility that a malicious actor could finish the installation and block you out — or worse. So please ensure that only you — or someone from your organization — can access the web installer. 

5. You’re now finished and can start using your new ownCloud server! Of course, there is much more that you can do to set up your ownCloud server for best performance and security. The Administration Manual provides [in-depth instructions](https://doc.owncloud.org/server/10.0/admin_manual/installation/installation_wizard.html#in-depth-guide) that covers important installation and post-installation steps. 

<a name="proxy"></a>
# Setting Up the Proxy Server 

Lorem ipsum 

https://doc.owncloud.org/server/10.0/admin_manual/configuration/index.html

https://doc.owncloud.org/server/10.0/admin_manual/configuration/ldap/ldap_proxy_cache_server_setup.html#configure-the-server

https://doc.owncloud.org/server/9.1/admin_manual/configuration_server/config_sample_php_parameters.html

https://doc.owncloud.org/server/9.1/admin_manual/configuration_server/config_sample_php_parameters.html#proxy-configurations

<a name="user"></a>
# Setting Up a User

You can set up new user accounts in the User management page of your ownCloud Web UI. 

User accounts have the following properties:

+ **Login Name (Username)**: The unique ID of an ownCloud user; it cannot be changed. 
+ **Full Name**: The user’s display name that appears on file shares, the ownCloud Web interface, and emails. Admins and users may change the Full Name anytime. If the Full Name is not set it defaults to the login name. 
+ **Password**: The admin sets the new user’s first password. Both the user and the admin can change the user’s password at anytime. 
+ **Groups**: You may create groups, and assign group memberships to users. By default new users are not assigned to any groups. 
+ **Group Admin**: Group admins are granted administrative privileges on specific groups, and can add and remove users from their groups. 
+ **Quota**: The maximum disk space assigned to each user. Any user that exceeds the quota cannot upload or sync data. You have the the option to include external storage in user quotas. 

> See [User Management](https://doc.owncloud.org/server/9.1/admin_manual/configuration_user/user_configuration.html) in the Server Administration Manual for in-depth information about managing user settings. 

To create a new user account: 
1. Enter the new user’s login name and their initial password in the fields provided. 

> Login names may contain letters, numbers, dashes, underscores, periods, and at (@) signs. After creating the user account, you can fill in their Full Name if it is different than the login name, or leave it for the user to complete. 

2. Assign group memberships as needed in the Users dropdown.
3. Click the Create button.
4. To automatically send the user a notification with their new login information, select Send Email in the control panel on the lower left sidebar and enter the new user’s email address. 

<a name="deckofficer"></a>
# Installing the Desktop Synchronization Client

Users can install the ownCloud Desktop Synchronization Client to access the server. the ownCloud Desktop Synchronization Client is avaialble for Microsoft Windows, Mac OS X and Linux. 

> This quick start guide covers how to install the desktop client. There are also mobile clients for the Android and Apple iOS operating systems, however. See the [ownCloud Server User Manual](https://doc.owncloud.com/server/user_manual/index.html) for more information about ownCloud desktop and mobile clients.

1. Download the latest version of the ownCloud Desktop Synchronization Client from the ownCloud's [Download Center](https://owncloud.org/download/). There are clients for Linux, macOS, and Microsoft Windows.

   + Installation on Mac OS X and Windows is the same as for any software application: download the program and then double-click it to launch the installation, and then follow the installation wizard. After it is installed and configured the sync client will automatically keep itself updated. 

   + Linux users must follow the instructions on the download page to add the appropriate repository for their Linux distribution, install the signing key, and then use their package managers to install the desktop sync client. Linux users will also update their sync clients via package manager, and the client will display a notification when an update is available. 

2. If you just want to install ownCloud Desktop Synchronization Client on your local system, you can simply launch the .msi file and configure it in the wizard that pops up. See [Customizing the Windows installation](https://doc.owncloud.com/desktop/2.5/installing.html#customizing-the-windows-installation) in the User Manual for more information on these custom settings.

https://doc.owncloud.com/desktop/2.5/index.html

https://doc.owncloud.com/desktop/2.5/installing.html#installation-wizard

