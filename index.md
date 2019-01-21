ownCloud 10.0.10: A Quick Start Guide
==============

**Author:** *Suzanne Burns* 


# Overview 

ownCloud is a file sharing server that puts the control and security of your own data back into your hands. It includes the ownCloud server, which runs on Linux, client applications for Microsoft Windows, Mac OS X and Linux, and mobile clients for the Android and Apple iOS operating systems.

This quick start serves as a step-by-step guide to installing it from ownCloud's *Open Build Service* packages. It also covers how to configure the proxy server, set the user in ownCloud, and how users can install the *Desktop Sychronization Client* and access the server:

+ [Installing ownCloud](#install)
+ [Setting Up the Proxy Server](#proxy) 
+ [Setting Up a User in ownCloud](#user)
+ [Installing the Desktop Synchronization Client](#deckofficer) 

> Need enterprise features? See [Installing & Upgrading ownCloud Enterprise Edition](https://doc.owncloud.org/server/10.0/admin_manual/enterprise/installation/install.html).

<a name="install"></a>
# Installing ownCloud 

Installing ownCloud on Linux from the *Open Build Service* packages is the preferred method. These are maintained by ownCloud engineers, and you can use your package manager to keep your ownCloud server up-to-date. The recommended package to use is *owncloud-files*. See [Linux Package Manager Installation](https://doc.owncloud.org/server/10.0/admin_manual/installation/linux_installation.html) for more information about package managers. 

1. Download the package manager you want to use from ownCloud's [Download Center](https://owncloud.org/download/). 

> Note: The package manager only installs ownCloud; it does not install Apache, a database, or any of the required PHP dependencies. These can be installed using a classic LAMP stack (Linux, Apache, MySQL/MariaDB, PHP). 

2. Install the LAMP stack. If there are no packages for your Linux distribution, you may prefer to install from source. This allows you to create your own custom LAMP stack without dependency conflicts with the ownCloud package. See [Manual Installation on Linux](https://doc.owncloud.org/server/10.0/admin_manual/installation/source_installation.html) for a step-by-step guide to installing your own LAMP stack.  

3. After you have installed the LAMP stack, you must update the [package manager's configuration](http://download.owncloud.org/download/repositories/10.0/owncloud/). Configurations are available for the following Linux distributions:

   + Ubuntu 14.04 & 16.04
   + Debian 7 & 8
   + RHEL 6 & 7
   + CentOS 7.2 & 7.3
   + SLES 11SP4 & 12SP2
   + openSUSE Leap 42.2 & 42.3

4.  Once your package manager's configuration has been updated, follow the instructions included in the configuration to install ownCloud. 

5.  When all ownCloud files are installed, the last step to completing the installation is to run the *Installation Wizard*. This involves the following three steps:

   1. Point your web browser to http://localhost/owncloud.
   2. Enter your desired administrator’s username and password.
   3. Click the *Finish Setup* button.

> Warning: If you are planning to use the installation wizard, we strongly encourage you to protect it, through some form of password authentication, or access control. If the installer is left unprotected when exposed to the public internet, there is the possibility that a malicious actor could finish the installation and block you out — or worse. So please ensure that only you, or someone from your organization, can access the web installer. 

You’re now finished and can start using your new ownCloud server! Of course, there is much more that you can do to set up your ownCloud server for best performance and security. The Administration Manual provides [in-depth instructions](https://doc.owncloud.org/server/10.0/admin_manual/installation/installation_wizard.html#in-depth-guide) that covers important installation and post-installation steps. 

<a name="proxy"></a>
# Configuring the Proxy Server 

ownCloud uses the config/config.php file to control server operations. See [Core Config.php Parameters](https://doc.owncloud.org/server/10.0/admin_manual/configuration/server/config_sample_php_parameters.html) in the *Server Configuration* section of the *Administration Manual* for more information about configurable parameters within ownCloud, as well as information about ownCloud's default values (with examples). 

Most options are configurable on your *Administration* page, so it is usually not necessary to edit *config/config.php*. One essential configuration in setting up ownCloud is to configure the proxy server. These setting allow you to enable users to connect to the Owncloud server using the server's IP address and specify the port.

You can configure the following:

> 'overwritehost' => '',

The automatic hostname detection of ownCloud can fail in certain reverse proxy and CLI/cron situations. These proxy settings allow you to manually override the automatic detection; for example, www.example.com, or specify the port, for example,  www.example.com:8080.

> 'overwriteprotocol' => '',

When generating URLs, ownCloud attempts to detect whether the server is accessed via *https* or *http*. However, if ownCloud is behind a proxy and the proxy handles the https calls, ownCloud would not know that ssl is in use, which would result in incorrect URLs being generated. Valid values are http and https.

> 'overwritewebroot' => '',

ownCloud attempts to detect the webroot for generating URLs automatically. For example, if www.example.com/owncloud is the URL pointing to the ownCloud instance, the webroot is */owncloud*. When proxies are in use, it may be difficult for ownCloud to detect this parameter, resulting in invalid URLs.

> 'overwritecondaddr' => '',

This option allows you to define a manual override condition as a regular expression for the remote IP address. The keys *overwritewebroot*, *overwriteprotocol*, and *overwritehost* are subject to this condition.

For example, defining a range of IP addresses starting with 10.0.0. and ending with 1 to 3: * ^10\.0\.0\.[1-3]$a

> 'overwrite.cli.url' => '',

Use this configuration parameter to specify the base URL for any URLs which are generated within ownCloud using any kind of command line tools (*cron* or *occ*). The value should contain the full base URL: https://www.example.com/owncloud. As an example, alerts shown in the browser to upgrade an app are triggered by a cron background process and therefore uses the url of this key, even if the user has logged in via a different domain defined in key trusted_domains. When the user clicks an alert like this, he will be redirected to that URL and must log in again.

> 'htaccess.RewriteBase' => '/',

To have clean URLs without */index.php* this parameter needs to be configured. This parameter will be written as “RewriteBase” on update and installation of ownCloud to your .htaccess file. While this value is often simply the URL path of the ownCloud installation it cannot be set automatically properly in every scenario and needs thus some manual configuration.

In a standard Apache setup this usually equals the folder that ownCloud is accessible at. So if ownCloud is accessible via “https://mycloud.org/owncloud,” the correct value would most likely be “/owncloud”. If ownCloud is running under “https://mycloud.org/,” then it would be “/”.

Note that the above rule is not valid in every case, as there are some rare setup cases where this may not apply. However, to avoid any update problems this configuration value is explicitly opt-in.

After setting this value run *occ maintenance:update:htaccess*. Now, when the following conditions are met ownCloud URLs won’t contain index.php:

   + mod_rewrite is installed
   + mod_env is installed

> 'proxy' => '',

The URL of your proxy server, for example *proxy.example.com:8080*.

> 'proxyuserpwd' => '',

This is the optional authentication for the proxy to use to connect to the internet. The format is: *username:password*.

<a name="user"></a>
# Setting Up a User

You can set up new user accounts in the *User Management* page of your ownCloud Web UI. See [User Management](https://doc.owncloud.org/server/9.1/admin_manual/configuration_user/user_configuration.html) in the *Administration Manual* for more detailed information about managing user settings. 

User accounts have the following properties:

+ **Login Name (Username)**: The unique ID for the ownCloud user; it cannot be changed. 
+ **Full Name**: The user’s display name that appears on file shares, the ownCloud Web interface, and emails. Admins and users may change the Full Name anytime. If the *Full Name* is not set it defaults to the login name. 
+ **Password**: The admin sets the new user’s first password. Both the user and the admin can change the user’s password at anytime. 
+ **Groups**: You may create groups, and assign group memberships to users. By default new users are not assigned to any groups. 
+ **Group Admin**: Group admins are granted administrative privileges on specific groups, and can add and remove users from their groups. 
+ **Quota**: The maximum disk space assigned to each user. Any user that exceeds the quota cannot upload or sync data. You have the the option to include external storage in user quotas. 

To create a new user account: 

1. Enter the new user’s login name and their initial password in the fields provided. 

> Login names may contain letters, numbers, dashes, underscores, periods, and at (@) signs. After creating the user account, you can enter their *Full Name* if it is different than the login name, or leave it for the user to complete. 

2. Assign group memberships as needed in the *Users* dropdown.
3. Click the *Create* button.
4. After you create the user account you can automatically send the user a notification with their new login information by selecting *Send Email* in the control panel on the lower left sidebar and enter the new user’s email address. 

<a name="deckofficer"></a>
# Installing the Desktop Synchronization Client

Users can install the *ownCloud Desktop Synchronization Client* to access the server. the *ownCloud Desktop Synchronization Client* is available for Microsoft Windows, Mac OS X and Linux. 

> There are also mobile clients for the Android and Apple iOS operating systems, however. See the [ownCloud Server User Manual](https://doc.owncloud.com/server/user_manual/index.html) for more information about ownCloud desktop and mobile clients.

1. Download the latest version of the *ownCloud Desktop Synchronization Client* from the ownCloud's [Download Center](https://owncloud.org/download/). There are clients for Linux, macOS, and Microsoft Windows.

   + Installation on Mac OS X and Windows is the same as for any software application: download the program and then double-click it to launch the installation, and then follow the installation wizard. After it is installed and configured the sync client will automatically keep itself updated. 

   + Linux users must follow the instructions on the download page to add the appropriate repository for their Linux distribution, install the signing key, and then use their package managers to install the desktop sync client. Linux users will also update their sync clients via package manager, and the client will display a notification when an update is available. 

2. If you just want to install *ownCloud Desktop Synchronization Client* on your local system, you can launch the .msi file and configure it in the wizard that pops up. See [Customizing the Windows installation](https://doc.owncloud.com/desktop/2.5/installing.html#customizing-the-windows-installation) in the *User Manual* for more information on these custom settings.

3. The installation wizard takes you step-by-step through configuration options and account setup. First you need to enter the URL of your ownCloud server in the *Server Address* field. Click the *Next* button to continue.

4. Enter your ownCloud login information in the *Username* and *Password* fields. Click the *Next* button to continue.

5. The “Local Folder Option” screen allows you to choose to sync all of your files on the ownCloud server, or select individual folders to sync. 

   + If you want to sync only specific folders, select *Choose What to Sync* and select the folder you want to include. The option *Sync everything from the server* is the default setting.
   + The default *Local Folder* is ownCloud, in your home directory. You can change this as needed.

6. When you have completed specifying your sync options, click the *Connect* button. The client will attempt to connect to your ownCloud server. When it is successful you’ll see two buttons, one to connect to your ownCloud Web GUI and one to open your local folder. The sytem will begin synchronizing your files.

Once installed, the user can log in to the *ownCloud Desktop Synchronization Client* and access the server.


