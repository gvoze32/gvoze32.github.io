---
title: Mengembalikan Entri Menu Windows Yang Hilang di GRUB
description: Mengembalikan Entri Menu Windows Yang Hilang di GRUB
image: cover.jpg
date: 2024-05-16 00:00:00+0000
categories:
    - Linux
tags:
    - linux
    - grub
---

Jadi tadi saya menemukan masalah di mana saat melakukan `update-grub` dan `os-probe`, file boot UEFI Windows saya tetap tidak terdeteksi.

Akhirnya saya menemukan cara memperbaikinya dengan mudah. Anda hanya tinggal membuat file di `/boot/grub` dengan nama `custom.cfg` dan isi dengan kode di bawah ini.

```sh
menuentry "Windows Custom" {
    insmod part_gpt
    insmod fat
    insmod chain
    search --no-floppy --fs-uuid --set=uuidbootuefikamu
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```

Isi `uuidbootuefikamu` dengan UUID partisi UEFI Anda (biasanya memiliki format FAT32). Anda bisa mencarinya dengan bantuan perintah `blkid` atau `lsblk -f`.

Coba muat ulang komputer dan pastikan ada pilihan boot Windows di menu GRUB Anda.

Atau jika Anda menggunakan sistem operasi Ubuntu, Anda bisa menggunakan bantuan tool _boot-repair_.

```sh
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

Dengan langkah-langkah di atas, seharusnya file boot UEFI Windows Anda sudah terdeteksi dan bisa diakses melalui menu GRUB. Selamat mencoba!