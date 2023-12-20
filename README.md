# Jarkom-Modul-5-D12-2023

Laporan Resmi Modul Jarkom 5 D12 2023
|Nama|NRP|
|-----|-----|
|Muhammad Revel Wivanto|5025211233|
|Muhammad Choirun Ni'am|5025221203|

## Topologi 
<img width="606" alt="image" src="https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/115228631/b600c309-ae87-4753-9d82-15d07e737afb">

## Rute
![image](https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/116476269/0abd0ca6-19e9-4daf-97e0-eaa68f818bbf)

## Pembagian IP
![image](https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/116476269/9614c6f6-acd5-4d2e-9843-ad57b0f516fd)

## Subnetting

### Aura
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.197.14.129
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.197.14.137
	netmask 255.255.255.252
```

### Frieren
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.197.14.138
	netmask 255.255.255.252
        gateway 192.197.14.137

auto eth1
iface eth1 inet static
	address 192.197.14.141
	netmask 255.255.255.252
        

auto eth2
iface eth2 inet static
	address 192.197.14.133
	netmask 255.255.255.252
       
```

### Stark
```
auto eth0
iface eth0 inet static
	address 192.197.14.142
	netmask 255.255.255.252
        gateway 192.197.14.141
```

### Himmel
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.197.14.134
	netmask 255.255.255.252

auto eth1
iface eth1 inet static
	address 192.197.12.1
	netmask 255.255.254.0

auto eth2
iface eth2 inet static
	address 192.197.14.1
	netmask 255.255.255.128
```

### Fern
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.197.14.2
	netmask 255.255.255.128
        
auto eth1
iface eth1 inet static
	address 192.197.14.145
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.197.14.149
	netmask 255.255.255.252
```

### Richter
```
auto eth0
iface eth0 inet static
	address 192.197.14.146
	netmask 255.255.255.252
        gateway 192.197.14.145
```

### Revolte
```
auto eth0
iface eth0 inet static
address 192.197.14.150
netmask 255.255.255.252
gateway 192.197.14.149
```

### Heiter
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.197.14.130
	netmask 255.255.255.252
        gateway 192.197.14.129

auto eth1
iface eth1 inet static
	address 192.197.0.1
	netmask 255.255.248.0

auto eth2
iface eth2 inet static
	address 192.197.8.1
	netmask 255.255.252.0
```

### Sein
```
auto eth0
iface eth0 inet static
	address 192.197.8.2
	netmask 255.255.252.0
        gateway 192.197.8.1
```

### Clients
```
auto eth0
iface eth0 inet dhcp
```

## Routing

### Aura:
```
route add -net 192.197.0.0 netmask 255.255.255.252 gw 192.197.14.130
route add -net 192.197.8.0 netmask 255.255.252.0 gw 192.197.14.130


route add -net 192.197.14.140 netmask 255.255.255.252 gw 192.197.14.138
route add -net 192.197.14.132 netmask 255.255.255.252 gw 192.197.14.138
route add -net 192.197.12.0   netmask 255.255.254.0   gw 192.197.14.138
route add -net 192.197.14.0   netmask 255.255.255.128 gw 192.197.14.138
route add -net 192.197.14.144 netmask 255.255.255.252 gw 192.197.14.138
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.138
```

### Heiter:
```
route add 0.0.0.0 netmask 0.0.0.0 gw 192.197.14.129
```

### freiren:
```
route add -net 192.197.12.0 netmask 255.255.254.0 gw 192.197.14.134
route add -net 192.197.14.0 netmask 255.255.255.128 gw 192.197.14.134
route add -net 192.197.14.144 netmask 255.255.255.252 gw 192.197.14.134
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.134
```

### Himmel:
```
route add -net 192.197.14.144 netmask 255.255.255.252 gw 192.197.14.2
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.2
```

### Fern:
```
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.2
```


## Setup

### DHCP Server
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt update
apt install netcat -y
apt install isc-dhcp-server -y

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo '
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

ddns-update-style none;

# A3
subnet 192.197.8.0 netmask 255.255.252.0 {
  range 192.197.8.2 192.197.11.254;
  option routers 192.197.8.1;
  option broadcast-address 192.197.11.255; 
  option domain-name-servers 192.197.14.146;
  default-lease-time 720;
  max-lease-time 7200;
}

# A2
subnet 192.197.0.0 netmask 255.255.248.0 {
  range 192.197.0.2 192.197.7.254;
  option routers 192.197.0.1;
  option broadcast-address 192.197.7.255;
  option domain-name-servers 192.197.14.146;
  default-lease-time 720;
  max-lease-time 7200;
}

# A4
subnet 192.197.12.0 netmask 255.255.254.0 {
  range 192.197.12.2 192.197.13.254;
  option routers 192.197.12.1;
  option broadcast-address 192.197.13.255;
  option domain-name-servers 192.197.14.146;
  default-lease-time 720;
  max-lease-time 7200;
}

# A8
subnet 192.197.14.0 netmask 255.255.255.128 {
  range 192.197.14.2 192.197.14.126;
  option routers 192.197.14.1;
  option broadcast-address 192.197.1.127;
  option domain-name-servers 192.197.14.146;
  default-lease-time 720;
  max-lease-time 7200;
}

# A1
subnet 192.197.14.128 netmask 255.255.255.252 {}

# A6
subnet 192.197.1.136 netmask 255.255.255.252 {}

# A7
subnet 192.197.14.140 netmask 255.255.255.252 {}

# A5
subnet 192.197.14.132 netmask 255.255.255.252 {}

# A9
subnet 192.197.14.144 netmask 255.255.255.252 {}

# A10
subnet 192.197.14.148 netmask 255.255.255.252 {}
' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server start

```

### DHCP Relay
```
apt update
apt install netcat -y
apt install isc-dhcp-relay -y

echo '
SERVERS="192.197.14.150"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

# nano /etc/sysctl.conf
# net.ipv4.ip_forward=1

service isc-dhcp-relay restart
```

### DNS Server
```
apt update
apt install netcat -y
apt install bind9 -y

echo '
options {
  directory "/var/cache/bind";
  forwarders {
    192.168.122.1;
  };
  allow-query {any;};
  auth-nxdomain no; # conform to RFC1035
  listen-on-v6 {any;};
}' > /etc/bind/named.conf.options

service bind9 restart
```

### Web Server
```
echo nameserver 192.168.122.1 > /etc/resolv.conf

echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt update
apt install netcat -y
apt install apache2 -y
service apache2 start

echo '# If you just change the port or add more ports here, youu
 will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 443

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet' > /etc/apache2/poo
rts.conf

echo '# Sein | Stark
Sein | Stark nih' > /var/www/html/index.html
```

## No.1
```
IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source "$IPETH0" -s 192.197.0.0/20
```
### Before:
![Screenshot 2023-12-16 033652](https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/116476269/84bddd02-1eaa-4a63-a04d-6217c1f29e92)
### After:
![Screenshot 2023-12-16 035735](https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/116476269/4d76a15e-5cc5-4b2b-afd5-d2bb4aa3433f)

## No.2
```
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP
iptables -A INPUT -p udp -j DROP
```
### Menggunakan koneksi TCP
![Screenshot 2023-12-16 040237](https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/116476269/a4d7145c-8a7a-4d70-ac5c-57a46a239b93)
![Screenshot 2023-12-16 040230](https://github.com/cchoirun/Jarkom-Modul-5-D12-2023/assets/116476269/65e8f59d-d062-4b54-ad3d-c43772817a03)

## No.3
```
iptables -I INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
iptables -I INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
## No.4
```
iptables -A INPUT -p tcp --dport 22 -s 192.197.x.x -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP
```

## No.5
```
iptables -A INPUT -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -j REJECT
```

## No.6
```
iptables -I INPUT 3 -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT
iptables -I INPUT 4 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT
```

## No.7
```
echo '
Listen 80
Listen 443

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>
' > /etc/apache2/ports.conf
```

## No.8
```
iptables -A INPUT -p tcp --dport 80 -s 192.197.1.104/30 -m time --datestart 2023-12-10 --datestop 2024-02-15 -j DROP
```

## No.9
```
iptables -N portscan

iptables -A INPUT -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP
iptables -A FORWARD -m recent --name portscan --update --seconds 600 --hitcount 20 -j DROP

iptables -A INPUT -m recent --name portscan --set -j ACCEPT
iptables -A FORWARD -m recent --name portscan --set -j ACCEPT
```

## No.10
```
iptables -I INPUT -m recent --name portscan --update --seconds 600 --hitcount 20 -j LOG --log-prefix "Portscan detected: " --log-level 4

iptables -I FORWARD -m recent --name portscan --update --seconds 600 --hitcount 20 -j LOG --log-prefix "Portscan detected: " --log-level 4
```