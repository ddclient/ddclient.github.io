---
layout: default
title: "Configuration: routers"
nav_order: 3
---

# Introduction

This page explains how to configure a router for ddclient, which is where ddclient will get your IP address. This is one of the three pieces of ddclient configuration alongside general config and protocols. Start on the [homepage](./index.md) for a breakdown of how these interact.

To configure your favorite router, modify the `use` property in your configuration to something like `use=linksys-ver2`. Don't forget to put your router password and login in the configuration.

This is an incomplete list of routers supported by ddclient. If your favorite isn't here, check the result of `ddclient --help` with the most recent version of ddclient. If it's not there, check the code at https://github.com/ddclient/ddclient and if it's really not supported by ddclient you can try to modify ddclient yourself.

# Overview

{:toc}

# Non router option

| option   | information |
| -------- | ----------- |
| use=web | obtain IP from an IP discovery page on the web. |
| use=if | obtain IP from the `-if {interface}`. |
| use=ip | obtain IP from `-ip {address}`. |
| use=cmd | obtain IP from the `-cmd {external-command}`. |
| use=fw | obtain IP from the firewall specified by `-fw {type|address}`. |

# Incomplete list of supported routers

option   | information
-------- | -----------
use=3com-3c886a | obtain IP from 3com 3c886a 56k Lan Modem at the -fw {address}.
use=3com-oc-remote812 | obtain IP from 3com !OfficeConnect Remote 812 at the -fw {address}.
use=alcatel-stp | obtain IP from Alcatel Speed Touch Pro at the -fw {address}.
use=allnet-1298 | obtain IP from Allnet 1298 at the -fw {address}.
use=cayman-3220h | obtain IP from Cayman 3220-H DSL at the -fw {address}.
use=cisco | obtain IP from Cisco FW at the -fw {address}.
use=dlink-604 | obtain IP from D-Link DI-604 at the -fw {address}.
use=dlink-614 | obtain IP from D-Link DI-614+ at the -fw {address}.
use=e-tech | obtain IP from E-tech Router at the -fw {address}.
use=elsa-lancom-dsl10 | obtain IP from ELSA !LanCom DSL/10 DSL FW at the -fw {address}.
use=elsa-lancom-dsl10-ch01 | obtain IP from ELSA !LanCom DSL/10 DSL FW (isdn ch01) at the -fw {address}.
use=elsa-lancom-dsl10-ch02 | obtain IP from ELSA !LanCom DSL/10 DSL FW (isdn ch01) at the -fw {address}.
use=linksys | obtain IP from Linksys FW at the -fw {address}.
use=linksys2 | obtain IP from Linksys FW ver 2 at the -fw {address}.
use=maxgate-ugate3x00 | obtain IP from !MaxGate UGATE-3x00 FW at the -fw {address}.
use=netgear-rt3xx | obtain IP from Netgear FW at the -fw {address}.
use=netopia-r910  | obtain IP from Netopia R910 FW at the -fw {address}.
use=smc-barricade | obtain IP from SMC Barricade FW at the -fw {address}.
use=sohoware-nbg800 | obtain IP from SOHOWare !BroadGuard NBG800 at the -fw {address}.
use=vigor-2200usb | obtain IP from Vigor 2200 USB at the -fw {address}.
use=watchguard-soho|obtain IP from Watchguard SOHO FW at the -fw {address}.
use=xsense-aero|obtain IP from Xsense Aero at the -fw {address}.

# Other configurations

* [Using ddclient on Siemens 6520 modem](http://sourceforge.net/forum/forum.php?thread_id=2024597&forum_id=399428)
* [Router (wireless) Linksys WRT610N](https://sourceforge.net/tracker2/?func=detail&atid=676130&aid=2407927&group_id=116817)
