# JARKOM Soal Shift Modul 5

## Daftar isi

- [Anggota Kelompok](#anggota-kelompok)

## Anggota Kelompok F07

| NRP        | NAMA                       |
| ---------- | -------------------------- |
| 5025201145 | Mochamad Revanza Kurniawan |
| 5025201241 | Jabalnur                   |

## Topologi
![image](https://user-images.githubusercontent.com/73029778/206865347-d348e6c0-789a-4154-ad65-2d1b7243bfc9.png)

- Eden adalah DNS Server
- WISE adalah DHCP Server
- Garden dan SSS adalah Web Server
- Jumlah Host pada Forger adalah 62 host
- Jumlah Host pada Desmond adalah 700 host
- Jumlah Host pada Blackbell adalah 255 host
- Jumlah Host pada Briar adalah 200 host

## GNS3 - CIDR

Didapatkan subnet sebagai berikut
![image](https://user-images.githubusercontent.com/73029778/206865356-c3a1f9b1-c084-41c5-8c01-6dcf0a23c16e.png)

Dari gambar diatas dapat kita buat tree subnet CIDR seperti berikut :
![image](https://user-images.githubusercontent.com/73029778/206865362-105d288e-1306-4c22-847a-f9921f3d9524.png)

- Subnet A: <br>

|  Subnet A | Jumlah IP | Netmask |
| :-------: | :-------: | :-----: |
|    A1     |   2    |   /30   |
|    A2     |    3    |   /29   |
|    A3     |   63     |   /25   |
|    A4     |   701     |   /22   |
|    A5     |   2     |   /30   |
|    A6     |    201    |   /24   |
|    A7     |    3    |   /29   |
|    A8     |     256    |   /23   |
| **Total** | **1231**  | |

- Subnet B:<br>

| Subnet B    | Jumlah IP | Netmask |
| ----------- | --------- | ------- |
| B1 (A2+A3) | 66       | /24     |
| B2 (A7+A8) | 259       | /22     |
| A1          | 2      | /30     |
| A4          | 701       | /22     |
| A5          | 2       | /30     |
| A6          | 201        | /24     |
| **Total**   | **1231**  | |

- Subnet C:<br>

| Subnet C    | Jumlah IP | Netmask |
| ----------- | --------- | ------- |
| C1 (B1+A4)  | 767      | /21     |
| C2 (B2+A6)  | 460       | /21     |
| A1          | 2       | /30     |
| A5          | 2        | /30     |

- Subnet D<br>

| Subnet D    | Jumlah IP | Netmask |
| ----------- | --------- | ------- |
| D1 (C1+A1) | 769      | /20     |
| D2 (C2+A5) | 462       | /20     |

- Subnet E<br>

| Subnet E   | Jumlah IP | Netmask |
| ---------- | --------- | ------- |
| E1 (D1+D2) | 1231      | /19     |

Untuk konfigurasinya sebagai berikut
- Blackbell

![image](https://user-images.githubusercontent.com/73029778/206905262-e2bba5ed-1c50-4ec5-9700-6183fb46bddc.png)

- Garden

![image](https://user-images.githubusercontent.com/73029778/206905284-92d4a70b-68f8-47b0-b81a-131b7db2f3af.png)

- Strix
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
	hwaddress ether b6:23:6b:b5:5d:33

auto eth1
iface eth1 inet static
	address 10.32.8.1
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.32.24.1
	netmask 255.255.255.252
```

- Ostania
```
auto eth0
iface eth0 inet static
	address 10.32.24.2
	netmask 255.255.255.252
	gateway 10.32.24.1

auto eth1
iface eth1 inet static
	address 10.32.20.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.32.18.1
	netmask 255.255.255.248

auto eth3
iface eth3 inet static
	address 10.32.16.1
	netmask 255.255.254.0
```

- Eden

![image](https://user-images.githubusercontent.com/73029778/206905412-a98f3ac3-f683-4ba0-80b4-91a82f3d3907.png)

- Westalis
```
auto eth0
iface eth0 inet static
	address 10.32.8.2
	netmask 255.255.255.252
	gateway 10.32.8.1

auto eth1
iface eth1 inet static
	address 10.32.4.129
	netmask 255.255.255.248

auto eth2
iface eth2 inet static
	address 10.32.4.1
	netmask 255.255.255.128

auto eth3
iface eth3 inet static
	address 10.32.0.1
	netmask 255.255.252.0
```

- Desmond

![image](https://user-images.githubusercontent.com/73029778/206905575-387daac9-957b-4487-b209-93118c6f69fc.png)

- Briar

![image](https://user-images.githubusercontent.com/73029778/206905592-b1851f5c-adc4-4a0b-9ef2-a55bdb7da099.png)

- SSS

![image](https://user-images.githubusercontent.com/73029778/206905609-1148a383-e279-4f7f-9c3d-43f81f4f3b8a.png)

- Wise

![image](https://user-images.githubusercontent.com/73029778/206905620-072be2b8-1dbe-4502-9c27-66338eeb99b5.png)

- Forger

![image](https://user-images.githubusercontent.com/73029778/206905645-64173cfc-8264-4866-91bb-486c5fd72cfa.png)


## Routing
<table><thead><tr><th>Router</th><th>Subnet</th><th>Network</th><th>Netmask</th><th>Gateway</th><th>Console</th></tr></thead><tbody><tr><td rowspan="6">Strix</td><td>A2</td><td>10.32.4.128</td><td>255.255.255.248</td><td>10.32.8.2</td><td>route add -net 10.32.4.128 netmask 255.255.255.248 gw 10.32.8.2</td></tr><tr><td>A3</td><td>10.32.4.0</td><td>255.255.255.128</td><td>10.32.8.2</td><td>route add -net 10.32.4.0 netmask 255.255.255.128 gw 10.32.8.2</td></tr><tr><td>A4</td><td>10.32.0.0</td><td>255.255.252.0</td><td>10.32.8.2</td><td>route add -net 10.32.0.0 netmask 255.255.252.0 gw 10.32.8.2</td></tr><tr><td>A6</td><td>10.32.20.0</td><td>255.255.255.0</td><td>10.32.24.2</td><td>route add -net 10.32.20.0 netmask 255.255.255.0 gw 10.32.24.2</td></tr><tr><td>A7</td><td>10.32.18.0</td><td>255.255.255.248</td><td>10.32.24.2</td><td>route add -net 10.32.18.0 netmask 255.255.255.248 gw 10.32.24.2</td></tr><tr><td>A8</td><td>10.32.16.0</td><td>255.255.254.0</td><td>10.32.24.2</td><td>route add -net 10.32.16.0 netmask 255.255.254.0 gw 10.32.24.2</td></tr></tbody></table>

## Testing
