---
layout: default
title: Usage
nav_order: 4
---

# Introduction

This page describes the configuration for ddclient. If you need anymore info about [supported routers](routers) or [supported protocols](protocols), check the other pages. Other options are described here.

Normally you don't need many arguments when starting ddclient. You can run ddclient as `/usr/sbin/ddclient -daemon 300 -syslog` which should be enough for most configuration. You can put all the needed parameters in the configuration file.

# Usage

usage: `ddclient [options]`
options are:

option              | result
--------------------|-------
-daemon delay       | run as a daemon (default: 0).
-foreground         | do not fork (default: noforeground) (since r113)
-proxy host         | use 'host' as the HTTP proxy.
-server host        | update DNS information on 'host' (default: members.dyndns.org).
-protocol type      | update protocol used (default: dyndns2).
-file path          | load configuration information from 'path' (default:     /etc/ddclient/ddclient.conf).
-cache path         | record address used in 'path' (default: /etc/ddclient/ddclient.cache).
-pid path           | record process id in 'path'.
-use which          | how the should IP address be obtained. (default: ip). More information about the possible use-arguments can be found on the supported routers page
-ip address         | set the IP address to 'address'. 
-postscript script  | run 'script' after updating. The new IP address is added as argument.
-if interface       | obtain IP address from 'interface' (default: ppp0).
-if-skip pattern    | skip any IP addresses before 'pattern' in the output of ifconfig {if}.
-web provider&#124;url | obtain IP address from provider's IP checking page (default: dyndns).
-web-skip pattern | skip any IP addresses before 'pattern' on the web provider&#124;url.
-fw address&#124;url | obtain IP address from firewall at 'address'.
-fw-skip pattern | skip any IP addresses before 'pattern' on the firewall address|url. 
-fw-login login | use 'login' when getting IP from fw. 
-fw-password secret | use password 'secret' when getting IP from fw. 
-cmd program | obtain IP address from by calling {program}. 
-cmd-skip pattern | skip any IP addresses before 'pattern' in the output of {cmd}. 
-login user | login as 'user'. 
-password secret | use password 'secret'. 
-host host | update DNS information for 'host'. 
-{no}ssl   | do updates over encrypted SSL connection (default: nossl).  Works only on a few providers.
-{no}retry | retry failed updates. (default: noretry).
-{no}force | force an update even if the update may be unnecessary (default: noforce).
-timeout max | wait at most 'max' seconds for the host to respond (default: 0).
-{no}syslog | log messages to syslog (default: nosyslog).
-facility {type} | log messages to syslog to facility {type} (default: daemon).
-priority {pri} | log messages to syslog with priority {pri} (default: notice).
-mail address | e-mail messages to {address}.
-mail-failure address | e-mail messages for failed updates to {address}.
-{no}exec | do {not} execute; just show what would be done (default: exec).
-{no}debug | print {no} debugging information (default: nodebug).
-{no}verbose | print {no} verbose information (default: noverbose).
-{no}quiet | print {no} messages for unnecessary updates (default: noquiet).
-help | this message (default: 0).
-{no}query | print {no} ip addresses and exit.

# Configuring ddclient

## Simple configuration

The configuration file, `ddclient.conf`, can be used to define the default behaviour and operation of ddclient. The file consists of sequences of global variable definitions and host definitions. Since version 3.6.5, `ddclient.conf` is located by default in `/etc/ddclient/ddclient.conf`. Another location can be forced by using the -file option

Global definitions look like: `name=value [,name=value]*`

Next example specifies that ddclient should operate as a daemon, checking the eth0 interface for an IP address change every 5 minutes and use the 'dyndns2' protocol by default.

    daemon=600
    use=if, if=eth0
    proxy=proxy.myisp.com
    protocol=dyndns2

Host definitions look like: `[name=value [,name=value]*]* a.host.domain [,b.host.domain] [login] [password]`

Information about the protocols can be found on [the supported protocols](protocols).

## Multiple hosts

Next example specifies two host definitions. The first definition will use the hammernode1 protocol, my-hn-login and my-hn-password to update the ip-address of myhost.hn.org and my2ndhost.hn.org.

The second host definition will use the current default protocol ('dyndns2'), my-login and my-password to update the ip-address of myhost.dyndns.org and my2ndhost.dyndns.org.

The order of this sequence is significant because the values of any global variable definitions are bound to a host definition when the host definition is encountered.


    protocol=hammernode1, \
    login=my-hn-login, password=my-hn-password  myhost.hn.org
    login=my-login, password=my-password  myhost.dyndns.org,my2nd.dyndns.org

See the sample-ddclient.conf file for further examples.

## Multiple IPs
Since version 3.8.0 ddclient support the update of multiple ip's.  More information can be found [on the ddclient forum](https://sourceforge.net/p/ddclient/mailman/message/20383414/)


