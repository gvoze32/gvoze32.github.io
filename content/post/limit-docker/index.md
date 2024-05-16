---
title: Cara Menjadikan Docker Bisa Membuat Lebih Dari 31 Default Network
description: Dengan menyesuaikan rentang jaringan dalam konfigurasi daemon Docker, Anda dapat membuat lebih dari 31 jaringan.
image: cover.jpg
date: 2024-05-16 00:00:00+0000
categories:
    - Docker
tags:
    - docker
    - limit
    - network
    - jaringan
---

Saat bekerja dengan Docker, seringkali kita menemui batasan jumlah jaringan yang dapat dibuat menggunakan driver network bridge default. Secara default, Docker memiliki batasan 31 jaringan untuk driver network bridge pada satu perangkat.

Jika Anda mencoba membuat lebih dari 31 jaringan, Anda mungkin akan mendapatkan pesan kesalahan seperti ini:

> Error response from daemon: could not find an available, non-overlapping IPv4 address pool among the defaults to assign to the network

Hal ini disebabkan oleh pengaturan rentang jaringan default Docker, yaitu 172.17-31.xx/16 dan 192.168.xx/20.

Untungnya, Anda dapat menyesuaikan rentang jaringan dalam konfigurasi daemon Docker. Berikut langkah-langkahnya:

1.  Buat file baru bernama `daemon.json` di direktori `/etc/docker`:

```sh
$ nano /etc/docker/daemon.json
```

2.  Tambahkan konfigurasi berikut ke dalam file `daemon.json`:

```json
{
    "default-address-pools": [
        {"base":"10.10.0.0/16","size":24}
    ]
}
```

3.  Simpan perubahan dan tutup file `daemon.json`.
    
4.  Restart service `dockerd` untuk menerapkan perubahan:

```sh
$ service docker restart
```

5.  Periksa hasilnya dengan menjalankan perintah berikut untuk melihat rentang subnet jaringan bridge:

```sh
$ docker network inspect bridge | grep Subnet
```

Sekarang, Docker akan menggunakan rentang jaringan yang telah Anda atur untuk membuat jaringan baru, mengatasi batasan 31 jaringan.

Dengan langkah-langkah ini, Anda dapat dengan mudah mengatasi batas jumlah jaringan pada Docker dan melanjutkan pekerjaan Anda tanpa hambatan.