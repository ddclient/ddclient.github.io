---
layout: default
title: Home
nav_order: 1
---

# Introduction

`ddclient` updates dynamic DNS entries for accounts on a wide range of dynamic DNS services.

This is applicable to a wide range of use cases. It's commonly used when you have an IP address that changes regularly (e.g. on a residential network), that you want to keep service pointing at (e.g. your domain name).

# Installation

See the [GitHub README](https://github.com/ddclient/ddclient?tab=readme-ov-file#installation).

# Configuration

ddclient has two primary means of configuration:
- (Recommended) The `ddclient.conf` file, which defaults to `/etc/ddclient/ddclient.conf`.
- Passing in arguments via [the command line](#command-line-arguments).

There are three key pieces to configuring ddclient:
- [General settings](./general.md)
- [Routers](./routers.md): where should ddclient find your IP? For example, [ipify](https://www.ipify.org/), or one of 20+ others.
- [Protocols](./protocols.md): what should ddclient update when your IP changes? For example, [DuckDNS](https://www.duckdns.org/), [Cloudflare](https://developers.cloudflare.com/dns/manage-dns-records/how-to/managing-dynamic-ip-addresses/), or one of [30+ others](./protocols.md).

## Example

A typical configuration file looks like:

```
# General config
daemon=300

# Router
usev4=webv4,webv4=ipify-ipv4

# Protocol
protocol=dyndns2
login=myUsername
password=myPassword
myhost.dyndns.org
```

With this config, executing `ddclient` would start a daemon that every 300 seconds would:
1. Get your IPv4 address from the ipify web service.
2. Login to your dyndns account with the given username and password, and update the `myhost.dyndns.org` domain to your current IPv4 address.

You can set up `ddclient` to run on automatically using other packages on your system, such as [systemd](https://github.com/ddclient/ddclient/blob/master/sample-etc_systemd.service), [cron](https://github.com/ddclient/ddclient/blob/master/sample-etc_cron.d_ddclient), [dhclient](https://github.com/ddclient/ddclient/blob/master/sample-etc_dhclient-exit-hooks), [dhcpc](https://github.com/ddclient/ddclient/blob/master/sample-etc_dhcpc_dhcpcd-eth0.exe) and others. There are additional sample startup scripts in the [GitHub repository](https://github.com/ddclient/ddclient).

## Command-line arguments

For simplicity, it's recommended you use the `ddclient.conf` file over command line arguments. If you can't use the default location, you can use the `file` argument only to read config from a different file, e.g. `ddclient -file ddclientCustom.conf`

However, any arguments can also be provided via the command line when invoking ddclient. For example:

```
ddclient -daemon 300 -protocol dyndns2 -login myUsername -password myPassword myhost.dyndns.org
```

ddclient prioritizes command line arguments, then falls back to `ddclient.conf`, then falls back to in-built defaults.

# Support

If you need extra help, want to report a bug, or submit a feature request, [create a GitHub issue](https://github.com/ddclient/ddclient/issues/new). Before posting, check it is not a duplicate and the problem is present on the latest version of ddclient.

If you want to contribute code to ddclient, raise a pull request on GitHub.
