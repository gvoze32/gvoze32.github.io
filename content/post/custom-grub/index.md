---
title: Menjadikan Custom Config Muncul Sebelum Entri Utama di GRUB
description: Menampilkan entri dari custom.cfg sebelum entri menu GRUB
image: cover.jpg
date: 2024-05-17 00:00:00+0000
categories:
    - Linux
tags:
    - linux
    - grub
---

Tahukah Anda bahwa Anda bisa menampilkan konfigurasi khusus sebelum entri utama di GRUB? Pada artikel ini, saya akan membagikan langkah-langkah sederhana untuk melakukannya.

Secara default, script file `41_custom` berfungsi untuk mencari dan memberitahu sistem tentang keberadaan file `custom.cfg`, kemudian menampilkan entri tersebut setelah entri menu GRUB (`grub.cfg`) di layar bootscreen Anda.

Jika Anda ingin menampilkan entri dari `custom.cfg` sebelum entri menu GRUB, ikuti langkah-langkah berikut:

## Langkah-langkah

### 1. Salin File `41_custom`
- Pertama, salin file `41_custom` ke direktori yang sama.
- Beri nama file tersebut menjadi `09_custom`.

Mengapa `09_custom`? Karena sistem GRUB membaca file konfigurasi berdasarkan urutan numerik. Dengan menamainya `09_custom`, file tersebut akan dibaca sebelum `10_linux`, script yang digunakan untuk membuat konfigurasi file `grub.cfg`.

### 2. Matikan Script `41_custom`
- Buka file `41_custom` dengan editor teks favorit Anda.
- Tambahkan tanda `#` di awal setiap baris dalam file tersebut untuk menonaktifkannya.

Contoh:

```sh
# if [ -f ${config_directory}/custom.cfg ]; then
#   source ${config_directory}/custom.cfg
# fi
```

### 3. Perbarui Konfigurasi GRUB
- Setelah melakukan perubahan, jalankan perintah berikut di terminal untuk memperbarui konfigurasi GRUB Anda:

```sh
sudo update-grub
```

Perintah ini akan membuat ulang file konfigurasi `grub.cfg` dengan urutan entri yang baru.

Dengan langkah-langkah ini, entri dari `custom.cfg` akan muncul sebelum entri menu GRUB utama. Ini sangat berguna jika Anda memiliki konfigurasi khusus yang ingin diutamakan saat booting.

Selamat mencoba, dan semoga bermanfaat!