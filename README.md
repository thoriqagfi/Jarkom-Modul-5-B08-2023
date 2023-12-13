# Praktikum 5 Jaringan Komputer B08 2023

|Nama|NRP|Kelas|
|:--:|:-:|:---:|
|Adrian Karuna Soetikno|5025211019|Jarkom B|
|Thariq Agfi Hermawan|5025211215|Jarkom B|


## Contents

- [Topology](#topology)


## Subnetting

![Subnetting](/images/subnetting.jpg)


## IP Distribution

### Tree

![Pembagian IP - Tree](/images/pembagian-ip-tree.jpg)

### IP Table

| **Nama Subnet**   | **Rute**                                 | **Jumlah IP** | **Netmask** |
| ----------------- | ---------------------------------------- | --------- | ------- |
| A1                | Fern - Switch1 - Revolte                 | 2         | /30     |
| A2                | Fern - Richter                           | 2         | /30     |
| A3                | Himmel - Switch1 - Fern - SchwerMountain | 66        | /25     |
| A4                | Himmel - LaubHills                       | 256       | /23     |
| A5                | Frieren - Himmel                         | 2         | /30     |
| A6                | Frieren - Stark                          | 2         | /30     |
| A7                | Aura - Frieren                           | 2         | /30     |
| A8                | Aura - Heiter                            | 2         | /30     |
| A9                | Heiter - TurkRegion                      | 1023      | /21     |
| A10               | Heiter - Switch3 - Sein - GrobeForest    | 514       | /22     |
| **Total (10 Subnet)** |                                      | **1871**  | **/20** |


### Assigning IP from Subnet

| Subnet | Node           | IP                           | Netmask         | Length | NID           | Broadcast      |
|--------|----------------|------------------------------|-----------------|--------|---------------|----------------|
|   A1   | Fern           | 192.182.0.1                  | 255.255.255.252 | /30    | 192.182.0.0   | 192.182.0.3    |
|        | Revolte        | 192.182.0.2                  | 255.255.255.252 | /30    | 192.182.0.0   | 192.182.0.3    |
|   A2   | Fern           | 192.182.0.5                  | 255.255.255.252 | /30    | 192.182.0.4   | 192.182.0.7    |
|        | Richter        | 192.182.0.6                  | 255.255.255.252 | /30    | 192.182.0.4   | 192.182.0.7    |
|   A4   | Himmel         | 192.182.2.1                  | 255.255.254.0   | /23    | 192.182.2.0   | 192.182.3.255  |
|        | LaubHills      | 192.182.2.2 - 192.182.3.255  | 255.255.254.0   | /23    | 192.182.2.0   | 192.182.3.255  |
|   A5   | Frieren        | 192.182.0.13                 | 255.255.255.252 | /30    | 192.182.0.12  | 192.182.0.15   |
|        | Himmel         | 192.182.0.14                 | 255.255.255.252 | /30    | 192.182.0.12  | 192.182.0.15   |
|   A6   | Frieren        | 192.182.0.17                 | 255.255.255.252 | /30    | 192.182.0.16  | 192.182.0.19   |
|        | Stark          | 192.182.0.18                 | 255.255.255.252 | /30    | 192.182.0.16  | 192.182.0.19   |
|   A7   | Aura           | 192.182.0.21                 | 255.255.255.252 | /30    | 192.182.0.20  | 192.182.0.23   |
|        | Frieren        | 192.182.0.22                 | 255.255.255.252 | /30    | 192.182.0.20  | 192.182.0.23   |
|   A8   | Aura           | 192.182.0.25                 | 255.255.255.252 | /30    | 192.182.0.24  | 192.182.0.27   |
|        | Heiter         | 192.182.0.26                 | 255.255.255.252 | /30    | 192.182.0.24  | 192.182.0.27   |
|   A9   | Heiter         | 192.182.8.1                  | 255.255.248.0   | /21    | 192.182.8.0   | 192.182.15.255 |
|        | Turk Region    | 192.182.8.2 - 192.182.15.255 | 255.255.248.0   | /21    | 192.182.8.0   | 192.182.15.255 |
|   A10  | Heiter         | 192.182.4.1                  | 255.255.252.0   | /22    | 192.182.4.0   | 192.182.7.255  |
|        | Sein           | 192.182.4.2                  | 255.255.252.0   | /22    | 192.182.4.0   | 192.182.7.255  |
|        | Grobe Forest   | 192.182.4.3 - 192.182.7.255  | 255.255.252.0   | /22    | 192.182.4.0   | 192.182.7.255  |
|   A3   | Himmel         | 192.182.0.129                | 255.255.255.128 | /25    | 192.182.0.128 | 192.182.0.255  |
|        | Fern           | 192.182.0.130                | 255.255.255.128 | /25    | 192.182.0.128 | 192.182.0.255  |
|        | SchwerMountain | 192.182.0.131                | 255.255.255.128 | /25    | 192.182.0.128 | 192.182.0.255  |


## Topology Setup

![Topoloy](/images/topologi.png)


## Node Configuration

### Client Configuration
------------------------------------------------

#### Revolte
```bash
auto eth0
iface eth0 inet static
address 192.182.0.2
netmask 255.255.255.252
gateway 192.182.0.1
```

#### Richter
```bash
auto eth0
iface eth0 inet static
address 192.182.0.6
netmask 255.255.255.252
gateway 192.182.0.5
```

#### SchwerMountain
```bash
auto eth0
iface eth0 inet dhcp
address 192.182.0.131
netmask 255.255.255.128
gateway 192.182.0.129
```

#### LaubHills
```bash
auto eth0
iface eth0 inet dhcp
address 192.182.2.2
netmask 255.255.254.0
gateway 192.182.2.1
```

#### Stark
```bash
auto eth0
iface eth0 inet static
address 192.182.0.18
netmask 255.255.255.252
gateway 192.182.0.17
```

#### TurkRegion
```bash
auto eth0
iface eth0 inet dhcp
address 192.182.8.2
netmask 255.255.248.0
gateway 192.182.8.1
```

#### Sein
```bash
auto eth0
iface eth0 inet static
address 192.182.4.2
netmask 255.255.252.0
gateway 192.182.4.1
```

#### GrobeForest
```bash
auto eth0
iface eth0 inet dhcp
address 192.182.4.3
netmask 255.255.252.0
gateway 192.182.4.1
```

### Router Configuration
----------------------------------------------------------------

#### Fern
```bash
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet static
address 192.182.0.1
netmask 255.255.255.252
gateway 192.182.0.129

auto eth1
iface eth1 inet static
address 192.182.0.5
netmask 255.255.255.252

auto eth0
iface eth0 inet static
address 192.182.0.130
netmask 255.255.255.128
```

#### Himmel
```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.182.0.14
netmask 255.255.255.252
gateway 192.182.0.13

auto eth1
iface eth1 inet static
address 192.182.2.1
netmask 255.255.254.0

auto eth2
iface eth2 inet static
address 192.182.0.129
netmask 255.255.255.128
```

#### Frieren
```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.182.0.22
netmask 255.255.255.252
gateway 192.182.0.21

auto eth1
iface eth1 inet static
address 192.182.0.17
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.182.0.13
netmask 255.255.255.252
```

#### Heiter
```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.182.0.26
netmask 255.255.255.252
gateway 192.182.0.25

auto eth1
iface eth1 inet static
address 192.182.8.1
netmask 255.255.248.0

auto eth2
iface eth2 inet static
address 192.182.4.1
netmask 255.255.252.0
```

#### Aura
```bash
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.182.0.25
netmask 255.255.255.252


auto eth2
iface eth2 inet static
address 192.182.0.21
netmask 255.255.255.252
```

## Node Routing

#### Fern
```bash
echo nameserver 192.168.122.1 > /etc/resolv.conf
route add -net 192.182.0.0 netmask 255.255.255.252 gw 192.182.0.1
route add -net 192.182.0.4 netmask 255.255.255.252 gw 192.182.0.5
```

#### Himmel
```bash
echo nameserver 192.168.122.1 > /etc/resolv.conf
route add -net 192.182.2.0 netmask 255.255.254.0 gw 192.182.2.1
route add -net 192.182.0.128 netmask 255.255.255.128 gw 192.182.0.129
route add -net 192.182.0.0 netmask 255.255.255.252 gw 192.182.0.130
route add -net 192.182.0.4 netmask 255.255.255.252 gw 192.182.0.130
```

#### Frieren
```bash
echo nameserver 192.168.122.1 > /etc/resolv.conf
route add -net 192.182.0.16 netmask 255.255.255.252 gw 192.182.0.17
route add -net 192.182.0.12netmask 255.255.255.252 gw 192.182.0.14
route add -net 192.182.2.0 netmask 255.255.254.0 gw 192.182.0.14
route add -net 192.182.0.128 netmask 255.255.255.128 gw 192.182.0.14
route add -net 192.182.0.0 netmask 255.255.255.252 gw 192.182.0.14
route add -net 192.182.0.4 netmask 255.255.255.252 gw 192.182.0.14
```

#### Heiter
```bash
echo nameserver 192.168.122.1 > /etc/resolv.conf
route add -net 192.182.4.0  netmask 255.255.252.0 gw 192.182.4.1
route add -net 192.182.8.0  netmask 255.255.248.0  gw 192.182.8.1
```

#### Aura
```bash
# Heiter
route add -net 192.182.4.0  netmask 255.255.252.0 gw 192.182.0.26
route add -net 192.182.8.0  netmask 255.255.248.0  gw 192.182.0.26
route add -net 192.182.0.24  netmask 255.255.255.252 gw 192.182.0.26

# Frieren
route add -net 192.182.0.20 netmask 255.255.255.252 gw 192.182.0.22
route add -net 192.182.0.16 netmask 255.255.255.252 gw 192.182.0.22
route add -net 192.182.0.12netmask 255.255.255.252 gw 192.182.0.22
route add -net 192.182.2.0 netmask 255.255.254.0 gw 192.182.0.22
route add -net 192.182.0.128 netmask 255.255.255.128 gw 192.182.0.22
route add -net 192.182.0.0 netmask 255.255.255.252 gw 192.182.0.22
route add -net 192.182.0.4 netmask 255.255.255.252 gw 192.182.0.22
```

# Soal

1. Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.

  - Aura
```bash
ETH0_IP=$(ip -4 addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}')

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source $ETH0_IP
```

2. Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.

  - GrobeForest, Stark, and Sein
```bash
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt-get update
apt-get install netcat -y

# Menolak semua koneksi TCP kecuali port 8080
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP

# Menolak semua koneksi UDP
iptables -A INPUT -p udp -j DROP
```

3. Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.

  - Revolte & Richter (DHCP server & DNS Server)
```bash
# Allow established and related connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Limit ICMP connections to 3 per second
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

4. Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.

  - Sein & Stark (Web Server)
```bash
iptables -A INPUT -p tcp --dport 22 -s 192.182.4.0/22 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP
```

5. Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.
  - Sein & Stark (Web Server)
```bash
# Izinkan akses ke Web Server pada senin-jumat pukul 08:00-16:00
iptables -A INPUT -p tcp --dport 80 -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
```

6. Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).

  - Konfigurasi Sein & Stark (Web Server)
```bash
# Larangan Akses pada hari Senin-Kamis jam 12:00 - 13:00
iptables -A INPUT -p tcp --dport 80 -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j DROP

# Larangan akses pada hari jumat pada 11:00 - 13:00
iptables -A INPUT -p tcp --dport 80 -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j DROP
```

7. Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.
  - Sein
```bash
# Soal 7
iptables -A PREROUTING -t nat -p tcp -d 192.182.4.2 --dport 80 -m statistics --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.182.4.2:80

iptables -A PREROUTING -t nat -p tcp -d 192.182.4.2 --dport 80 -j DNAT --to-destination 192.182.0.14:80
```

  - Stark
```bash
# Soal 7
iptables -A PREROUTING -t nat -p tcp -d 192.182.0.4 --dport 443 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.182.4.2:443

iptables -A PREROUTING -t nat tcp -d 192.182.0.4 --dport 443 -j DNAT --to-destination 192.182.0.14:443
```

8. Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.

```bash

```

9. Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. (clue: test dengan nmap)

```bash

```

10. Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level.

```bash

```
