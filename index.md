ownCloud 10.0.10: A Quick Start Guide
==============

**Author:** *Suzanne Burns* 


# 1. Overview 

ownCloud is a file sharing server that puts the control and security of your own data back into your hands. ownCloud includes the ownCloud server, which runs on Linux, client applications for Microsoft Windows, Mac OS X and Linux, and mobile clients for the Android and Apple iOS operating systems.

This quick start is written for system administrators, and serves as a step-by-step guide to installing and configuring it from ownCloud's Open Build Service packages. These are maintained by ownCloud engineers, and you can use your package manager to keep your ownCloud server up-to-date. 

The document takes you through the following:  

+ Installing ownCloud on Linux
+ Setting Up the Proxy Server 
+ Setting Up a User in ownCloud
+ Logging in as a User

# 2. Installing ownCloud 

Installing ownCloud on Linux from our Open Build Service packages is the preferred method. These are maintained by ownCloud engineers, and you can use your package manager to keep your ownCloud server up-to-date. The recommended package to use is *owncloud-files*. See Linux Package Manager Installation for more information about package managers. Package managers are downloaded in ownCloud's Download Center (https://owncloud.org/download/).

> The package manager only installs ownCloud; it does not install Apache, a database, or any of the required PHP dependencies. These must be installed using a classic LAMP stack. 

2. If there are no packages for your Linux distribution, you may prefer to install from source using a LAMP stack (Linux, Apache, MySQL/MariaDB, PHP). This allows you to create your own custom LAMP stack without dependency conflicts with the ownCloud package. See *Manual Installation on Linux* for a step by step guide to installing your own LAMP stack and installing from source.  
3. After you have installed the LAMP stack, you must then update the package manager's configuration. The folliowing  (http://download.owncloud.org/download/repositories/10.0/owncloud/) are available for the following Linux distributions:

   + Ubuntu 14.04 & 16.04
   + Debian 7 & 8
   + RHEL 6 & 7
   + CentOS 7.2 & 7.3
   + SLES 11SP4 & 12SP2
   + openSUSE Leap 42.2 & 42.3

4.  Once your package manager has been updated, follow the rest of the instructions included in the configuration to install ownCloud. 
5.  When the ownCloud prerequisites are fulfilled and all ownCloud files are installed, the last step to completing the installation is running the Installation Wizard. This involves just three steps:

   1. Point your web browser to http://localhost/owncloud
   2. Enter your desired administrator’s username and password.
   3. Click “Finish Setup”.

> Warning: If you are planning to use the installation wizard, we strongly encourage you to protect it, through some form of password authentication, or access control. If the installer is left unprotected when exposed to the public internet, there is the possibility that a malicious actor could finish the installation and block you out — or worse. So please ensure that only you — or someone from your organization — can access the web installer. 

5. You’re now finished and can start using your new ownCloud server! Of course, there is much more that you can do to set up your ownCloud server for best performance and security. The Admistration Manual provides in-depth instructions that covers cover important installation and post-installation steps. https://doc.owncloud.org/server/10.0/admin_manual/installation/installation_wizard.html#in-depth-guide

# 3. Setting Up the Proxy Server 

Lorem ipsum 

# 4. Setting Up a User

Lorem ipsum

# 5. Logging in as a User

Once you have created the user account, the user will be able to log in and access the server. All the user needs is *lorem ipsum* is a Linux client running Mozilla Firefox or a Windows client running Internet Explorer. 

Lorem ipsum

