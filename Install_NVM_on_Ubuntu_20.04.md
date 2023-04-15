
How To Install NVM on Ubuntu 20.04
==================================

NVM is a Node Version Manager tool. Using the NVM utility, you can install multiple node.js versions on a single system. You can also choose a specific Node version for applications. It also provides an option to auto-select the node version using the .nvmrc configuration file.


This tutorial will help you to install NVM on Ubuntu 20.04 Linux system. Also, allow you to install different node versions and other useful examples.

Prerequisites
-------------

-   You must have a running Ubuntu 20.04 Linux system with shell access.
-   Log in with a user account to which you need to install node.js.

Installing NVM on Ubuntu
------------------------

A shell script is available for the installation of nvm on the Ubuntu 20.04 Linux system. Open a terminal on your system or connect a remote system using SSH. Use the following commands to install curl on your system, then run the nvm installer script.

```
sudo apt install curl
```

The nvm installer script creates an environment entry to the login script of the current user. You can either log out and log in again to load the environment or execute the below command to do the same.

```
source ~/.bashrc
```

The nvm installation is successfully completed on your Ubuntu system.

Installing Node using NVM
-------------------------

You can install multiple node.js versions using nvm. And use the required version for your application from installed node.js.


Install the latest version of node.js. Here node is the alias for the latest version.

```
nvm install node
```

To install a specific version of node:

```
nvm install 12.18.3
```

You can choose any other version to install using the above command. The very first version installed becomes the default. New shells will start with the default version of the node (e.g., nvm alias default).


Working with NVM
----------------

You can use the following command to list installed versions of the node for the current user.


```
nvm ls
```


With this command, you can find the available node.js version for the installation.

```
nvm ls-remote
```

You can also select a different version for the current session. The selected version will be the currently active version for the current shell only.

```
nvm use 12.18.3
```

To find the default Node version set for the current user, type:

```
nvm run default --version
```

You can run a Node script with the desired version of node.js using the below command:

```
nvm exec 12.18.3 server.js
```

Conclusion
----------

In this tutorial, you have learned to install nvm on Ubuntu 20.04 LTS (Focal Fossa) Linux system. Also, get a basic understanding of the uses of nvm.
