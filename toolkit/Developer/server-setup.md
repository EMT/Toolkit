# Server Setup

## See these articles

- [Set up main user](https://www.digitalocean.com/community/articles/initial-server-setup-with-debian-7)
- [Set up firewall](https://www.digitalocean.com/community/articles/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)
- [Set up LAMP](https://www.digitalocean.com/community/articles/how-to-install-linux-apache-mysql-php-lamp-stack-on-debian)

## 1. Create the server

Use Digital Ocean or Rackspace to spin up a new server instance using the latest Debian OS version they offer.

## 2. Set up the main user

We use one user to administrate server instances, to keep things simple. Here’s how to set the main user up:

Log in:
```
ssh root@ip.address.goes.here
```

Type "yes" if you get a warning. Enter the root password (emailed to you after setting up the server instance).

Update:
```
apt-get update
```

Add new user:
```
adduser [your_username]
```

Then add the user to the sudoers:

```
adduser [your_username] sudo
```

Create the password, and then just hit return for each of the other fields.

## 3. Set up firewall and change SSH Port

- [Install UFW](https://www.digitalocean.com/community/articles/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)

`sudo apt-get install ufw`

Change the port number from the default 22 to something less obvious:

- `sudo ufw allow [your ssh port number]/tcp`
- `sudo nano /etc/ssh/sshd_config` change Port from 22 to [your ssh port number]
- `sudo invoke-rc.d ssh restart`

Allow web traffic:

- `sudo ufw allow http`
- `sudo ufw allow https`

And tuen the firwall on:

- `sudo ufw enable`

## 4. Install Apache

```
apt-get install apache2
```

## 5. Install MySQL

```
apt-get install mysql-server
```

You'll be prompted to set up a password for the root user during installation.

Run:

```
mysql_secure_installation
```

Answer yes at each step.

## 6. Install PHP

```
apt-get install php5 php-pear php5-mysql
```

Restart Apache:

```
service apache2 restart
```

## 8. Set up a public site, served by Apache

### Create directory structure

```
mkdir ~/web
mkdir ~/web/site_name
mkdir ~/web/site_name/logs
```

### Create virtual host

```
nano /etc/apache2/sites-available/site_name
```

Add the following, replacing the placeholder stuff

```
# domain: example.com
# public: /path/to/public/root

<VirtualHost *:80>

  # Admin email, Server Name (domain name) and any aliases
  ServerAdmin someone@example.com
  ServerName  example.com
  ServerAlias www.example.com


  # Index file and Document Root (where the public files are located)
  DirectoryIndex index.php
  DocumentRoot /path/to/public/root


  # Custom log file locations
  ErrorLog  /path/to/logs/error.log
  CustomLog /path/to/logs/access.log combined

  AllowEncodedSlashes On

</VirtualHost>
```

#### For an Li3 app

```
DocumentRoot: /home/user/web/appname/reponame/app/webroot
ErrorLog  /home/user/web/appname/logs/error.log
CustomLog /home/user/web/appname/logs/access.log combined
```

### Enable site

```
a2ensite site_name
service apache2 restart
```

## 7. Other bits you’ll probably need

Enable mod rewrite:

```
a2enmod rewrite 
service apache2 restart
```

Install Git:
```
apt-get install git-core
```
