## Temporär (bis zum nächsten Reboot):

```
sudo ip addr add 116.203.3.155 dev eth0
```

## Dauherhaft
siehe: [https://wiki.hetzner.de/index.php/Cloud_IP_static](https://wiki.hetzner.de/index.php/Cloud_IP_static)

Editieren von /etc/network/interfaces:

```
auto eth0
iface eth0 inet static
        address 116.203.3.155
        netmask 255.255.255.255
        pointopoint 172.31.1.1 dev eth0
        gateway 172.31.1.1
        dns-nameservers 213.133.98.98 213.133.99.99 213.133.100.100


iface eth0 inet6 static
        address <Eine IPv6 Adresse aus dem Subnetz. z.B. 2a01:4f8:1c1c:4083::1>
        netmask 64
        gateway fe80::1
```
Die bestehende IPv6 (aus  `/etc/network/interfaces.d/50-cloud-init.cfg`) verwenden.

Editieren von /etc/netplan/01-netcfg.yml
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: yes
      dhcp6: no
      addresses:
        - <one IPv6 address from your subnet, e.g. 2001:db8:0::1>/64
      gateway6: fe80::1
```

Hinzufügen von /etc/cloud/cloud.cfg.d/98-disable-network.cfg:

```
network:
  config: disabled
```

Folgender Befehl muss ausgeführt werden:

```
rm /etc/network/interfaces.d/50-cloud-init.cfg
```

`sudo service networking restart`
