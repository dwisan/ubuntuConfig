>Step 1 – Update repositories list
```
sudo apt-get update
```
>Step 2 – Install additional module
```
sudo apt install ifenslave bridge-utils
```
>Step 3 – Interface configuration
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#eth0 configuration
auto eth0
iface eth0 inet manual
bond-master bond0

#eth1 configuration
auto eth1
iface eth1 inet manual
bond-master bond0

# bond0 is the bonded NIC and can be used like any other normal NIC.
# bond0 is configured using static network information.
auto bond0
iface bond0 inet static
address 202.1.2.10
gateway 202.1.2.1
netmask 255.255.255.0
dns-nameservers 8.8.8.8

# bond0 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4
bond-miimon 100
bond-lacp-rate fast
bond-slaves eth0 eth1
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
```
>Step 4 – Apply network configution
```
sudo systemctl restart networking
more /proc/net/bonding/bond0
```
