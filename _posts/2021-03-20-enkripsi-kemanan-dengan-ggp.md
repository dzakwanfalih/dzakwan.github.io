---
title:  "Mengamankan file dengan gpg" 
permalink: /posts/2021/03/mengamankan-file-dengan-gpg
date: 2021-03-20-00
---

# Pendahuluan

Menurut gue pengamanan data itu penting. tapi bagaimana  caranya? "yo wes tak bahas disini". 

**_Catatan:_** Ini buat yang udah pro, artinya pembelajaran sudah tingkat lanjutan.

coba deh lu lihat gambar dibawah ini
![enkripsi dan dekripsi](/images/engkirpsi.png)

kira-kira ceritanya begini. suatu hari ucok ingin mengirimkan sebuah file rahasia, ketika file rahasia itu mau di transmisikan ke internet, biar aman. kudu di enkripsi. *"apa lagi tuh cuy engkripsi?"*. gini bor, enkripsi itu singkatnya file yang utuh kita acak. supaya orang bingung begimane mbacanya. "alay lu tong"

# Tools 
oke, buat mengamankan suatu file kita pake **GnuPG**. apa tuh? itu singkatan dari GNU Privacy Guard atau singkatanya dari GNUPG atau GPG bahasa gaulnya. 

# Buat apa sih?

* Menambahkan enkripsi dekripsi pada aplikasi pengirim email seperti Thunderbird.

* Mengamankan data dengan enkripsi sebelum disimpan ke media penyimpanan online.

* Mengamankan data sensitif dengan enkripsi sebelum data tersebut dikirimkan ke orang lain yang berhak menerima.

* Membuat pasangan kunci pengaman (key pair) dan manajemen kunci pengamannya.

* Mengamankan data-data penting yang disimpan pada media digital tidak online, seperti data yang disimpan di USB Drive, Harddisk Eksternal, Micro SD Card, dan lain lain.

# Cara install
untuk cara install GnuPG mudah banget, kalo user linux silahkan ketik perintah di command terminal anda seperti ini: 

```bash
sudo apt install gnupg
```

mudah bukan bund :smiley: , biasanya sih udah build in kalo pake ubuntu. 

# Bahasa planet

Di aplikasi ini banyak banget bahasa planetnya. jadi kudu dimengerti satu persatu. 

