# A Guide to SSH Key-Based Authentication

_Last Updated: 2024-07-07_

**Introduction**

Tired of constantly typing your password for SSH connections to your VPS? SSH key-based authentication offers a secure and convenient solution. This guide will walk you through the process of setting up SSH keys for seamless and passwordless login to your VPS.

**Benefits of SSH Key-Based Authentication**

- **Enhanced Security:** Public keys are not transmitted over the network during login, unlike passwords, which are vulnerable to interception.
- **Convenience:** Eliminate the need to remember and enter your password for every SSH session.
- **Efficiency:** Streamline your workflow with faster login times.

**Generating an SSH Key Pair**

The first step involves creating an SSH key pair on your local machine. Here's how:

1.  Open your terminal.
2.  Run the following command, replacing `<path/to/key>` with your desired location for the key files and `<passphrase>` with a strong passphrase (optional but recommended for added security):

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f <path/to/key>

```

- Press Enter when prompted for the key pair location.
- If using a passphrase, enter it twice when prompted.

This command generates two files:

- `<path/to/key>`: Your private key file (**Keep this secure!**).
- `<path/to/key>.pub`: Your public key file.

**Adding the Public Key to your VPS**

There are two methods to transfer your public key to your VPS:

**Method 1: Using ssh-copy-id (Recommended)**

This is the simplest method:

1.  Replace `<username>` with your VPS username and `<server_ip>` with your VPS IP address in the following command:

```
ssh-copy-id -i <path/to/key>.pub <username>@<server_ip>

```

2.  Enter your VPS password when prompted.

This command copies your public key to the authorized_keys file on your VPS, enabling key-based authentication.

**Method 2: Manual Copying**

If `ssh-copy-id` is unavailable, follow these steps:

1.  Access your VPS using another method (e.g., control panel or temporary password).
2.  Open a terminal on your VPS.
3.  Create the `.ssh` directory (if it doesn't exist): `mkdir ~/.ssh`
4.  Create a file named `authorized_keys` within the `.ssh` directory: `nano ~/.ssh/authorized_keys`
5.  Paste the contents of your public key file (`<path/to/key>.pub`) into the `authorized_keys` file.
6.  Save and close the file.
7.  Set the permissions of `authorized_keys` to 600: `chmod 600 ~/.ssh/authorized_keys`

**Logging in with SSH Key**

Once you've added your public key using either method, you can log in to your VPS using your SSH key:

1.  Open your terminal on your local machine.
2.  Run the following command, replacing `<username>` with your VPS username and `<server_ip>` with your VPS IP address:

```
ssh <username>@<server_ip>

```

You should now be able to log in without entering a password (provided you have the private key on your local machine).

**Additional Security Recommendation**

For enhanced security, consider disabling password authentication on your VPS after successfully configuring SSH key-based authentication. This can be done by editing the SSH configuration file (usually `/etc/ssh/sshd_config`) on your VPS and setting `PasswordAuthentication` to `no`.

**Conclusion**

By implementing SSH key-based authentication, you can significantly improve the security and convenience of your VPS access. With a strong key pair and proper configuration, you can enjoy a more streamlined and secure workflow.
