---
layout: default
title: Supported Protocols
nav_order: 2
---

# Introduction about the supported protocols

This is an incomplete list of the services supported by ddclient. If your favourite dynamic dns provider isn't here, check the result `ddclient --help` with the most recent version of ddclient. If it's there, check the patches section on https://github.com/ddclient/ddclient and if it's really not supported by ddclient you can try to modify ddclient yourself.

Since ddclient version 3.7, ddclient also supports https to update your favourite provider. Use the ssl=yes option to use this feature.

# Overview of the protocols

{:toc}

# dnspark protocol
The 'dnspark' protocol is used by DNS service offered by www.dnspark.com.  According to [bugs:#54] you have to use ssl and set the server to www.dnspark.org to get it working but that bug isn't confirmed yet. A possible fix for it can be found on [bugs:#36].

Configuration variables applicable to the 'dsnpark' protocol are:

configuration          | information 
-----------------------|-------------
protocol=dnspark       |
server=fqdn.of.service | defaults to www.dnspark.com
backupmx=no            | indicates that DNSPark should be the secondary MX for this domain or host.
mx=any.host.domain     | a host MX'ing for this host or domain.
mxpri=priority         | MX priority.
login=service-login    | login name and password registered with the service
password=service-password |
fully.qualified.host    | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=dnspark,                                         \
    login=my-dnspark.com-login,                               \
    password=my-dnspark.com-password                          \
    myhost.dnspark.com

    ## multiple host update with wildcard'ing mx, and backupmx
    protocol=dnspark,                                         \
    login=my-dnspark.com-login,                               \
    password=my-dnspark.com-password,                         \
    mx=a.host.willing.to.mx.for.me,                           \
    mxpri=10,                                                 \
    my-toplevel-domain.com,my-other-domain.com

    ## multiple host update to the custom DNS service
    protocol=dnspark,                                         \
    login=my-dnspark.com-login,                               \
    password=my-dnspark.com-password                          \
    my-toplevel-domain.com,my-other-domain.com

# dslreports

The 'dslreports1' protocol is used by a free DSL monitoring service offered by www.dslreports.com.

Configuration variables applicable to the 'dslreports1' protocol are: [[br]]

configuration          | information 
-----------------------|-------------
protocol=dslreports1   |
server=fqdn.of.service | defaults to www.dslreports.com
login=service-login    | login name and password registered with the service
password=service-password |
unique-number        | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=dslreports1,                                     \
    server=www.dslreports.com,                                \
    login=my-dslreports-login,                                \
    password=my-dslreports-password                           \
    123456

Note: DSL Reports uses a unique number as the host name. This number can be found on the Monitor Control web page.

# dyndns1

The 'dyndns1' protocol is a deprecated protocol used by the free dynamic DNS service offered by www.dyndns.com. The 'dyndns2' should be used to update the www.dyndns.com service. However, other services are also using this protocol so support is still provided by ddclient.

Configuration variables applicable to the 'dyndns1' protocol are:

configuration          | information 
-----------------------|-------------
protocol=dyndns1       |             
server=fqdn.of.service | defaults to members.dyndns.org
backupmx=no            | indicates that this host is the primary MX for the domain.  Set to yes to mark it as a backup mx.
mx=any.host.domain     | a host MX'ing for this host definition.
wildcard=yes           | add a DNS wildcard CNAME record that points to {host}.  Set to no if you don't need a wildcard.
login=service-login    | login name and password registered with the service
password=service-password |
fully.qualified.host   | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=dyndns1,                                         \
    login=my-dyndns.org-login,                                \
    password=my-dyndns.org-password                           \
    myhost.dyndns.org
    
    ## multiple host update with wildcard'ing mx, and backupmx
    protocol=dyndns1,                                         \
    login=my-dyndns.org-login,                                \
    password=my-dyndns.org-password,                          \
    mx=a.host.willing.to.mx.for.me,backupmx=yes,wildcard=yes  \
    myhost.dyndns.org,my2ndhost.dyndns.org

Note: you only need one of the examples

# dyndns2

The 'dyndns2' protocol is a newer low-bandwidth protocol used by a free dynamic DNS service offered by www.dyndns.com. It supports features of the older 'dyndns1' in addition to others. 

Configuration variables applicable to the 'dyndns2' protocol are:

configuration          | information 
-----------------------|-------------
protocol=dyndns2       |
server=fqdn.of.service | defaults to members.dyndns.org
backupmx=no            | indicates that this host is the primary MX for the domain.
static=no              | indicates that this host has a static IP address.
custom=no              | indicates that this host is a 'custom' top-level domain name.
mx=any.host.domain     | a host MX'ing for this host definition.
wildcard=no            | add a DNS wildcard CNAME record that points to {host}
login=service-login    | login name and password registered with the service
password=service-password |
fully.qualified.host   | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=dyndns2,                                         \
    login=my-dyndns.org-login,                                \
    password=my-dyndns.org-password                           \
    myhost.dyndns.org
    
    ## multiple host update with wildcard'ing mx, and backupmx
    protocol=dyndns2,                                         \
    login=my-dyndns.org-login,                                \
    password=my-dyndns.org-password,                          \
    mx=a.host.willing.to.mx.for.me,backupmx=yes,wildcard=yes  \
    myhost.dyndns.org,my2ndhost.dyndns.org
    
    ## multiple host update to the custom DNS service
    protocol=dyndns2,                                         \
    login=my-dyndns.org-login,                                \
    password=my-dyndns.org-password                           \
    my-toplevel-domain.com,my-other-domain.com

'''Note:''' you only need one of the examples

# easydns

The 'easydns' protocol is used by the for fee DNS service offered by www.easydns.com.

Configuration variables applicable to the 'easydns' protocol are:

configuration          | information 
-----------------------|-------------
protocol=easydns       |
server=fqdn.of.service | defaults to members.easydns.com
backupmx=no|yes        | indicates that EasyDNS should be the secondary MX for this domain or host.
mx=any.host.domain     | a host MX'ing for this host or domain.
wildcard=no            | add a DNS wildcard CNAME record that points to {host}
login=service-login    | login name and password registered with the service
password=service-password |
fully.qualified.host   | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=easydns,                                         \
    login=my-easydns.com-login,                               \
    password=my-easydns.com-password                          \
    myhost.easydns.com

    ## multiple host update with wildcard'ing mx, and backupmx
    protocol=easydns,                                         \
    login=my-easydns.com-login,                               \
    password=my-easydns.com-password,                         \
    mx=a.host.willing.to.mx.for.me,                           \
    backupmx=yes,                                             \
    wildcard=yes                                              \
    my-toplevel-domain.com,my-other-domain.com

    ## multiple host update to the custom DNS service
    protocol=easydns,                                         \
    login=my-easydns.com-login,                               \
    password=my-easydns.com-password                          \
    my-toplevel-domain.com,my-other-domain.com

# namecheap

The 'namecheap' protocol is used by DNS service offered by www.namecheap.com.

Configuration variables applicable to the 'easydns' protocol are:

configuration          | information 
-----------------------|-------------
protocol=namecheap     |
server=fqdn.of.service | defaults to dynamicdns.park-your-domain.com
login=service-login    | login name and password registered with the service
password=service-password |
fully.qualified.host   | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=namecheap,                                         \
    login=my-namecheap.com-login,                               \
    password=my-namecheap.com-password                          \
    myhost.namecheap.com

# zoneedit1

The 'zoneedit1' protocol is used by a DNS service offered by www.zoneedit.com.

Configuration variables applicable to the 'zoneedit1' protocol are:

configuration          | information 
-----------------------|-------------
protocol=zoneedit1     |
server=fqdn.of.service | defaults to www.zoneedit.com
login=service-login    | login name and password registered with the service
password=service-password |
your.domain.name       | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=zoneedit1,                                     \
    server=www.zoneedit.com,                                \
    login=my-zoneedit-login,                                \
    password=my-zoneedit-password                           \
    my.domain.name

    ## multiple host update                                 \
    protocol=zoneedit1,                                     \
    server=www.zoneedit.com,                                \
    login=my-zoneedit-login,                                \
    password=my-zoneedit-password                           \
    my.domain.name,my2nd.domain.com


# Changeip

The 'changeip' protocol is used by DNS services offered by changeip.com.

Configuration variables applicable to the 'changeip' protocol are:

configuration          | information 
-----------------------|-------------
protocol=changeip            |
server=fqdn.of.service       | defaults to nic.changeip.com
login=service-login          | login name and password registered with the service
password=service-password    |
fully.qualified.host         | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=changeip,                                               \
    login=my-my-changeip.com-login,                                  \
    password=my-changeip.com-password                                \
    myhost.changeip.org

ChangeIP is supported since [r150] based on a patch submitted by Michele Giorato in [e85661ad]

# googledomains

The 'googledomains' protocol is used by DNS service offered by www.google.com/domains.

Configuration variables applicable to the 'googledomains' protocol are:

configuration          | information 
-----------------------|-------------
protocol=googledomains       |
login=service-login          | the user name provided by the admin interface
password=service-password    | the password provided by the admin interface
fully.qualified.host         | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=googledomains,                                      \
    login=my-generated-user-name,                                \
    password=my-genereated-password                              \
    myhost.com

    ## multiple host update to the custom DNS service
    protocol=googledomains,                                      \
    login=my-generated-user-name,                                \
    password=my-genereated-password                              \
    my-toplevel-domain.com,my-other-domain.com

Googledomains are supported since [r171] based on a pull request from nelsonjr on github.

# duckdns

The 'duckdns' protocol is used by the free
dynamic DNS service offered by www.duckdns.org.
Check http://www.duckdns.org/install.jsp?tab=linux-cron for API

Configuration variables applicable to the 'duckdns' protocol are:

configuration          | information 
-----------------------|-------------
protocol=duckdns             |
server=www.fqdn.of.service   | defaults to www.duckdns.org
password=service-password    | password (token) registered with the service
non-fully.qualified.host     | the host registered with the service.

Example ddclient.conf file entries:

    ## single host update
    protocol=duckdns,                \
    password=z0mgs3cjur3p4ss         \
    myhost

DuckDNS is supported since [r179] based on a patch provided by by gkranis on github.

# nsupdate
The 'nsupdate' protocol (added in ddclient version 3.8.3) is a wrapper around the `nsupdate` command-line tool. It uses the [RFC 2136 DNS Update protocol](https://www.ietf.org/rfc/rfc2136.txt) to push changes to a zone using the standard DNS communication protocols directly to a DNS server, instead of to a web service operated by a DNS vendor (like most other ddclient protocols do).

To use 'nsupdate', your DNS server or servers must be configured to accept RFC 2136 DNS Update requests (consult the documentation for your DNS server, or its hosting provider, on how to do this). While it is allowed in RFC 2136 to configure DNS updates without authentication, it is strongly discouraged, and ddclient does not support it. You must generate a TSIG key (with, for example, a tool like `dnssec-keygen`), configure your DNS server to accept only those DNS updates signed by that key, and then create a key file for ddclient+nsupdate to use.

There are two supported key file formats. The first is a pair of symmetric key files output by `dnssec-keygen` (or similar tools) with the same name but different extensions (one ends in `.key` and the other in `.private`). When specifying the key file in your ddclient configuration options, you use the path to the file with the `.key` extension, and `nsupdate` uses it and replaces the extension with `.private` to obtain the second key file. However, newer versions of `dnssec-keygen` generate newer key file formats that `nsupdate` might not understand. A more reliable option is to create a key file containing a `named`-compatible key statement and specify the full path to that (with extension) in your ddclient configuration. See the examples below for more information.

Configuration variables applicable to the 'nsupdate' protocol are:

configuration          | information 
-----------------------|-------------
protocol=nsupdate       |
server=fqdn.of.name.server OR server="fqdn.of.name.server port-number"   | Server name defaults to members.dyndns.org, server port defaults to 53. If you need to specify a port number, you must put quotes around the space-separated server address and port number. The server name can also be specified as an IPv4 or IPv6 address instead of a host name.
login=/usr/bin/nsupdate   | Defaults to /usr/bin/nsupdate. Change to the full path to nsupdate on your system if it differs.
password=/path/to/key       | The path to the symmetric HMAC key file with the `.key` extension, or the path to the `named`-compatible key file.
zone=domain.name       | The domain name of the DNS zone under which the host to be updated resides.
ttl=600       | The time to live that should be used for the host record. Defaults to 600 seconds.
tcp=no&#124;yes       | `nsupdate` uses UDP by default, and switches to TCP if the update is too large to fit in a UDP datagram. This setting forces `nsupdate` to always use TCP. Defaults to no (default automatic operation). (This option was added in ddclient version 3.8.next / 3.next.0).
full.qualified.host       | The host whose IP address should be updated.

The following is an example `named`-compatible key file. You can get the algorithm and secret from the HMAC key file with the `.private` extension. If the algorithm in the file contains an underscore, replace it with a hyphen. If the secret is longer than 56 characters, you must insert a space every 56 characters.

~~~~
key my.key.name {
algorithm HMAC-MD5;
secret "SAdhkjhkjashdkjhasdkjbasdkbk8768/+sadfnasdasdkjahsdasdhk jhasdasd/+oeurc8234==";
};
~~~~

Example ddclient.conf file entries:

~~~~
## Single host update with default port, nsupdate path, TTL, and TCP options
protocol=nsupdate
server=ns1.mydomain.com
password=/secure/folder/key-file.key
zone=mydomain.com
dynamic-domain.mydomain.com

## Multiple hosts with nonstandard port and no defaults
protocol=nsupdate
server="ns1.mydomain.com 54"
login=/custom/sbin/nsupdate
password=/secure/folder/key-file.key
zone=mydomain.com
ttl=1800
tcp=yes
dynamic-domain1.mydomain.com,dynamic-domain2.mydomain.com
~~~~

# Your-favorite-provider here
If you want your favorite provider, please don't just ask.  You can provide your own patch against the latest version of ddclient.  It will probably be accepted if:

 * it's a free dynamic DNS provider.
 * if the provider support SSL please add it to the readme.ssl file.
 * if you provide a nice example in the sample-etc_ddclient.conf file.
 * if you don't forget to edit the README.md
 * if your patch applies nicely
 * and if you provide a link to the API.

As we don't use all the possible options, we also like it if you could give support if people are having problems with your provider.
You can also provide a pull request on [github](https://github.com/ddclient/ddclient/)
