> Documentation
```
https://git.launchpad.net/netplan/tree/doc/netplan.md
```
> /etc/netplan/01-netcfg.yaml
```
network:
  version: 2
  renderer: networkd
  ethernets:
    bound_inf:
      match: {name: "eno*"}
      optional: true  
  bonds:
    bond0:
      interfaces: [bound_inf]
      addresses: [192.168.1.101/24]
      gateway4: 192.168.1.1
      nameservers:
         addresses: [192.168.1.2]
      parameters:
        mode: 802.3ad
        lacp-rate: fast
        mii-monitor-interval: 100

```
