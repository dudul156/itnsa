# Complete Tutorial for Configuring ITNSA Services on Debian 13

## Table of Contents
1. [DNS Bind9](#dns-bind9)
2. [LDAP OpenLDAP](#ldap-openldap)
3. [Mail Server Postfix+Dovecot](#mail-server-postfixdovecot)
4. [WebMail Roundcube](#webmail-roundcube)
5. [Web Server Nginx](#web-server-nginx)
6. [Reverse Proxy HAProxy](#reverse-proxy-haproxy)
7. [Firewall nftables](#firewall-nftables)
8. [VPN OpenVPN](#vpn-openvpn)

## DNS Bind9
### Installation
```bash
apt update
apt install bind9
```

### Configuration
Edit the `/etc/bind/named.conf.local` file to add your zones:
```bash
zone "example.com" {
    type master;
    file "/etc/bind/db.example.com";
};
```

### Testing DNS
```bash
named-checkconf
named-checkzone example.com /etc/bind/db.example.com
```

## LDAP OpenLDAP
### Installation
```bash
apt install slapd ldap-utils
```

### Configuration
During installation, set the administrator password. You can reconfigure with:
```bash
dpkg-reconfigure slapd
```

## Mail Server Postfix+Dovecot
### Installation
```bash
apt install postfix dovecot-core dovecot-imapd
```

### Configuration
Edit `/etc/postfix/main.cf` for your hostname and other settings. Configure Dovecot in `/etc/dovecot/dovecot.conf`.

## WebMail Roundcube
### Installation
```bash
apt install roundcube
```

### Configuration
Set up your Roundcube in `/etc/roundcube/config.inc.php`.

## Web Server Nginx
### Installation
```bash
apt install nginx
```

### Configuration
Create a server block in `/etc/nginx/sites-available/example.com` and enable it by linking to `sites-enabled`.

## Reverse Proxy HAProxy
### Installation
```bash
apt install haproxy
```

### Configuration
Edit the `/etc/haproxy/haproxy.cfg` to set up frontend and backend servers.

## Firewall nftables
### Installation
```bash
apt install nftables
```

### Configuration
Create rules to manage traffic in `/etc/nftables.conf`.

## VPN OpenVPN
### Installation
```bash
apt install openvpn
```

### Configuration
Use the Easy-RSA package to build a CA and configure OpenVPN settings.