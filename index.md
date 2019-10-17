---
layout: default
title: Home page
nav_order: 1
---

<!-- 

Ddclient is a Perl client used to update dynamic DNS entries for accounts on 'Dynamic DNS Network Services' free DNS service. It currently supports a lot of different routers and a few different services.

[[project_screenshots]]
[[project_admins]]
[[download_button]]

Other instuctions on how to use the wiki syntax can be found on https://sourceforge.net/p/necessitas/wiki/markdown_syntax/ 

Project for rent
Unfortunatly I (wimpunk) don't have any spare time to work on this project.  If there's anyone out there willing to help me and eventually tak over this project, pleas let it know at [the mailing list](https://sourceforge.net/p/ddclient/mailman/message/36589979/)
-->

# Index

1. TOC
{:toc}

<!--
# Important notice
There are a few changes coming.

* Because of some recent personal changes I'm not having enough time to work on this project any more.  There are only some obvious bugreports which get solved quickly but others stay there forever.
* Dyndns decided to change their business model and [they stopped offering free account](http://www.dyndnscommunity.com/questions/21580/from-dyn-what-happened-to-free-accounts.html).  It made me decide to make dyndns less important for ddclient.
* Sourceforge [decided to retire the hosted apps](http://sourceforge.net/blog/hosted-apps-migration-update/) which means this trac environment will come to an end.  A backup of the old trac can be found on http://ddclient.tisnix.be but all usefull data will be moved to the new environment.
-->

# Introduction

DDclient is a Perl client used to update dynamic DNS entries for accounts on Dynamic DNS Network Service Provider. It was originally written by Paul Burry and is now mostly by wimpunk.  It has the capability to update more than just [dyndns](http://www.dyndns.com) and it can fetch your WAN-ipaddress in a few different ways. Check the configuration pages to find how to do this.

According to [cudeso.be](http://linux.cudeso.be/linuxdoc/ddclient.php):
> DDclient is a small but full featured client requiring only Perl and no additional modules. It runs under most UNIX OSes and has been tested under GNU/Linux and FreeBSD. Supported features include: operating as a daemon, manual and automatic updates, static and dynamic updates, optimized updates for multiple addresses, MX, wildcards, abuse avoidance, retrying failed updates, and sending update status to syslog and through e-mail.

# News

 * [Ddclient 3.9.0 released](https://github.com/ddclient/ddclient/releases/tag/v3.9.0)

You can also check [the mailinglist](https://sourceforge.net/p/ddclient/mailman/message/36589979/) to find out what's going on.

# Installation
Most distributions have a recent version of ddclient.  Use it unless you really need the latest version. On debian-based systems you can run `apt-get install ddclient` and it will install ddclient.  Unless there is a good reason, you should't use the release link.

[release link](https://github.com/ddclient/ddclient/releases){: .btn }

Ddclient doesn't have an automatic installation procedure. Get the tar-file from using the download button and untar it. Copy the perl script to your favorite location (ex. /usr/sbin)
and create a ``/etc/ddclient/ddclient.conf`` configuration file. Don't forget to create the cache directory.

If you want the bleeding edge of ddclient, you can access the latest version using svn. Instructions can be found on [the code section](/p/ddclient/code/). Or if you prefer git, you can also fork the latest version from [ddclient on github](https://github.com/ddclient/ddclient)

When upgrading just replace the ddclient file by the one from the package, read the release notes and modify the cache file.  Some distributions use other directories than the default directories used by ddclient.  If you want to reuse the old once, you will have to change the configuration.

# Configuration
<!-- this should be moved to a separate wiki page -->
If you installed ddclient by using the installer of your distribution, it probably already asked you some questions and prepared a useful config file.

There are a few configuration examples provided which you can copy to ``/etc/ddclient/ddclient.conf`` and modify. More info about the configuration can be found on the [usage page](usage). There's also a sample configuration delivered with ddclient.

A typical configuration like:

    # /etc/ddclient/ddclient.conf
    #
    protocol=dyndns2
    use=web
    login=mylogin
    password=mypassword
    myhost.dyndns.org

You can run ddclient as ``/usr/sbin/ddclient -daemon 300 -syslog`` and put it in your startup scripts. There are samples of startup scripts provided with ddclient.  Most distributions provide a generic startup sample.  You can change it to work with ddclient.  As there are to many different distributions, ddclient doesn't maintain all of them. 

# Documentation
<!-- keep it shorter on this place -->
The documentation about the configuration has been split into three sections.  The [usage page](usage) describes the most parts of the configuration while the [supported protocols](protocols) page describes the protocol-specific options. If you want to know how to use ddclient with your router, check the [supported routers](routers).

Debugging ddclient looks pretty hard but it isn't. First try to put as less as necessary in your configuration. Try to run

    ./ddclient -daemon=0 -noquiet -debug 

and check the result. Try to add the features you need and check it again.

Once you're happy with the result, run it as a daemon.

If this doesn't work for you, there are a few places where you can look for help. If you need any help in configuring ddclient,
You could try ddclient --help. It should give you all the possible configuration options so.

If you think your configuration is correct, but ddclient doesn't work as you expected, you can enable debug and verbose messages by running

    ddclient -daemon=0 -debug -verbose -noquiet

We know the manual is not very clear, you have to read the example configurations included in the tar-file or you can run ``ddclient --help`` to get more help.

# Help and bugreporting
If you need extra help, have any bug to report, an enhancement to submit or a feature request, you can use the [ddclient mailing list](https://lists.sourceforge.net/lists/listinfo/ddclient-support) or [create a new issue](https://github.com/ddclient/ddclient/issues/new).  Please only post bugs against the latest version of ddclient.
If you want to provide a patch for ddclient, please use a pull request on github.  It's the easiest way of working.
