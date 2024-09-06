# How to Reset PostgreSQL `postgres` Password

If you've forgotten your PostgreSQL `postgres` password or are unable to log in, follow these steps to reset it securely. The process involves temporarily changing the authentication method, resetting the password, and then restoring the original settings.

## 1. Check the Current Authentication Method in `postgresql.conf`

Before modifying `pg_hba.conf`, it's a good idea to check the `password_encryption` setting in `postgresql.conf` to ensure you know which authentication method is being used.

**Steps**:
1. Locate the `postgresql.conf` file. On Debian/Ubuntu systems, it's usually found in `/etc/postgresql/<version>/main/`. On Red Hat-based systems, it might be in `/var/lib/pgsql/data/`.
2. Open the `postgresql.conf` file with a text editor (as root or with sudo):

   ```bash
    sudo nano /etc/postgresql/<version>/main/postgresql.conf
    ```
   
4. Look for the `password_encryption` setting. It will look like:

   ```plaintext
    # - Authentication -

    password_encryption = scram-sha-256     # scram-sha-256 or md5
    ```
   
6. Take note of the encryption method used (either `scram-sha-256` or `md5`). This will help you understand which method you need to revert to in `pg_hba.conf` after resetting the password.

## 2. Edit the `pg_hba.conf` to Temporarily Trust Connections

The next step is to modify the `pg_hba.conf` file, which controls how PostgreSQL authenticates users. We will temporarily change the authentication method to `trust`, allowing users to log in without a password.

**Steps**:
1. Locate the `pg_hba.conf` file, usually found in `/etc/postgresql/<version>/main/` on Debian/Ubuntu or `/var/lib/pgsql/data/` on Red Hat-based systems.
2. Open the `pg_hba.conf` file with a text editor (as root or with sudo):

   ```bash
    sudo nano /etc/postgresql/<version>/main/pg_hba.conf
    ```
   
4. Find the line that looks like this (specific to your PostgreSQL version and installation):

   ```
    local   all             postgres                                md5
    ```
   
6. Change the `md5` or `scram-sha-256` method to `trust`, so it looks like:

   ```
    local   all             postgres                                trust
    ```
   
8. Save the file and restart PostgreSQL for the changes to take effect:

   ```bash
    sudo systemctl restart postgresql
    ```
   

## 3. Log in to PostgreSQL without a Password

Now that PostgreSQL is set to trust local connections, you can log in without a password.

**Steps**:
1. Open a terminal and log in as the `postgres` user:

   ```bash
    sudo -u postgres psql
    ```
   

## 4. Reset the `postgres` Password

Once you're logged in, you can reset the password for the `postgres` user.

**Steps**:
1. Run the following command to set a new password for the `postgres` user:

   ```sql
    ALTER USER postgres WITH PASSWORD 'new_password';
    ```
    Replace `'new_password'` with your desired password. After resetting the password, exit the PostgreSQL session:
    ```bash
    \q
    ```
    

## 5. Revert `pg_hba.conf` to Use Password Authentication

After resetting the password, it's important to revert the authentication method back to requiring a password for security.

**Steps**:
1. Reopen the `pg_hba.conf` file:

   ```bash
    sudo nano /etc/postgresql/<version>/main/pg_hba.conf
    ```
   
3. Change the `trust` method back to `md5` or `scram-sha-256` (whichever your system used):

   ```
    local   all             postgres                                md5
    ```
   
    Ensure it matches the `password_encryption` setting you noted from `postgresql.conf`.
5. Save the file and restart PostgreSQL:

   ```bash
    sudo systemctl restart postgresql
    ```
   

## Conclusion

Resetting the `postgres` password in PostgreSQL is a straightforward process. By temporarily setting trust authentication, you can gain access to the database without a password, reset the password, and then secure the configuration again. Always remember to restore the original settings to prevent unauthorized access.

This method ensures your database remains secure while allowing you to regain control when you've lost or forgotten your password.
