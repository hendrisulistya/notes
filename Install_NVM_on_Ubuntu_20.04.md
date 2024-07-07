# How To Install NVM on Ubuntu 20.04

_Last Updated: July 07, 2024_

NVM, or Node Version Manager, is a handy tool that lets you manage multiple Node.js versions on your Ubuntu system. This allows you to choose the specific Node.js version your applications require, ensuring compatibility and flexibility.

This guide walks you through installing NVM on Ubuntu 20.04 and demonstrates its basic functionalities.

**Prerequisites**

- You'll need a running Ubuntu 20.04 system with shell access.
- Log in with a user account where you want to install Node.js.

**Installing NVM on Ubuntu**

We'll utilize a script provided by the NVM project to facilitate installation. Open a terminal window and follow these steps:

1.  **Install curl:** If you don't already have curl installed, use the following command:

    Bash

    ```
    sudo apt install curl

    ```

2.  **Run the NVM installer script:** Execute the following command to download and run the NVM installer script:

    Bash

    ```
    curl -o- https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash

    ```

    The script creates an environment entry for your current user.

3.  **Load the environment (optional):** NVM's changes typically take effect after a logout and login. Alternatively, you can source your shell's configuration file to load the environment immediately:

    Bash

    ```
    source ~/.bashrc

    ```

**Installing Node.js using NVM**

With NVM installed, you can easily manage Node.js versions on your system. Here are some commands for common tasks:

1.  **Install the latest Node.js version:** The `node` alias typically points to the latest version. Use the following command to install it:

    Bash

    ```
    nvm install node

    ```

2.  **Install a specific Node.js version:** Specify the desired version number after `nvm install`:

    Bash

    ```
    nvm install 16.15.0

    ```

    The first installed version becomes the default.

**Working with NVM**

NVM offers various commands to manage and work with Node.js versions:

1.  **List installed versions:** See a list of all Node.js versions installed on your system with:

    Bash

    ```
    nvm ls

    ```

2.  **List available versions (remote):** Use this command to discover all available Node.js versions on the NVM project's repository:

    Bash

    ```
    nvm ls-remote

    ```

3.  **Use a specific version (current shell):** Activate a particular Node.js version for the current shell session:

    Bash

    ```
    nvm use 14.17.0

    ```

4.  **Check default version:** Find out the default Node.js version set for your user:

    Bash

    ```
    nvm run default --version

    ```

5.  **Run a Node.js script with a specific version:** Execute a Node.js script using a chosen Node.js version:

    Bash

    ```
    nvm exec 10.24.1 server.js

    ```

**Conclusion**

By following this guide, you've successfully installed and configured NVM on your Ubuntu 20.04 system. You've also learned how to manage Node.js versions and leverage NVM to ensure your applications run on the appropriate Node.js environment. Now, you can enjoy the flexibility of having multiple Node.js versions at your disposal!
