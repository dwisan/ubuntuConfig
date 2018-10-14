> Documentation
```
https://git.launchpad.net/netplan/tree/doc/netplan.md?_ga=2.168659361.1462401523.1539532048-1762523469.1524738621
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
