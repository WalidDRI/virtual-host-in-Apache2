# virtual-host-in-Apache2
create a new virtual host in Apache2
To create a new virtual host in Apache2, you can follow these steps:

1. Create a new configuration file: Apache2 typically stores virtual host configuration files in the `/etc/apache2/sites-available/` directory. You can create a new configuration file for your virtual host by using a text editor. For example, let's create a file named `mywebsite.conf`:

   ```shell
   sudo nano /etc/apache2/sites-available/mywebsite.conf
   ```

2. Configure the virtual host: Inside the configuration file, you'll need to specify the settings for your virtual host. Here's an example of a basic configuration:

   ```apache
   <VirtualHost *:80>
       ServerName mywebsite.com
       ServerAlias www.mywebsite.com
       DocumentRoot /var/www/mywebsite
       ErrorLog ${APACHE_LOG_DIR}/error.log
       CustomLog ${APACHE_LOG_DIR}/access.log combined
   </VirtualHost>
   ```

   Customize the settings according to your requirements. The important directives to configure are:

   - `ServerName`: Specify the primary domain name for your website.
   - `ServerAlias`: Optionally, specify additional domain names or aliases for your website.
   - `DocumentRoot`: Set the directory path where the website files are located.
   - `ErrorLog` and `CustomLog`: Define the log file paths for error and access logs respectively.

   You can add more directives or modify them based on your specific needs.

3. Enable the virtual host: Once the configuration file is created, you need to enable the virtual host by creating a symbolic link to it in the `/etc/apache2/sites-enabled/` directory. Use the following command:

   ```shell
   sudo a2ensite mywebsite.conf
   ```

   This command creates a symbolic link from the `sites-available` directory to the `sites-enabled` directory.

4. Disable default virtual host (if needed): If you want to disable the default virtual host that comes with Apache2, you can use the following command:

   ```shell
   sudo a2dissite 000-default.conf
   ```

   This command disables the default virtual host by removing the symbolic link from the `sites-enabled` directory.

5. Restart Apache2: To apply the changes, restart the Apache2 service:

   ```shell
   sudo service apache2 restart
   ```

   Apache2 will read the new virtual host configuration and make it available.

Now, your new virtual host should be active and accessible. Make sure to upload your website files to the specified `DocumentRoot` directory (`/var/www/mywebsite` in the example) and configure any necessary DNS settings to point your domain name(s) to your server's IP address.
