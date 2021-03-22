---
title:  "Installasi nasm dengan di ubuntu 18.04 dan pendahuluan bahasa assembly"
permalink: /posts/2021/03/installasi-nasm-dengan-ubuntu-18.04
date: 2021-03-21-00
---

**_Catatan:_** Tutorial untuk tingkat pemula



# Installasi nasm di ubuntu 18.04 dan pendahuluan bahasa assembly

cara melakukan memasang nasm cukup mudah, silahkan ikuti langkah berikut ini. dan lakukan pada terminal anda. 

## step 1 

```bash
sudo apt-get update -y 
```

## step 2 
```bash
sudo apt install -y nasm
```


# Pendahuluan bahasa assembly

pendahuluan ini gue mulai dari, kenapa bahasa assembly ada didunia ini? yah karena ada prosesor pada komputer, yang hanya mengerti 0 dan 1. 

bahasa assembly sebagai pahlawan hero, mempermudah manusia untuk berinteraksi dengan prosesor.

# Keuntungan  mempelajar bahasa assembly 

keuntungan orang mempelajari bahasa assembly sebagai berikut :
*  Memiliki pemahaman tentang bahasa assembly membuat seseorang lebih sasar bagai mana cara membuat program interface. 

* Bagaimana proses, BIOS bekerja. 

* Bagaimana mengetahui repesentasi  data dalam sebuah memori dan perangkat keras diluar dari komputer. 

* mengatahui  instruksi pada prosesor dan bagaimana data diproses dalam prosesor. 

* dan masih banyak lagi manfaatnya 



# Back to basic

## konversi decimal ke biner

oke, kita hari belajar mengenai bagaiman cara mengubah decimal ke binar, karena kita sudah belajar sebelumnya bahasa memesin menggunakan respresentasi dari angka 0 dan 1. jadi belajar mengkonversi bilangan desimal hukumnya wajib untuk seorang yang ingin belajar bahasa assembly. 

bagimana cara kita belajar, kita belajar dengan menggunakan programming python saja, agar ilmunya bisa langsung dipraktek, hitung-hitung mengasah al-goritma. 

```bash
Step 1:  Let n be the decimal number.

Step 2:  Let b be the number, initially 0, that becomes our answer.  Well be composing it right to left.

Step 3:  Repeat until n becomes 0
     Step 3a:Divide n by 2, letting the result be d and the remainder be r.
     Step 3b:Append the remainder, r, as the leftmost digit of b.
     Step 3c:Let d be the new value of n.

```
[sumber](https://www.wyzant.com/resources/answers/212551/1_write_an_algorithm_flow_chart_pseudo_code_to_convert_from_decimal_number_system_base_10_to_binary_number_system_base_2)


```python
# Konversi decimal ke biner

# inisiasi variabel 

nilai_desimal = 17
nilai_biner = ''

# perulangan jika nilai desimal lebih dari nol 
while nilai_desimal > 0:
    # jika nilai desimal sisa bagi 2 adalah nol 
    if nilai_desimal % 2 == 0:
        #nilai biner adalah 0 dan nilai biner
        nilai_biner = '0' + nilai_biner
    # jika tidak
    else:
        #nilai biner biner adalah satu + nili biner
        nilai_biner = '1' + nilai_biner

    nilai_desimal = nilai_desimal / 2

# Cetak bilai biner
print nilai_biner
```

## konversi bilangan hexa 

oke kenapa kita harus belajar hexa? karena instruksi set dalam proses terdapat kode hexa. 

bagaimana cara simple, mengubah kode hexa dengan bahasa python. tanpa menggunakan algoritma. simak kode box dibawah ini. ditulis dengan menggunakan bahasa shell. 

```bash
# mengubah desimal ke hexa dengan terminal.
algorima bypass dan simpel: 
1. buka terminal
2. ketik python3 
3. ketik hex(kode desimal)
4. enter
```
kira kira jika di aplikasi pada terminal seperti ini. 

```bash
supernode@labs:~$ python3
Python 3.6.9 (default, Jan 26 2021, 15:33:00) 
[GCC 8.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> hex(100)
'0x64
```

<br>

# Alamat memori pada CPU atau  MAR 

![alamat memori pada cpu](https://upload.wikimedia.org/wikipedia/commons/c/c2/Memory_Address_Register_%28MAR%29.jpg)


## Pengertian biar ngerti 
 merupakan register yang menampung alamat data atau instruksi pada main memory yang akan di akses,baik itu yang akan diambil (dibaca) maupun yang akan diletakan (disimpan/ditulis).

 Register ini berisi **alamat dari data dan dihubungkan pada bus alamat**, sehingga dapat **menspesifikasikan alamat di dalam memori untuk operasi baca atau simpan/tulis**. Alamat dari main memory (tempat data berada), diletakan di MAR dan dikirimkan ke main memory melalui address bus. Selama komputer bekerja, alamat dalam pencacah program ditahan (latched) pada MAR. Setelah itu MAR akan mengirimkan alamat ke dalam RAM dan operasi membaca dilaksanakan.