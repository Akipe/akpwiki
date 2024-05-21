---
title: NUT
description: 
published: true
date: 2024-05-21T19:11:37.274Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:11:37.274Z
---

# NUT

## Server

### Installation

```bash
apt install nut nut-client nut-server
```

```bash
lsusb
nut-scanner -U
```

/etc/nut/ups.conf:

```ini
pollinterval = 1
maxretry = 3

[elipseeco0]
        driver = "usbhid-ups"
        port = "auto"
        desc = "EATON Ellipse ECO 800"
        vendorid = "0463"
        productid = "FFFF"
```

/etc/nut/upsd.conf:

```ini
LISTEN 0.0.0.0 3493
```

/etc/nut/upsmon.conf:

```ini
RUN_AS_USER root

MONITOR elipseeco0@localhost 1 admin secret master
```

/etc/nut/upsd.users:

```ini
[admin]
        password = STRONG_PASSWORD
        admin master
        upsmon master
        actions = SET
        instcmds = ALL

[user]
        password = STRONG_PASSWORD
        upsmon slave
        
# For Synology devices :
[monuser]
        password = secret
        upsmon slave
```

```bash
systemctl restart nut-server.service
systemctl status nut-server.service
```

```bash
upsc elipseeco0@localhost
upsc elipseeco0@localhost battery.charge
```

#### TLS

With NSS Mozilla certificate database.

```bash
mkdir -p /etc/nut/ssl/nssdb

# Create database
certutil -d /etc/nut/ssl/nssdb -N

# Create CA
certutil -S \
  -x \
  -d /etc/nut/ssl/nssdb \
  -n "CA_nut" \
  -s "CN=CA_nut,O=MyCompany,ST=MyState,C=US" \
  -t "CT,," \
  -2

# Create certificat sign
certutil -R \
  -d /etc/nut/ssl/nssdb \
  -s "CN=CA_nut,O=MyCompany,ST=MyState,C=US" \
  -o /etc/nut/ssl/nut.csr.der


openssl req -inform der -in /etc/nut/ssl/nut.csr.der -out /etc/nut/ssl/nut.csr

# Create server certificat
certutil -C \
  -x \
  -d /etc/nut/ssl/nssdb \
  -a \
  -i /etc/nut/ssl/nut.csr \
  -o /etc/nut/ssl/nut.pem \
  -2

# Add server certificat to database 
certutil -A -d /etc/nut/ssl/nssdb \
	-n "nut" -a -i /etc/nut/ssl/nut.pem \
	-t ',,'
 
# Check certificates on database
certutil -L -d /etc/nut/ssl/nssdb
certutil -K -d /etc/nut/ssl/nssdb
 
# Fix access
chown -R nut:nut /etc/nut/ssl
```

upsd.conf:

```ini
# Set path to database
CERTPATH /etc/nut/ssl/nssdb
# Set certificate name & database password
CERTIDENT "nut" "PASSWORD_DATABASE"

LISTEN 0.0.0.0 3493
```

#### For Synology clients

/etc/nut/ups.conf:

```ini
# UPS has to be named "ups"
[ups]
        driver = "usbhid-ups"
        # ...
```

/etc/nut/upsd.users:

```ini
[monuser]
	password = secret
    upsmon slave
```

### Web interface

```bash
apt install apache2 nut-cgi
```

/etc/nut/hosts.conf :

```ini
MONITOR elipseeco0@localhost "EATON Ellipse ECO 800 - Rack"
```

```bash
a2enmod cgi
systemctl restart apache2
```

/etc/nut/upsset.conf :

```ini
I_HAVE_SECURED_MY_CGI_DIRECTORY
```

```
http://IP_ADRESS/cgi-bin/nut/upsstats.cgi
```

## Client

```bash
apt install nut-client
```

```bash
upsc elipseeco0@localhost
```

/etc/nut/upsmon.conf:

```ini
RUN_AS_USER root

MONITOR apcname@IP_ADRESS 1 USER PASSWORD slave

MINSUPPLIES 1			# Minimum UPS needed
SHUTDOWNCMD "/sbin/shutdown -h +0" 	# Command execute when need to shutdown
NOTIFYCMD /usr/sbin/upssched 		# Call this to send message
POLLFREQ 5 							# Frequences to check activity in seconds
POLLFREQALERT 1		# Frequence to check activity when in battery mode
HOSTSYNC 15	# How long to wait before giving up
DEADTIME 15
POWERDOWNFLAG /etc/killpower

NOTIFYMSG ONLINE    "UPS %s on line power"
NOTIFYMSG ONBATT    "UPS %s on battery"
NOTIFYMSG LOWBATT   "UPS %s battery is low"
NOTIFYMSG FSD       "UPS %s: forced shutdown in progress"
NOTIFYMSG COMMOK    "Communications with UPS %s established"
NOTIFYMSG COMMBAD   "Communications with UPS %s lost"
NOTIFYMSG SHUTDOWN  "Auto logout and shutdown proceeding"
NOTIFYMSG REPLBATT  "UPS %s battery needs to be replaced"
NOTIFYMSG NOCOMM    "UPS %s is unavailable"
NOTIFYMSG NOPARENT  "upsmon parent process died - shutdown impossible"

NOTIFYFLAG ONLINE   SYSLOG+WALL+EXEC
NOTIFYFLAG ONBATT   SYSLOG+WALL+EXEC
NOTIFYFLAG LOWBATT  SYSLOG+WALL
NOTIFYFLAG FSD      SYSLOG+WALL+EXEC
NOTIFYFLAG COMMOK   SYSLOG+WALL+EXEC
NOTIFYFLAG COMMBAD  SYSLOG+WALL+EXEC
NOTIFYFLAG SHUTDOWN SYSLOG+WALL+EXEC
NOTIFYFLAG REPLBATT SYSLOG+WALL
NOTIFYFLAG NOCOMM   SYSLOG+WALL+EXEC
NOTIFYFLAG NOPARENT SYSLOG+WALL

RBWARNTIME 43200

NOCOMMWARNTIME 600

FINALDELAY 5

```

/etc/nut/nut.conf:

```ini
MODE=netclient
```

/etc/nut/upssched.conf:

```ini
CMDSCRIPT /etc/nut/upssched-cmd
PIPEFN /etc/nut/upssched.pipe
LOCKFN /etc/nut/upssched.lock

AT ONBATT * START-TIMER onbatt 30
AT ONLINE * CANCEL-TIMER onbatt online
AT ONBATT * START-TIMER earlyshutdown 30
AT LOWBATT * EXECUTE onbatt
AT COMMBAD * START-TIMER commbad 30
AT COMMOK * CANCEL-TIMER commbad commok
AT NOCOMM * EXECUTE commbad
AT SHUTDOWN * EXECUTE powerdown
AT SHUTDOWN * EXECUTE powerdown
```

/etc/nut/upssched-cmd:

```sh
#!/bin/sh
 case $1 in
       onbatt)
          logger -t upssched-cmd "UPS running on battery"
          ;;
       earlyshutdown)
          logger -t upssched-cmd "UPS on battery too long, early shutdown"
          /usr/sbin/upsmon -c fsd
          ;;
       shutdowncritical)
          logger -t upssched-cmd "UPS on battery critical, forced shutdown"
          /usr/sbin/upsmon -c fsd
          ;;
       upsgone)
          logger -t upssched-cmd "UPS has been gone too long, can't reach"
          ;;
       *)
          logger -t upssched-cmd "Unrecognized command: $1"
          ;;
 esac
```
```bash
chmod +x /etc/nut/upssched-cmd
```

```bash
systemctl enable nut-client.service
systemctl status nut-client.service
```

## Links

- <https://wiki.ipfire.org/addons/nut/detailed>
- <https://www.youtube.com/watch?v=vyBP7wpN72c>