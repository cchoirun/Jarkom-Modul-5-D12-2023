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

# Aura
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

# Frieren
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

# Stark
```
auto eth0
iface eth0 inet static
	address 192.197.14.142
	netmask 255.255.255.252
        gateway 192.197.14.141
```

# Himmel
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

# Fern
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

# Richter
```
auto eth0
iface eth0 inet static
	address 192.197.14.146
	netmask 255.255.255.252
        gateway 192.197.14.145
```

# Revolte
```
auto eth0
iface eth0 inet static
address 192.197.14.150
netmask 255.255.255.252
gateway 192.197.14.149
```

# Heiter
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

# Sein
```
auto eth0
iface eth0 inet static
	address 192.197.8.2
	netmask 255.255.252.0
        gateway 192.197.8.1
```

# Clients
```
auto eth0
iface eth0 inet dhcp
```

## Routing

# Aura:
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

# Heiter:
```
route add 0.0.0.0 netmask 0.0.0.0 gw 192.197.14.129
```

# freiren:
```
route add -net 192.197.12.0 netmask 255.255.254.0 gw 192.197.14.134
route add -net 192.197.14.0 netmask 255.255.255.128 gw 192.197.14.134
route add -net 192.197.14.144 netmask 255.255.255.252 gw 192.197.14.134
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.134
```

# Himmel:
```
route add -net 192.197.14.144 netmask 255.255.255.252 gw 192.197.14.2
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.2
```

# Fern:
```
route add -net 192.197.24.148 netmask 255.255.255.252 gw 192.197.14.2
```