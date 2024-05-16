---
title: Membuat Subdomain Untuk Minecraft Server
description:
image: cover.png
date: 2024-05-16 00:00:00+0000
categories:
    - Game
tags:
    - game
    - minecraft
    - server
---

Server Minecraft yang baru dibuat umumnya menggunakan alamat IP dan port yang terdiri dari angka. Contohnya adalah `195.27.18.197:2574`. Memiliki rangkaian angka ini bisa sangat merepotkan untuk ditulis dan dihafalkan.

Untuk mempermudah hal ini, Anda dapat menyambungkannya ke domain atau subdomain yang Anda miliki dengan bantuan Cloudflare.

## Persiapan

Sebelum memulai, pastikan Anda telah memiliki:

1. **Domain**
2. **VPS**
3. **Cloudflare**

## Menjalankan Server Minecraft

Pastikan server Minecraft Anda sudah berjalan di VPS. Jika sudah, Anda bisa melanjutkan ke tahap selanjutnya.

## Langkah-langkah Menyambungkan Subdomain dengan Server Minecraft melalui Cloudflare

### 1. Tambahkan Subdomain di Cloudflare

1. Login ke akun Cloudflare Anda.
2. Pilih domain yang ingin Anda gunakan untuk server Minecraft.
3. Buka bagian **DNS**.
4. Tambahkan **A Record** baru dengan:
   - **Name**: Nama subdomain yang Anda inginkan.
   - **IPv4 Address**: Isi dengan alamat IP VPS tempat server Minecraft Anda berjalan.
   - **TTL**: Biarkan nilai default atau atur sesuai kebutuhan Anda.

### 2. Tunggu Proses Propagasi DNS

Tunggu beberapa saat hingga perubahan DNS terpropagasi. Waktu propagasi DNS dapat bervariasi, biasanya membutuhkan waktu hingga 1 jam.

### 3. Cek Integrasi

Setelah propagasi DNS selesai, coba akses subdomain Anda melalui permainan Minecraft. Jika konfigurasi sudah benar, subdomain Anda seharusnya dapat digunakan untuk terhubung ke server Minecraft Anda.

Dengan langkah-langkah di atas, sekarang server Minecraft Anda dapat diakses dengan menggunakan domain atau subdomain yang lebih mudah diingat. Jika Anda mengalami kesulitan, jangan ragu untuk berkomentar. Semoga berhasil!
