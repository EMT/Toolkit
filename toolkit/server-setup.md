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

Add new user:
```
adduser [your_username]
```

Create the password, and then just hit return for each of the other fields.

## 3. Set up firewall and change SSH Port

- [Install UFW](https://www.digitalocean.com/community/articles/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)

Change the port number from the default 22 to something less obvious:

- `sudo ufw allow [your ssh port number]/tcp`
- `sudo nano /etc/ssh/sshd_config` change Port from 22 to [your ssh port number]
- `sudo invoke-rc.d ssh restart`
