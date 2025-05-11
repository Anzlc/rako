# Rako cheatsheet

## Apache server

### Install

    sudo apt update
    sudo apt install apache2

### Configurations

    sudo nano /etc/apache2/sites-available/000-default.conf

#### Contents

Fill with your info

    <VirtualHost *:80>
        ServerName jaz.example.internal

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/jaz


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

    </VirtualHost>

    <VirtualHost *:80>
        ServerName ocena.example.internal

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/ocena


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

    </VirtualHost>

#### Setup permissions

In directory /var/www/

    sudo chown -R skrbnik www-data html/
    sudo chmod 775 html/

### Where the website

    /var/www/

---

## SSH

    sudo apt install openssh-server

---

## Network setup

    sudo nano /etc/network/interfaces

Also set VirtualBox adapter to Bridged aka Povezan adapter/vmesnik.

### Static

    auto enp0s3
    iface enp0s3 inet static
        address <ip>/<cidr mask>
        gateway <ip>
        dns-nameservers <ip> # One or more

### DHCP

    auto enp0s3
    iface enp0s3 inet dhcp

---

## DNS Setup

**CNAME** - Points to another domain (Canonical name)

    jaz.neki.internal -> me.neki.internal

**A** - Points to an IPv4 address

    me.neki.internal -> 213.123.2.12 (Ker kol ip pač)
