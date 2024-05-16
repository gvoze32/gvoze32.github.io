---
title: Mengembalikan Menu GRUB Yang Hilang
description: Langkah-langkah mengembalikan menu GRUB yang hilang pada sistem Linux yang mungkin tertimpa oleh bootloader Windows atau mengalami konfigurasi yang salah.
image: cover.png
date: 2024-05-16 00:00:00+0000
categories:
    - Linux
tags:
    - linux
    - grub
---

Jika komputer kita sudah menginstal distro Linux, terkadang GRUB akan hilang atau bisa saja tertimpa oleh bootloader milik Windows sehingga GRUB tidak akan tampil.

Pada kondisi ini, sebenarnya distro Anda tidak rusak ataupun hilang, hanya saja ada konfigurasi yang salah dan harus diperbaiki.

Untuk mengembalikan GRUB, Anda bisa melakukannya langsung melalui terminal di distro Linux Anda jika masih bisa boot ke dalamnya, atau menggunakan LiveCD jika tidak bisa melakukan boot.

## Langkah-langkah

### 1. Install GRUB

Jika Anda sudah bisa mengakses distro Linux Anda, buka terminal dan jalankan perintah berikut:

```sh
sudo grub-install
```

### 2. Update Konfigurasi GRUB

Setelah perintah di atas sukses dijalankan, langkah berikutnya adalah membuat file konfigurasi GRUB baru:

```sh
sudo update-grub
```

### 3. Restart Komputer

Restart komputer Anda untuk memastikan apakah GRUB sudah tampil pada saat booting.

### 4. Deteksi Windows dengan `os-prober`

Jika Windows tidak dikenali, silakan jalankan perintah berikut:

```sh
sudo os-prober
```

### 5. Edit Konfigurasi GRUB (Opsional)

Jika boot menu masih tidak tampil, mungkin ada konfigurasi GRUB yang bermasalah. Anda dapat mengedit file `/etc/default/grub` pada seksi `GRUB_TIMEOUT_STYLE` dari `hidden` menjadi `menu` untuk menampilkan entri menu boot. Berikut adalah contohnya:

```sh
sudo nano /etc/default/grub
```

Ubah baris:

```sh
GRUB_TIMEOUT_STYLE=hidden
```

Menjadi:

```sh
GRUB_TIMEOUT_STYLE=menu
```

Simpan perubahan dan jalankan kembali perintah `update-grub`:

```sh
sudo update-grub
```

Dengan langkah-langkah di atas, seharusnya GRUB Anda sudah kembali dan bisa digunakan untuk memilih sistem operasi yang akan di-boot. Selamat mencoba!