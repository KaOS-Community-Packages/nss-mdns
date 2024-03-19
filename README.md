# nss-mdns

## Overview

**nss-mdns** is a plugin for the GNU Name Service Switch (NSS) functionality of the GNU C Library (glibc) providing host name resolution via Multicast DNS (aka Zeroconf, aka Apple Rendezvous, aka Apple Bonjour), effectively allowing name resolution by common Unix/Linux programs in the ad-hoc mDNS domain .local.

nss-mdns provides client functionality only, which means that you have to run a mDNS responder daemon (e.g. [Avahi](http://avahi.org/)) seperately from nss-mdns if you want to register the local host name via mDNS.

## Installation

```
kcp -u
kcp -i nss-mdns
```

This installs the relevant software and modifies /etc/nsswitch.conf to activate it.  The pre-existing file is saved as /etc/nsswitch.conf.bak.

If you run a firewall, don't forget to allow UDP traffic to the the mDNS multicast address `224.0.0.251` on port 5353.
