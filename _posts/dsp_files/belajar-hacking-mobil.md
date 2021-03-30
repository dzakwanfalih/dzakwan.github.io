---
title:  "Ngoprek CAN BUS untuk ngehack mobil"
permalink: /posts/2021/03/ngoprek-can-bus
---

# Tujuan 
***

Tujuan utama tutorial ini adalah membantu kita (sebagai anak teknik yang gila), memulai belajar mengenai sistem keamanan Otomotif. Hambatan untuk bisa melakukan Peretasan Mobil jauh lebih tinggi dibandingkan dengan bidang keamanan lainnya. gue harap tutorial ini dapat memainkan peran penting dalam membantu kita dalam melakukan peretasan mobil.

> Meskipun Peretasan Mobil dan Keamanan Otomotif adalah bidang yang jauh lebih luas, tutorial ini hanya berfokus pada Jaringan Area Pengontrol (CAN) dan terbatas pada lalu lintas mengintip CAN, menganalisisnya, merekayasa balik, dan **melakukan serangan ulangan pada otomotif.**

Tujuan artikel ini adalah untuk membantu kita memulai keamanan otomotif  atau peretasan mobil dengan mudah tanpa menghabiskan banyak uang untuk membeli mobil.

Ini BUKAN artikel “Zero to Hero in Car hacking to make you expert in X minutes”, sebaliknya, artikel ini hanya bertujuan untuk membantu Anda memulai hacking mobil di simulator.




## Apa saja yang kita butuhkan?
***


Jika lu memutuskan untuk mempraktikkan tutorial ini, Anda akan membutuhkan:

```
1. Ubuntu 18.04 
2. can-utils
3. ICSim 
```




# Apa itu CAN BUS
***
Controller Area Network (CAN bus) adalah standar [bus](https://id.wikipedia.org/wiki/Bus_komputer#:~:text=Dalam%20arsitektur%20komputer%2C%20sebuah%20bus,satu%20set%20kabel%20yang%20sama.) kendaraan yang dirancang untuk memungkinkan mikrokontroler dan perangkat untuk berkomunikasi dengan aplikasi satu sama lain tanpa komputer host. <sup>1</sup> Ternyata control unit pada mobil juga sering update status. Tentunya bukan update status di facebook dan instagram. hehehe <sup>2</sup>

Controller Area Network alias CAN adalah sistem saraf pusat yang memungkinkan komunikasi antara semua / beberapa bagian mobil. Sebelum CAN awalnya dikembangkan oleh BOSCH pada tahun 1985 sebagai sistem komunikasi intra-kendaraan, pabrikan otomotif menggunakan sistem kabel point-to-point. Saat kami mulai memiliki lebih banyak komponen elektronik di dalam mobil, ini hanya menjadi besar dan terlalu mahal untuk dirawat. 

Masalah ini kemudian diperbaiki dengan menggantinya dengan CAN.
Secara sederhana, CAN memungkinkan berbagai unit elektronik di mobil untuk saling berkomunikasi dan berbagi data. Motif utama pengusulan CAN adalah memungkinkan beberapa ECU dikomunikasikan hanya dengan satu kabel. 

mobil modern  memiliki sebanyak 70 ECU. Di dalam mobil, Anda dapat memiliki komponen seperti Engine Control Unit, Airbag, Transmission, Gear Unit, Anti-lock braking system atau hanya ABS, sistem infotainment, kontrol iklim, Windows, pintu, dll. Agar semua unit ini dapat berkomunikasi satu sama lain, kabel point-to-point akan sangat besar. 

Bayangkan, setiap komponen yang terhubung ke setiap komponen lain, ini akan menjadi kekacauan nyata untuk didiagnosis untuk pemecahan masalah apa pun. Tetapi dengan CAN, ini dapat diganti dengan satu kabel dan komunikasi antara setiap unit menjadi lebih sederhana.<sup>3</sup>


# Setting up the virtual Environment
Cara terbaik dan murah untuk mempraktikkan peretasan mobil adalah dengan menjalankan simulator kluster instrumentasi. Terima kasih kepada Craig Smith dan repo open-source bernama ICSim. Menggunakan ICSim, cukup mudah untuk disiapkan dan tidak mahal untuk mempelajari eksploitasi CAN-Bus. Ayo lakukan lakukan.


```bash
sudo apt-get install libsdl2-dev libsdl2-image-dev -y
```


## Installing CAN Utils
In order for us to send, receive and analyze CAN packets, we need CAN utils. can-utils is a Linux specific set of utilities that enables Linux to communicate with the CAN network on the vehicle. The canutils consist of 5 main tools that we use very frequently:

+ cansniffer for sniffing the packets
+ cansend for writing a packet
+ candump dump all received packets
+ canplayer to replay CAN packets
+ cangen to generate random CAN packets

can-utils can be installed via apt-get

```bash
sudo apt-get install can-utils -y
```












### Sumber : 
***
+  [1. *Can BUS.* ( 2021, Maret 28). Di akses pada Maret 28, 2021 ](https://en.wikipedia.org/wiki/CAN_bus )

+ [2. *10 menit belajar jaringan komputer pada mobil yaitu CAN BUS*. (2019, Maret 16). Di akses pada Maret 2021 ](https://www.montirpintar.com/2019/03/can-bus.html)

+ [3. *Car Hacking 101: Practical Guide to Exploiting CAN-Bus using Instrument Cluster Simulator — Part I: Setting Up.* (2019, November 2019). Di akses pada Maret 28, 2021](https://medium.com/@yogeshojha/car-hacking-101-practical-guide-to-exploiting-can-bus-using-instrument-cluster-simulator-part-i-cd88d3eb4a53)