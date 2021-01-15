# nss-mdns
*version 0.14.1*.

**nss-mdns** is a plugin for the GNU Name Service Switch (NSS) functionality of the GNU C Library (glibc) providing host name resolution via Multicast DNS (aka Zeroconf, aka Apple Rendezvous, aka Apple Bonjour), effectively allowing name resolution by common Unix/Linux programs in the ad-hoc mDNS domain .local.

nss-mdns provides client functionality only, which means that you have to run a mDNS responder daemon seperately from nss-mdns if you want to register the local host name via mDNS. I recommend Avahi.

nss-mdns is very lightweight (9 KByte stripped binary .so compiled with -DNDEBUG=1 -Os on i386, gcc 4.0), has no dependencies besides the glibc and requires only minimal configuration.

nss-mdns tries to contact a running avahi-daemon for resolving host names and addresses and making use of its superior record cacheing. If Avahi is not available at lookup time, the lookups will fail.

## Included libraries
After compiling and installing nss-mdns you'll find six new NSS modules in /lib:

- libnss_mdns.so.2
- libnss_mdns4.so.2
- libnss_mdns6.so.2
- libnss_mdns_minimal.so.2
- libnss_mdns4_minimal.so.2
- libnss_mdns6_minimal.so.2

## Activation
To activate one of the NSS modules you have to edit /etc/nsswitch.conf and add mdns4 and mdns4_minimal (resp. mdns, mdns6) to the line starting with "hosts:". On KaOS this looks like this:

```
# Begin /etc/nsswitch.conf

passwd: files systemd
group: files systemd
shadow: files

publickey: files

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 myhostname mymachines resolve [!UNAVAIL=return] 
networks: files

protocols: files
services: files
ethers: files
rpc: files

netgroup: files

# End /etc/nsswitch.conf
```

further information at https://github.com/lathiat/nss-mdns.
Copyright 2004-2007 Lennart Poettering <mzaffzqaf (at) 0pointer (dot) de>
