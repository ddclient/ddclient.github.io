---
layout: default
title: "Configuration: General"
nav_order: 2
---

# Introduction

This page describes general configuration options for ddclient. This is one of the three pieces of ddclient configuration alongside routers and protocols. Start on the [homepage](./index.md) for a breakdown of how these interact.

Most users are unlikely to need to specify many of these options.

# Reference

option              | result
--------------------|-------
-daemon delay       | run as a daemon, every `delay` number of seconds (default: 0).
-{no}foreground     | do not fork (default: noforeground) (since r113)
-proxy host         | use 'host' as the HTTP proxy.
-server host        | update DNS information on 'host' (default: members.dyndns.org).
-protocol type      | update protocol used (default: dyndns2).
-file path          | load configuration information from 'path'. Only works when given as a command line argument. (default: /etc/ddclient/ddclient.conf).
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
-help | print a help message (default: nohelp).
-{no}query | print {no} ip addresses and exit.
