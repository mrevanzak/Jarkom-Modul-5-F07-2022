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


## Routing

## Testing
