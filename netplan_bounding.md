> /etc/netplan/01-netcfg.yaml
```
network:
  version: 2
  renderer: networkd
  ethernets:
    bond-ports:
      dhcp4: no
      match:
        name: ens*
  bonds:
    bond0:
      dhcp4: no
      interfaces: [bond-ports]
      parameters:
        mode: 802.3ad
  bridges:
    br0:
      addresses: [XXX.XXX.XXX.40/24]
      gateway4: XXX.XXX.XXX.1
       nameservers:
            addresses: [XXX.XXX.XXX.1]
      interfaces:
        - bond0
```
