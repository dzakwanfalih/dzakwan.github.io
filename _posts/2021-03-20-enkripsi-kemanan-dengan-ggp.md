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


## Alur Penggunaan GPG
* Penggunaan GnuPG pertama kali dilakukan dengan membuat kunci pengaman terlebih dahulu, Dianjurkan untuk membuat kunci pengaman dengan mode expert agar bisa menentukan parameter-parameter tambahan dengan lebih lengkap.

* Setelah kunci pengaman selesai dibuat, dilanjutkan dengan membuat sub kunci pengaman untuk fungsi tanda tangan, enkripsi, dan autentikasi data.

* Kemudian dilanjutkan dengam membuat kunci pembatalan revocation key dan ekspor kunci pengaman yang tersimpan.

* Setelah kunci pengaman dan sub kunci pengaman selesai dibuat, pengguna dapat melanjutkan dengan proses pengamanan data dengan enkripsi dan dekripsi dari data enkripsi yang didapat.

### Membuat Kunci Utama atau Master Key GPG (Key Value Pair)

Langkah pertama dilakukan dengan membuat kunci pengaman yang berbentuk public key dan private key. Pembuatan kunci utama atau disebut juga dengan master key ini bisa dengan menggunakan perintah instan yaitu.

```bash
gpg --generate-key
```
atau bisa juga dengan perintah lebih lengkap yaitu:

```bash
gpg --full-generate-key
```

Namun di tulisan ini kita tidak akan menggunakan cara seperti itu, **karena kita akan membuat master key untuk sertifikasi kunci utama dan subkey untuk fungsi enkripsi, tanda tangan digital, dan autentikasi**. Kita akan membuat kunci utama dengan mode expert sehingga banyak pilihan yang bisa dipakai. Perintah yang kita gunakan yaitu :

```bash
gpg --expert --full-generate-key
```

hasil outputnya akan seperti ini: 

```bash 

supernode@labs:~/kemanan$ gpg --expert --full-generate-key
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
   (7) DSA (set your own capabilities)
   (8) RSA (set your own capabilities)
   (9) ECC and ECC
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (13) Existing key
Your selection? 8
```

Kita memilih pilihan kedelapan yaitu **RSA (set your own capabilities)** . Masukkan angka 8 pada pilihan “Your Selection?” . Tekan enter untuk melanjutkan proses berikutnya. Kemudian akan muncul perintah pilihan berikut ini.

```bash
Possible actions for a RSA key: Sign Certify Encrypt Authenticate 
Current allowed actions: Sign Certify Encrypt 

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? 
```

Kita akan membuat kunci utama atau master key dengan kemampuan membuat sertifikat kunci digital. Kita matikan fungsi Sign dan Encrypt terlebih dahulu. Yaitu dengan menekan tombol E dan A . Tekan pilihan disertai dengan Enter sampai tersisa Current allowed actions hanya tersisa Certify saja. Jika sudah , masukkan pilihan (Q) Finished untuk menyelesaikan pilihan opsi.

```bash

Possible actions for a RSA key: Sign Certify Encrypt Authenticate 
Current allowed actions: Sign Certify Encrypt 

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? a

Possible actions for a RSA key: Sign Certify Encrypt Authenticate 
Current allowed actions: Sign Certify Encrypt Authenticate 

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? S

Possible actions for a RSA key: Sign Certify Encrypt Authenticate 
Current allowed actions: Certify Encrypt Authenticate 

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? Q
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits
```

Setelah menekan Q, kita akan dilanjutkan dengan mengisi jumlah bits untuk RSA key yang akan dibuat. Kita masukkan saja nilai 4096 bits untuk panjang kunci RSA nya.

Setelah memasukkan panjang kunci RSA, akan muncul pilihan untuk menentukan masa berlaku dari master key ini. Idealnya adalah 5 tahun, dan jika sudah habis masa berlakunya, dapat diperbarui kembali dengan fungsi `--edit-key` pada master key tersebut. Namun kita dapat memilih masa berlakunya seumur hidup tanpa masa kadaluarsa. Yaitu dengan memilih pilihan 0 . Namun kita juga membuat masa berlaku menjadi 5 tahun dengan memasukkan pilihan berbentuk <n>y , yaitu 5y , untuk masa berlaku selama 5 tahun.

```bash
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y
```
Pada contoh  ini, kita masukkan masa berlaku tidak terbatas yaitu pilihan 0. Tekan Enter untuk melanjutkan pilihan berikutnya. Yaitu memasukkan data diri berupa nama lengkap dan alamat email kontak kita.

```bash
GnuPG needs to construct a user ID to identify your key.

Real name: Mantap bin mantap
Email address: mantap@mail.com
Comment: comment untuk mengunci email
You selected this USER-ID:
    "Mantap bin mantap (comment untuk mengunci email) <mantap@mail.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
```
Setelah memasukkan kolom isian data diri seperti Real name, Email address, dan Comment. Akan muncul pilihan untuk konfirmasi bahwa data yang kita masukkan sudah benar. Pada artikel ini, data yang dimasukkan sudah benar, dan tidak ada perubahan lagi, sehingga kita cukup memilih pilihan O dari (O)kay di atas. Tekan Enter untuk melanjutkan.

Langkah berikutnya kita akan disuruh untuk memasukkan kata kunci untuk kunci utama atau master key ini. Usahakan kata kunci-nya terdiri dari kombinasi huruf besar, huruf kecil, dan angka dengan panjang lebih atau sama dengan dari 10 karakter. Password ini akan selalu dibutuhkan ketika kita melakukan enkripsi data, impor kunci , dan dekripsi data.

```bash
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 30FCE53598C356BB marked as ultimately trusted
gpg: directory '/home/supernode/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/supernode/.gnupg/openpgp-revocs.d/3DB2E0E7763DF806EBCDE30930FCE53598C356BB.rev'
public and secret key created and signed.

pub   rsa4096 2021-03-20 [CEA]
      3DB2E0E7563DF806EBCDE30930FCE53598C356BB
uid                     Mantap bin mantap (comment untuk mengunci kenangan) <mantap@mail.com>
```

Setelah memasukkan kata kunci pengaman, aplikasi GnuPG akan membuat generasi kode acak berdasarkan aktivitas sistem komputer yang dipakai. Usahakan membuat sistem komputer menjadi sibuk dengan aktivitas harddisk seperti menggerakan kursor, membuka aplikasi, membuka halaman browser. Tujuannya adalah bisa mendapatkan kode RSA atau entropi kode yang aman dan sangat acak. Setelah berhasil membuat kode RSA, kunci pengaman utama ini akan disimpan oleh GnuPG ke dalam tempat penyimpanan khusus. GnuPG akan menampilkan keterangan hasil pembuatan master key yang telah dibuat seperti di bawah ini.

```bash
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 30FCE53598C356BB marked as ultimately trusted
gpg: directory '/home/supernode/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/supernode/.gnupg/openpgp-revocs.d/3DB2E0E7763DF806EBCDE30930FCE53598C356BB.rev'
public and secret key created and signed.

pub   rsa4096 2021-03-20 [CEA]
      3DB2E0E7763DF806EBCDE30930FCE53598C356BB
uid                     Mantap bin mantap (comment untuk mengunci kenangan) <mantap@mail.com>
```

Kunci utama ini telah disimpan ke dalam database dari GnuPG. Kita dapat mengeceknya dengan menggunakan perintah gpg --list-keys atau gpg -k untuk menampilkan daftar public key . Kemudian kita bisa melihat daftar private key dengan **gpg --list-secret-keys atau gpg -K** . Hasilnya akan tampak seperti gambar di bawah ini.

```bash
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
/home/supernode/.gnupg/pubring.kbx
----------------------------------
pub   rsa4096 2021-03-20 [CEA]
      3DB2E0E7563DF806EBCDE30930FCE53598C356BB
uid           [ultimate] Mantap bin mantap (comment untuk mengunci kenangan) <mantap@mail.com>
```

Kemudian kita lanjutkan dengan mengubah setelan dari master key ini untuk menggunakan metode Cipher, Hash, dan Compression tertentu. Yaitu dengan memasukkan perintah penyuntingan kunci mode expert yaitu
**gpg --expert --edit-key** [UID_kunci] . UID atau kode kunci ini bisa didapat dengan menggunakan perintah gpg -K sebelumnya.

```bash
supernode@labs:~/keamanan$ gpg -K
/home/supernode/.gnupg/pubring.kbx
----------------------------------
sec   rsa4096 2021-03-20 [CEA]
      3DB2E0E7763DF806EBCDE30930FCE53598C356BB
uid           [ultimate] Mantap bin mantap (comment untuk mengunci kenangan) <mantap@mail.com>

supernode@labs:~/keamanan$ gpg --expert --edit-key 3DB2E0E7763DF806EBCDE30930FCE53598C356BB
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Secret key is available.

sec  rsa4096/30FCE57598C359BB
     created: 2021-03-20  expires: never       usage: CEA 
     trust: ultimate      validity: ultimate
[ultimate] (1). Mantap bin Mantap (comment untuk mengunci email) <mantap@mail.com>

gpg> 

```

Pada mode penyuntingan ini, kita memasukkan perintah perubahan pada konsol yang disediakan, yaitu disebelah tulisan gpg> . Kita dapat melihat daftar perintah yang disediakan dengan mengetik help pada kolom isian konsol tersebut.

```bash
gpg> help
quit        quit this menu
save        save and quit
help        show this help
fpr         show key fingerprint
grip        show the keygrip
list        list key and user IDs
uid         select user ID N
key         select subkey N
check       check signatures
sign        sign selected user IDs [* see below for related commands]
lsign       sign selected user IDs locally
tsign       sign selected user IDs with a trust signature
nrsign      sign selected user IDs with a non-revocable signature
adduid      add a user ID
addphoto    add a photo ID
deluid      delete selected user IDs
addkey      add a subkey
addcardkey  add a key to a smartcard
keytocard   move a key to a smartcard
bkuptocard  move a backup key to a smartcard
delkey      delete selected subkeys
addrevoker  add a revocation key
delsig      delete signatures from the selected user IDs
expire      change the expiration date for the key or selected subkeys
primary     flag the selected user ID as primary
pref        list preferences (expert)
showpref    list preferences (verbose)
setpref     set preference list for the selected user IDs
keyserver   set the preferred keyserver URL for the selected user IDs
notation    set a notation for the selected user IDs
passwd      change the passphrase
trust       change the ownertrust
revsig      revoke signatures on the selected user IDs
revuid      revoke selected user IDs
revkey      revoke key or selected subkeys
enable      enable key
disable     disable key
showphoto   show selected photo IDs
clean       compact unusable user IDs and remove unusable signatures from key
minimize    compact unusable user IDs and remove all signatures from key

* The 'sign' command may be prefixed with an 'l' for local signatures (lsign),
  a 't' for trust signatures (tsign), an 'nr' for non-revocable signatures
  (nrsign), or any combination thereof (ltsign, tnrsign, etc.).
```


Daftar perintah itu dapat kita gulir ke atas atau ke bawah untuk melihat daftar yang lain. Pada langkah kali ini, kita akan mengubah setelan dari master key untuk metode cipher, hash , dan compression yang dipakai. Yaitu dengan menggunakan perintah setpref . Kita masukkan setelan berikut ini untuk master key-nya :

```bash
setpref SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP Uncompressed
```

Tekan Enter, dan akan muncul jendela konfirmasi dan jendela untuk memasukkan password. Tekan Y untuk setuju. Kemudian masukkan password master key yang telah kita buat ketika proses awal pembuatan master key sebelumnya. Hasil tampilan dari penambahan setelan ini akan tampak di teks di bawah ini.

```bash

gpg> setpref SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP Uncompressed
Set preference list to:
     Cipher: AES256, AES192, AES, CAST5, 3DES
     Digest: SHA512, SHA384, SHA256, SHA224, SHA1
     Compression: ZLIB, BZIP2, ZIP, Uncompressed
     Features: MDC, Keyserver no-modify
Really update the preferences? (y/N) y

sec  rsa4096/30FCE73795C356BB
     created: 2021-03-20  expires: never       usage: CEA 
     trust: ultimate      validity: ultimate
[ultimate] (1). Mantap bin mantap (comment untuk mengunci kenangan) <mantap@mail.com>

```

Kemudian kita simpan konfigurasi tersebut dengan mengetikkan save pada konsol gpg> yang disediakan.

```bash
gpg> save
supernode@labs:~/kemanan$ 
```

Langkah selanjutnya adalah membuat subkey dari master key ini. Subkey yang akan dibuat yaitu **subkey untuk signing, encryption, dan authentication**. Dengan menggunakan subkey, kita dapat dengan mudah mengatur master key dan pengamanan master key. 

Misalkan subkey yang kita miliki ternyata telah diketahui orang atau berhasil dibobol, kita dapat dengan mudah membuat revocation key untuk subkey tersebut. Dan kita tidak perlu membuat revocation key untuk master key utama, karena yang dibobol atau compromised key hanya pada bagian subkey nya saja.

Subkey ini dapat dengan mudah kita hapus dan tambahkan sesuai keperluan yang akan datang dengan fungsi **--edit-key** . Selengkapnya dapat dilihat pada artikel berikut ini.

### Membuat subkey

Pada pilihan yang muncul ketika memasukkan perintah addkey di dalam konsol penyuntingan master key, pilih pilihan nomor 4 yaitu
**(4) RSA (sign only)** .Pilih pilihan tersebut dengan menekan tombol Enter, dan langkah berikutnya akan muncul , yaitu memasukkan panjang bits dari RSA key, masa berlaku, dan memasukkan kata kunci password untuk konfirmasi pembuatan subkey ini. Prosesnya dapat dilihat pada tampilan teks dibawah ini.

```bash
supernode@labs:~/kemanan$ gpg -k
/home/supernode/.gnupg/pubring.kbx
----------------------------------
pub   rsa4096 2021-03-20 [CEA]
      3DB2E0E7763DF806EBCDE30930FCE53598C356BB
uid           [ultimate] Mantap bin mantap (comment untuk mengunci email) <mantap@mail.com>

supernode@labs:~/kemanan$ gpg --expert --edit-key 3DB2E0E7563DF806EBCDE30930FCE53598C356BB
gpg (GnuPG) 2.2.4; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Secret key is available.

sec  rsa4096/30FCE53598C356BB
     created: 2021-03-20  expires: never       usage: CEA 
     trust: ultimate      validity: ultimate
[ultimate] (1). Mantap bin mantap (comment untuk mengunci kenangan) <mantap@mantap.com>

gpg> addkey
Please select what kind of key you want:
   (3) DSA (sign only)
   (4) RSA (sign only)
   (5) Elgamal (encrypt only)
   (6) RSA (encrypt only)
   (7) DSA (set your own capabilities)
   (8) RSA (set your own capabilities)
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (12) ECC (encrypt only)
  (13) Existing key
Your selection? 4
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 5y
Key expires at Kam 19 Mar 2026 12:57:59  WIB
Is this correct? (y/N) y
Really create? (y/N) y
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.

sec  rsa4096/30FCE53898C396BB
     created: 2021-03-20  expires: never       usage: CEA 
     trust: ultimate      validity: ultimate
ssb  rsa4096/5C774CC9D56D6C77
     created: 2021-03-20  expires: 2026-03-19  usage: S   
[ultimate] (1). Mantap bin mantap (comment untuk mengunci email) <mantap@hotmail.com>

gpg> save
```

ita akan melihat kunci subkey ini berhasil dibuat pada teks tampilan diatas. Yaitu secret subkey (ssb) dengan rsa key, waktu pembuatan , waktu kadaluarsa expires, tujuan penggunaan usage untuk Signing (s) . Jangan lupa untuk menyimpan kunci subkey yang telah dibuat ini dengan memasukkan perintah save pada konsol edit mode gpg> 

```bash
supernode@labs:~/kemanan$ gpg -k
/home/supernode/.gnupg/pubring.kbx
----------------------------------
pub   rsa4096 2021-03-20 [CEA]
      3DB1E0E7763DF806EBCDE30930FCE53598C356BB
uid           [ultimate] Mantap bin mantap (comment untuk mengunci kengan) <mantap@mail.com>
sub   rsa4096 2021-03-20 [S] [expires: 2026-03-19]
```

Kita dapat mengubah parameter subkey yang telah dibuat tersebut. Parameter yang dapat diubah yaitu masa berlaku subkey, mengaktifkan dan nonaktifkan subkey (enable / disable) , membuat revocation key untuk subkey, dan menghapus subkey. Caranya adalah masuk ke mode penyuntingan master key, dan masukkan perintah key (nomor subkey) untuk memilih subkey yang telah dibuat.

