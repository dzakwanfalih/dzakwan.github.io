---
title:  "Mengamankan file dengan gpg" 
permalink: /posts/2021/03/mengamankan-file-dengan-gpg
date: 2021-03-20-00
---

# Pendahuluan

Menurut gue pengamanan data itu penting. tapi bagaimana  caranya? *"yo wes tak bahas disini"*. 

**_Catatan:_** Ini buat yang udah pro, artinya pembelajaran sudah tingkat lanjutan.

coba deh, lu lihat gambar dibawah ini: 

![enkripsi dan dekripsi](/images/engkirpsi.png)

kira-kira ceritanya begini. suatu hari ucok ingin mengirimkan sebuah file rahasia, ketika file rahasia itu mau di transmisikan ke internet, biar aman. kudu di enkripsi. *"apa lagi tuh cuy engkripsi?"*. gini bor, enkripsi itu singkatnya file yang utuh kita acak. supaya orang bingung begimane membacanya. habis di acak-acak terus kita obok-obok pake kunci. supaya orang makin  bingung bacanya. nah habis pesan itu dijadikan barang ancur. 

nah yang bisa buka file ini, cuma orang yang tau gimana cara benerinya. sama yang tau resep supaya file ini bener lagi, kira-kira gitu deh ceritanya. yuks langsung praktek aja kalo begitu. 
<br>

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

# Kamus, kamus, bahasa gaulnya 

Di aplikasi ini banyak banget bahasa planetnya. jadi kudu dimengerti satu persatu. 

**keypair** : secara etimilogi kalimat ini gabungan dari key + pair. "ya iya lah bambang". tapi dalam ilmu [kriptografi](https://id.wikipedia.org/wiki/Kriptografi) sebuah public key dan private key. menunjukan sebuah kepercayan dalam sistem. jika di analogikan: **gembok dan kunci**. gitu deh simpelnya. 

**private key** : private key itu ibarat kaya kuncinya.

**public key** : ibarat kaya gembok. tapi gemboknya lu boleh kasih ke orang. 

# Latihan, latihan latihan 

yaudah dari pada lama-lama, mending kita masuk ke sesi latihan. *"mau ngapain kita?"*. ayo kita nikmatin sesi permainan kita kali ini. bawa enjoy bro !


## help 
kalo bingung make aplikasinya bisa ketik perintah gini. supaya kalo lupa bisa nyontek paremeternya begimana. 

```bash
supernode@labs:~$ gpg --help
gpg (GnuPG) 2.2.4
libgcrypt 1.8.1
Copyright (C) 2017 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: /home/supernode/.gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

Syntax: gpg [options] [files]
Sign, check, encrypt or decrypt
Default operation depends on the input data

Commands:
 
 -s, --sign                  make a signature
     --clear-sign            make a clear text signature
 -b, --detach-sign           make a detached signature
 -e, --encrypt               encrypt data
 -c, --symmetric             encryption only with symmetric cipher
 -d, --decrypt               decrypt data (default)
     --verify                verify a signature
 -k, --list-keys             list keys
     --list-signatures       list keys and signatures
     --check-signatures      list and check key signatures
     --fingerprint           list keys and fingerprints
 -K, --list-secret-keys      list secret keys
     --generate-key          generate a new key pair
     --quick-generate-key    quickly generate a new key pair
     --quick-add-uid         quickly add a new user-id
     --quick-revoke-uid      quickly revoke a user-id
     --quick-set-expire      quickly set a new expiration date
     --full-generate-key     full featured key pair generation
     --generate-revocation   generate a revocation certificate
     --delete-keys           remove keys from the public keyring
     --delete-secret-keys    remove keys from the secret keyring
     --quick-sign-key        quickly sign a key
     --quick-lsign-key       quickly sign a key locally
     --sign-key              sign a key
     --lsign-key             sign a key locally
     --edit-key              sign or edit a key
     --change-passphrase     change a passphrase
     --export                export keys
     --send-keys             export keys to a keyserver
     --receive-keys          import keys from a keyserver
     --search-keys           search for keys on a keyserver
     --refresh-keys          update all keys from a keyserver
     --import                import/merge keys
     --card-status           print the card status
     --edit-card             change data on a card
     --change-pin            change a card's PIN
     --update-trustdb        update the trust database
     --print-md              print message digests
     --server                run in server mode
     --tofu-policy VALUE     set the TOFU policy for a key

Options:
 
 -a, --armor                 create ascii armored output
 -r, --recipient USER-ID     encrypt for USER-ID
 -u, --local-user USER-ID    use USER-ID to sign or decrypt
 -z N                        set compress level to N (0 disables)
     --textmode              use canonical text mode
 -o, --output FILE           write output to FILE
 -v, --verbose               verbose
 -n, --dry-run               do not make any changes
 -i, --interactive           prompt before overwriting
     --openpgp               use strict OpenPGP behavior

(See the man page for a complete listing of all commands and options)

Examples:

 -se -r Bob [file]          sign and encrypt for user Bob
 --clear-sign [file]        make a clear text signature
 --detach-sign [file]       make a detached signature
 --list-keys [names]        show keys
 --fingerprint [names]      show fingerprints

Please report bugs to <https://bugs.gnupg.org>.

```

nah habis lu ketik tuh baris perintah, muncul lah contekan-contekan berupa baris command. 


sedikit penejalasan aja, nih yak biar ngk bego-bego amat. 

* Perintah **--generate-key** dan **--full-generate-key** untuk pembuatan kunci pengaman berbentuk private key dan public key.

* Perintah **--encrypt atau -e** untuk mengunci data dengan kunci pengaman yang telah dibuat.

* Perintah **--decrypt atau -d** untuk membuka enkripsi dengan kunci pengaman.

* Perintah **--armor atau -a** untuk mengacak data yang telah dikunci menjadi bentuk kode acak ASCII.

* Perintah **--sign atau -s** untuk menandatangani data yang akan dikunci ataupun data yang telah dikunci.

* Perintah **--detach-sig** untuk menandatangani data dengan memisahkan kode tanda tangan ke bentuk data terpisah berformat **.sig** .

* Perintah **--list-keys atau -k** untuk menampilkan kunci pengaman public atau public key yang telah terpasang di perangkat.

* Perintah **--list-secret-keys atau -K** untuk menampilkan kunci pengaman pribadi atau private key yang terpasang di perangkat.

* Perintah **--export** untuk ekspor kunci pengaman publik atau public key ke dalam bentuk file.

* Perintah **--export-secret-key** untuk ekspor kunci pengaman pribadi atau private key ke bentuk file.

* Perintah **--import** untuk memasang kunci pengaman berbentuk data untuk dimasukkan ke dalam aplikasi GnuPG.

* Perintah **--edit-key** untuk mengubah parameter yang terdapat di dalam kunci pengaman.

* Perintah **--delete-key** untuk menghapus kunci pengaman bersifat publik atau public key dari penyimpanan GnuPG.

* Perintah **--delete-secret-key** untuk menghapus kunci pengaman yang bersifat pribadi atau private key dari penyimpanan GnuPG.

* Perintah **--generate-revocation** untuk membuat kunci pembatalan revoke key untuk membuat kadaluarsa kunci pengaman dengan bantuan jaringan publikasi kunci pengaman online atau keyserver.

* Perintah **--verify** untuk melakukan verifikasi data terenkripsi dengan tanda tangan .sig yang terpisah . Tanda tangan terpisah .sig ini dibuat dengan perintah --detach-sig di atas.

* Perintah **--send-keys** untuk mengirim public key ke layanan keyserver publik.

* Perintah **--receive-keys** untuk menerima public key dari layanan public keyserver online.

